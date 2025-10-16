# Activity Diagram

**Activity Diagram (biểu đồ hoạt động)** là một loại biểu đồ **hành vi (behavior diagram)** trong UML — dùng để mô tả **luồng công việc (workflow) hoặc luồng điều khiển (control flow) giữa các hoạt động (activities)** trong một hệ thống.

Nói cách khác, **Activity Diagram thể hiện quá trình xử lý từng bước của một nghiệp vụ hoặc chức năng trong hệ thống.**

| Thành phần             | Ký hiệu                  | Ý nghĩa                                                            |
| ---------------------- | ------------------------ | ------------------------------------------------------------------ |
| **Initial Node**       | 🔵 (chấm đen)            | Điểm bắt đầu của luồng hoạt động                                   |
| **Activity / Action**  | ⬜ (hình chữ nhật bo góc) | Một hành động hoặc bước xử lý                                      |
| **Decision Node**      | ⬠ (hình thoi)            | Rẽ nhánh luồng dựa vào điều kiện                                   |
| **Merge Node**         | ⬠ (hình thoi)            | Hợp nhất các nhánh sau điều kiện                                   |
| **Fork Node**          | ————                     | Chia luồng thành các nhánh song song                               |
| **Join Node**          | ————                     | Hợp nhất các luồng song song                                       |
| **Final Node**         | ⭕ (vòng tròn kép)        | Kết thúc luồng hoạt động                                           |
| **Transition (Arrow)** | ➜                        | Biểu diễn luồng chuyển từ hoạt động này sang hoạt động khác        |
| **Swimlane**           | 🏊                       | Phân chia trách nhiệm (ví dụ: Người dùng, Hệ thống, Quản trị viên) |

![](https://circle.visual-paradigm.com/wp-content/uploads/2017/06/Activity-Diagram-ATM.png)

---

## Actions

- **Action** là bước hành động nhỏ nhất trong một **Activity**.
- Không thể chia nhỏ thêm trong cùng một sơ đồ.
- **Hình dạng:** hình chữ nhật bo góc.
- **Tên:** thường là động từ, ví dụ: `Process Order`, `Review Document`, `Checkout`.

**Cách hoạt động**

- Chỉ chạy khi **điều kiện đầu vào** thỏa mãn.
- Khi xong, kích hoạt **action tiếp theo**.
- Nếu có **exception**, có thể **bắt lỗi** hoặc **lan truyền ra ngoài**.

---

## Controls

- Là **nút điều khiển** trong Activity Diagram.  
- **Chức năng:** điều phối các luồng (flow) giữa các node khác.  
- Dùng để điều khiển **bắt đầu, kết thúc, phân nhánh, kết hợp, đồng bộ** luồng.

**Hoạt động cơ bản**
- **Initial Node:** token đặt ở đây khi Activity bắt đầu. 

![](https://www.uml-diagrams.org/activity-diagrams/activity-activity-initial.png)

- **Flow Final Node:** token tới đây → luồng kết thúc, token bị hủy. 

![](https://www.uml-diagrams.org/activity-diagrams/activity-flow-final.png)

- **Activity Final Node:** token tới đây → kết thúc toàn bộ Activity, hủy tất cả token.  

![](https://www.uml-diagrams.org/activity-diagrams/activity-activity-final.png)

- **Decision Node:** chọn **một luồng ra** dựa trên điều kiện (guard). 

![](https://www.uml-diagrams.org/activity-diagrams/decision-binary.png)
![](https://www.uml-diagrams.org/activity-diagrams/decision-ternary.png)


- **Merge Node:** gộp nhiều luồng thay thế → một luồng ra.  

![](https://www.uml-diagrams.org/activity-diagrams/activity-control-merge.png)

- **Fork Node:** nhân token ra nhiều luồng song song. 

![](https://www.uml-diagrams.org/activity-diagrams/activity-fork.png)

- **Join Node:** chờ tất cả luồng tới → kết hợp thành một luồng duy nhất.

![](https://www.uml-diagrams.org/activity-diagrams/activity-join.png)

---

##  Fork Node và Join Node

### 1. Fork Node (Chia luồng song song)
- **Chức năng:** Một luồng ra → nhiều luồng **chạy song song**.  
- **Token:** Token tới Fork sẽ **nhân bản** cho từng luồng ra.  
- **Ký hiệu UML:** một **thanh ngang** với **1 vào, nhiều ra**.  

![](https://sparxsystems.com/enterprise_architect_user_guide/17.1/images/activity-forkjoin2.png)

**Ví dụ:**  
Sau khi thanh toán xong trong Activity “Xử lý đơn hàng”:  
- Gửi email xác nhận khách hàng  
- Cập nhật kho  
- Thông báo bộ phận vận chuyển  

→ 3 bước này **chạy cùng lúc** → dùng **Fork Node**.


---

### 2. Join Node (Kết hợp luồng song song)
- **Chức năng:** Nhiều luồng song song → hợp lại thành **một luồng duy nhất**.  
- **Token:** Chờ **tất cả token từ các luồng vào** tới → mới đi tiếp.  
- **Ký hiệu UML:** một **thanh ngang** với **nhiều vào, 1 ra**.  

![](https://sparxsystems.com/enterprise_architect_user_guide/17.1/images/activity-forkjoin1.png)

**Ví dụ:**  
Sau khi gửi email, cập nhật kho, và thông báo vận chuyển xong:  
- Hợp lại để cập nhật trạng thái đơn hàng hoàn tất → dùng **Join Node**.
