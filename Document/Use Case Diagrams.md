# Thành phần chính của Use Case Diagram

## Actor (tác nhân):

- **Actor** Một thực thể bên ngoài tương tác với hệ thống. Actor có thể là **một người (ví dụ: người dùng, quản trị viên, khách hàng)** hoặc một **hệ thống khác (ví dụ: hệ thống thanh toán, cơ sở dữ liệu bên ngoài)**.

- **Biểu diễn:** Hình que người (stick figure), thường có tên ở bên dưới.

- **Vai trò:** Đại diện cho một vai trò chứ không phải một người cụ thể. Một người thật có thể đóng nhiều vai trò (actor) khác nhau.

- **Ví dụ:** `Khách hàng`, `Quản trị viên`, `Kế toán`, `Giáo viên`, `Sinh viên`, `Hệ thống Email`. `Cổng thanh toán trực tuyến (PayPal, VNPay)`, `API của bên thứ ba`

![](https://www.uml-diagrams.org/use-case-diagrams/use-case-actor-rel-gener.png)

### Phân loại theo mức độ tương tác (Quan trọng trong phân tích)

- **Actor chính (Primary Actor):** Là actor khởi tạo Use Case để đạt được mục tiêu nào đó. Họ là người sử dụng hệ thống để nhận về giá trị trực tiếp.

**Ví dụ:** Trong Use Case "Đặt mua hàng", Khách hàng là Primary Actor vì họ là người chủ động thực hiện việc đặt hàng.

- **Actor phụ (Supporting Actor hoặc Secondary Actor):**  Là actor cung cấp dịch vụ cho hệ thống. Hệ thống cần tương tác với họ để hoàn thành Use Case. 

**Ví dụ:** Trong Use Case "Đặt mua hàng", hệ thống cần gọi tới Hệ thống thanh toán để xử lý giao dịch và gửi email xác nhận cho Khách hàng thông qua Hệ thống Email. Cả Hệ thống thanh toán và Hệ thống Email đều là Supporting Actors.

---

## Use Case (ca sử dụng):

- **Use Case** là một chức năng hoặc dịch vụ mà hệ thống **cung cấp cho actor** để đạt được một **mục tiêu cụ thể**. Nó mô tả "hệ thống làm gì" chứ không mô tả "làm như thế nào".

- **Biểu diễn:** Hình elip (oval) với tên use case bên trong.

- **Vai trò:** Mỗi use case thể hiện một tình huống sử dụng hệ thống có ý nghĩa đối với actor. Nó giúp trả lời câu hỏi: Actor có thể làm gì với hệ thống?

- **Ví dụ:** Đăng nhập, Đăng ký tài khoản, Thanh toán, Xem điểm.

![](https://miro.medium.com/v2/resize:fit:1400/1*Iiw_wByLHaYfFeb_oog3Dw.png)


### B1 - Đối Với Từng Actor, Đặt Câu Hỏi: "Actor Muốn Đạt Được Điều Gì?"
- Đây là **trọng tâm** của việc xác định Use Case. Mỗi Use Case phải cung cấp một giá trị có thể quan sát được cho một Actor.

- **Ví dụ** với Actor Khách hàng:
    - Họ muốn `"Duyệt danh mục sản phẩm"` -> Use Case `Duyệt sản phẩm`.
    - Họ muốn `"Mua một món hàng"` -> Use Case `Đặt mua hàng`.
    - Họ muốn `"Xem tình trạng đơn hàng của mình"` -> Use Case `Theo dõi đơn hàng`.
    - Họ muốn `"Được hỗ trợ khi có vấn đề"` -> Use Case `Liên hệ hỗ trợ`.

- Xác Định Các Use Case Liên Quan Đến Sự Kiện Theo Thời Gian hoặc Sự Kiện Hệ Thống Ví dụ:
    - `"Vào lúc 23h59 mỗi ngày, hệ thống cần thông báo"` -> Hệ thống sẽ gửi mail thông báo về lịch đã hẹn của sinh viên và giáo viên.

    - `"Khi đơn hàng không được thanh toán sau 24h, hệ thống cần hủy đơn"` -> Use Case Tự động hủy đơn hàng quá hạn.

### B2 - Nhóm Các Use Case Lại và Sử Dụng Các Quan Hệ `<<include>>` và `<<extend>>`

- Khi đã có một danh sách dài các Use Case, hãy xem xét những Use Case nào có chức năng chung.

- Ví dụ: Cả Đặt mua hàng và Cập nhật giỏ hàng đều cần Tính tổng tiền. Thay vì viết lại chức năng này, hãy tách nó thành một Use Case riêng Tính toán đơn giá và sử dụng quan hệ `<<include>>` để biểu thị rằng nó được bao gồm bắt buộc.

- Tương tự, tìm các chức năng tùy chọn (như Áp dụng mã giảm giá trong quá trình thanh toán) và sử dụng `<<extend>>`.

---

## Hệ thống (System boundary): 

- **Hệ thống (System boundary)** Nó định nghĩa phạm vi của phần mềm hoặc hệ thống bạn đang phân tích và thiết kế.

- **Mục đích:** Nó trả lời câu hỏi "Ranh giới giữa phần `bên trong` và `bên ngoài` hệ thống ở đâu?".
    - **Bên TRONG đường biên:** Là tất cả các chức năng (Use Case) mà hệ thống của bạn sẽ thực hiện.

    - **Bên NGOÀI đường biên:** Là tất cả các Actor (tác nhân) và các hệ thống bên ngoài mà hệ thống của bạn tương tác với.

- **Xác định phạm vi dự án:** Nó giúp ngăn "phạm vi bùng nổ" (scope creep) bằng cách làm rõ những gì thuộc về và không thuộc về hệ thống cần xây dựng.

- **Tập trung vào hệ thống hiện tại:** Nó buộc người phân tích phải tập trung vào các chức năng cốt lõi của hệ thống đang được đề cập, thay vì các hệ thống bên ngoài.

![](https://blog.visual-paradigm.com/wp-content/uploads/2022/10/use-case-diagram-multiple-projects-with-system-boundaries.png)

--- 

## Quan hệ (Relationships):

### Association (liên kết): Actor <-> Use case.

- **Association** là một đường thẳng (có thể có mũi tên hoặc không) kết nối trực tiếp một Actor với một Use Case.
- **Ý nghĩa:** Nó cho biết rằng Actor đó tham gia hoặc tương tác với Use Case đó. Actor có thể kích hoạt Use Case, cung cấp thông tin đầu vào cho nó, hoặc nhận thông tin đầu ra từ nó.
- **Ký hiệu:** Một đường thẳng liền nét.
- **Nguyên tắc kết nối:**
    - Một Actor có thể kết nối đến nhiều Use Case.
    - Một Use Case có thể được kết nối đến nhiều Actor.
    - Không bao giờ có kết nối trực tiếp giữa Actor với Actor hoặc Use Case với Use Case. Các kết nối này phải được thực hiện thông qua các quan hệ khác như `<<include>>` hoặc `<<extend>>`.

![](https://images.upgrad.com/7f187cfd-4b7c-4e8f-b4b7-08283d904876-zzz001.png)

### Include: Một use case luôn bao gồm use case khác.

- **`<<include>>`** thể hiện một mối quan hệ bắt buộc từ một Use Case này (gọi là Use Case cơ bản - base use case) đến một Use Case khác (gọi là Use Case được include - inclusion use case).
- **Ý nghĩa:** Hành vi của Use Case được include **LUÔN LUÔN được** thực thi như một phần không thể thiếu trong luồng sự kiện của Use Case cơ bản. Nó giống như việc gọi một hàm con hoặc một module có thể tái sử dụng.
- **Ký hiệu:** Một đường chấm chấm có mũi tên hướng từ **Use Case cơ bản ĐẾN Use Case được include**.
- **Khi nào sử dụng `<<include>>`**

    - **Tránh trùng lặp logic (Tính tái sử dụng):** Khi một đoạn hành vi (một nhóm các bước) giống nhau xuất hiện trong nhiều Use Case khác nhau.
    - **Ví dụ:** Cả Đặt mua hàng và Xem lịch sử đơn hàng đều bắt buộc phải Xác thực người dùng. Thay vì viết lại các bước xác thực trong cả hai Use Case, ta tách nó thành một Use Case riêng và dùng `<<include>>`.

        ![](https://www.uml-diagrams.org/use-case-diagrams/include-two-use-cases.png)


    - **Phân tách một Use Case phức tạp:** Khi một Use Case quá dài và có thể được chia nhỏ thành các phần độc lập về mặt logic. Phần được tách ra trở thành một Use Case được include.
    - **Ví dụ:** Use Case Đặt mua hàng rất phức tạp. Bạn có thể tách phần Tính toán phí vận chuyển thành một Use Case riêng và để Đặt mua hàng include nó.
        ![](https://www.uml-diagrams.org/use-case-diagrams/two-includes-use-case.png)
        ![](https://www.uml-diagrams.org/use-case-diagrams/include-use-case.png)

### Extend: Một use case có thể được mở rộng trong điều kiện cụ thể.

- **`<<extend>>`** thể hiện một mối quan hệ tùy chọn từ một Use Case này (Use Case mở rộng - extension use case) đến một Use Case khác (Use Case cơ bản - base use case).
- **Ý nghĩa:** Hành vi của Use Case mở rộng **chỉ được thực thi khi một điều kiện cụ thể xảy ra** trong quá trình thực thi Use Case cơ bản. Nó không phải là phần bắt buộc của luồng chính.
- **Ký hiệu:**  Một đường chấm chấm có mũi tên hướng từ **Use Case mở rộng ĐẾN Use Case cơ bản**.

![](https://www.jot.fm/issues/issue_2005_11/article4/images/figure3.gif)

### Generalization: Quan hệ kế thừa giữa actor hoặc use case.

- **Generalization** cho thấy rằng một thành phần cụ thể (con) kế thừa các đặc điểm và hành vi từ **một thành phần tổng quát hơn (cha)**, và **có thể mở rộng hoặc ghi đè chúng**.
- **Ý nghĩa:** Thành phần con `"là một"` dạng cụ thể của thành phần cha. Mọi kết nối (association, include, extend) của thành phần cha đều được áp dụng tự động cho thành phần con.
- **Ký hiệu:**  Một đường liền nét có mũi tên rỗng hình tam giác ở đầu, hướng từ thành phần con về phía thành phần cha.
- **Ví dụ:Ví dụ:** Một Người dùng có thể thực hiện các Use Case chung như Đăng nhập và Xem trang cá nhân. Quản trị viên là một Người dùng, nên họ cũng có thể thực hiện những việc đó, đồng thời có thêm các quyền riêng như Quản lý người dùng.

![](https://www.uml-diagrams.org/use-case-diagrams/use-case-actor-rel-gener.png)

![](https://www.uml-diagrams.org/use-case-diagrams/use-case-generalization.png)
