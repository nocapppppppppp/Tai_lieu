# Sequence Diagrams

**Sequence Diagram** là loại biểu đồ tương tác phổ biến nhất trong UML, dùng để mô tả trình **tự trao đổi thông điệp** giữa các đối tượng (lifelines) theo thời gian.

Nó cho thấy **ai gọi ai, gọi khi nào, và phản hồi ra sao** trong một tiến trình hoặc use case.

| **Thành phần**                           | **Mô tả**                                                                                                                                        | **Ký hiệu (Notation)**                                   |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------- |
| **Lifeline**                             | Đại diện cho một đối tượng hoặc thực thể tham gia vào tương tác. Hiển thị bằng hình chữ nhật (đầu) và đường thẳng đứng (thân) thể hiện vòng đời. | ▭────────── (đường thẳng đứng dưới tên đối tượng)        |
| **Message**                              | Mũi tên thể hiện thông điệp gửi giữa các lifelines. Có thể là gọi hàm, gửi tín hiệu, hoặc phản hồi.                                              | → (synchronous), (asynchronous), ↩ (return)            |
| **Execution Specification (Activation)** | Hình chữ nhật hẹp trên lifeline, thể hiện thời gian đối tượng đang xử lý hành động hoặc chờ phản hồi.                                            | ▯ (hình chữ nhật hẹp trên lifeline)                      |
| **Occurrence**                           | Thời điểm một sự kiện xảy ra, như bắt đầu hoặc kết thúc của một message.                                                                         | • (điểm trên lifeline, không có ký hiệu riêng trong UML) |
| **Destruction Occurrence**               | Dấu “X” ở cuối lifeline, biểu thị đối tượng bị hủy hoặc kết thúc tồn tại.                                                                        | ✕ (dấu X ở cuối lifeline)                                |
| **State Invariant (ít dùng)**                      | Ràng buộc trạng thái của đối tượng tại thời điểm cụ thể (ví dụ: `status = Completed`).                                                           | `{constraint}` hoặc trạng thái trong ô nhỏ trên lifeline |
| **Combined Fragment**                    | Khối logic gồm điều kiện `alt`, vòng lặp `loop`, hoặc tùy chọn `opt`, tương tự if–else/for/while.                                                | Khung chữ nhật có nhãn `alt`, `loop`, `opt`, ...         |
| **Interaction Use**                      | Tái sử dụng một biểu đồ tương tác khác (gọi là `ref`), giúp biểu đồ gọn hơn.                                                                     | Khung chữ nhật có nhãn `ref`                             |

![](https://www.uml-diagrams.org/sequence-diagrams/sequence-diagram-overview.png)

---

## Message

**Message (Thông điệp)** trong UML Sequence Diagram biểu diễn một hành động giao tiếp giữa **các đối tượng (lifeline)** trong một hệ thống.

```c++
User -> System: login(username, password)
System --> User: return success
```

| Loại                    | Ký hiệu UML                                                                    | Giải thích dễ hiểu                                          | Ví dụ thực tế                                             |
| ----------------------- | ------------------------------------------------------------------------------ | ----------------------------------------------------------- | --------------------------------------------------------- |
| **Synchronous Call**    | Mũi tên **đầu kín (filled)**                                                   | Gọi hàm **chờ kết quả**, giống như `function()` trong code. | `User -> System: login()` rồi đợi phản hồi.               |
| **Asynchronous Call**   | Mũi tên **đầu mở (open)**                                                      | Gửi xong **không chờ kết quả**, chạy tiếp.                  | `Server -> Logger: logEvent()` và tiếp tục làm việc khác. |
| **Asynchronous Signal (ít dùng)** | Giống Asynchronous Call, nhưng thể hiện **tín hiệu (signal)** thay vì gọi hàm. | `Sensor -> Alarm: signal()`.                                |                                                           |
| **Create Message (ít dùng)**      | Đường nét **gạch đứt** đến **lifeline mới xuất hiện**                          | Dùng để **tạo đối tượng**.                                  | `System ..> Account: create()`.                           |
| **Delete Message (ít dùng)**      | Gửi để **xóa đối tượng**, lifeline kết thúc bằng chữ **X**                     | `System -> Account: «destroy»`.                             |                                                           |
| **Reply Message (ít dùng)**       | Đường **gạch đứt** với mũi tên **mở**                                          | Phản hồi từ lời gọi đồng bộ (synchronous).                  | `System --> User: return success`.                        |

![](https://help.bizzdesign.com/resources/Storage/horizzon-help/specifying-the-type-of-a-message-in-a-uml-sequence-diagram/worddav669df1d6e1ac5266ad5312a65db0622d.png)

---

## Combined Fragment

**Combined Fragment** là thành phần trong **UML Sequence Diagram** dùng để mô tả **cấu trúc điều khiển** (rẽ nhánh, lặp, song song, điều kiện, v.v.).  
Nó giúp biểu đồ tuần tự ngắn gọn và thể hiện logic chương trình rõ ràng hơn.

Một Combined Fragment gồm:
- **Interaction Operator**: loại hành vi (alt, loop, par, …)
- **Interaction Operand**: phần nội dung (các thông điệp, hành động)

| Operator | Nghĩa | Giải thích dễ hiểu | Ví dụ |
|-----------|--------|--------------------|--------|
| **alt** | Alternative | Rẽ nhánh `if / else` | Nếu `balance > 0` → `accept()`, ngược lại → `reject()` |
| **opt** | Option | Tùy chọn, giống `if` (có thể không chạy) | Nếu `no errors` → `postComment()` |
| **loop** | Loop | Lặp lại hành vi (giống `for`, `while`) | Lặp `processItem()` 5–10 lần nếu `[size > 0]` |
| **break (ít dùng)** | Break | Thoát khỏi phần còn lại của biểu đồ | Nếu `[y > 0]` → dừng xử lý |
| **par (ít dùng)** | Parallel | Thực hiện song song hoặc xen kẽ | Tìm kiếm `Google`, `Bing`, `Ask` cùng lúc |
| **strict (ít dùng)** | Strict sequencing | Tuần tự nghiêm ngặt | Gọi `A()` → `B()` → `C()` theo đúng thứ tự |
| **seq (ít dùng)** | Weak sequencing | Tuần tự yếu, linh hoạt giữa các lifeline | `Google` song song `Bing`, nhưng `Bing` trước `Yahoo` |
| **critical (ít dùng)** | Critical region | Vùng độc quyền, không xen kẽ tiến trình khác | `add()` và `remove()` chạy song song, nhưng mỗi cái phải hoàn tất trước khi xen |
| **ignore (ít dùng)** | Ignore | Bỏ qua các message không quan trọng | Bỏ qua `get()` và `set()` |
| **consider (ít dùng)** | Consider | Chỉ xét một số message, bỏ qua phần khác | Chỉ xét `add()` và `remove()` |
| **assert (ít dùng)** | Assertion | Chỉ cho phép các hành vi trong khối là hợp lệ | `commit()` phải xảy ra |
| **neg (ít dùng)** | Negative | Mô tả tình huống lỗi / thất bại | Nhận `timeout` → hệ thống thất bại |

### Operator alt

- Thể hiện các lựa chọn tương tự như câu lệnh `if...else` trong lập trình.  
- Mỗi nhánh trong `alt` có một **điều kiện (guard condition)** xác định khi nào nó được thực hiện.  
- Dạng ký hiệu thường gặp là **Decision Node (hình thoi)** với các nhánh được ghi điều kiện bên cạnh.

![](https://www.softwareideas.net/i/DirectImage/3244/alt-fragment)

### Operator opt

- Tương tự như câu lệnh `if` trong lập trình (không có `else`).  
- Thường được dùng để biểu diễn **một hành động tùy chọn** hoặc **trường hợp đặc biệt**.  
- Chỉ có **một nhánh duy nhất** với **điều kiện bảo vệ (guard condition)**.  

![](https://www.softwareideas.net/i/DirectImage/3245/opt-fragment)

### Operator loop

- Tương tự như `while` hoặc `for` trong lập trình.  
- Luồng điều khiển sẽ **quay lại điểm bắt đầu** của hành động khi điều kiện vẫn còn đúng.  
- Khi điều kiện sai, quá trình lặp **kết thúc** và chuyển sang hành động tiếp theo.

![](https://i.sstatic.net/xJG1g.png)
