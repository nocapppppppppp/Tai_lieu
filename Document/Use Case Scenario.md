# Thành phần chính của Use Case Scenario

## Một tài liệu Use Case chi tiết thường bao gồm các mục sau:

| Thành Phần       | Mô Tả                                                                                      | Ví Dụ (Cho Use Case "Rút Tiền" tại ATM)                                                                                                                                   |
|------------------|---------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **1. Use Case Name** | Tên của Use Case.                                                                           | Rút Tiền                                                                                                                                                                 |
| **2. Use Case ID**   | Mã định danh duy nhất cho Use Case.                                                          | UC-101                                                                                                                                                                   |
| **3. Actor**         | Actor chính và actor phụ liên quan.                                                          | **Primary:** Khách hàng  <br> **Supporting:** Hệ thống Ngân hàng                                                                                                  |
| **4. Mô tả ngắn gọn**| 1-2 câu mô tả mục đích của Use Case.                                                         | "Cho phép khách hàng rút một số tiền mặt từ tài khoản ngân hàng của họ thông qua máy ATM."                                                                               |
| **5. Preconditions (Điều kiện tiên quyết)** | Các điều kiện bắt buộc phải đúng để Use Case có thể bắt đầu.                               | 1. Khách hàng đã có thẻ ATM.<br> 2. Máy ATM đang hoạt động và có tiền.<br> 3. Khách hàng đã đăng nhập thành công.                                                       |
| **6. Postconditions (Hậu điều kiện)** | Trạng thái của hệ thống sau khi Use Case kết thúc (dù thành công hay thất bại). | **Thành công:** <br>- Số tiền được trừ khỏi tài khoản.<br>- Giao dịch được ghi vào nhật ký.<br> **Thất bại:** <br>- Giao dịch được ghi vào nhật ký với trạng thái "lỗi". |
| **7. Basic Flow (Luồng chính - Happy Path)** | Luồng các bước khi mọi thứ diễn ra suôn sẻ và thành công. Đây là kịch bản mong đợi nhất. | 1. Khách hàng chọn chức năng "Rút tiền".<br> 2. Hệ thống yêu cầu nhập số tiền.<br> 3. Khách hàng nhập số tiền.<br> 4. Hệ thống kiểm tra số dư và tính khả dụng.<br> 5. Hệ thống đưa ra tiền và thẻ.<br> 6. Hệ thống in hóa đơn.<br> 7. Use Case kết thúc. |
| **8. Alternative Flows (Luồng thay thế)** | Các nhánh thay thế hoặc bổ sung cho luồng chính. Thường bắt đầu bằng "Tại bước X của luồng chính...". | **AF1: Số dư không đủ (Tại bước 4):** <br> 4.1. Hệ thống hiển thị thông báo "Số dư không đủ".<br> 4.2. Quay lại bước 2.<br><br> **AF2: Hủy giao dịch (Tại bước 2 hoặc 3):** <br> 2.1. Khách hàng nhấn nút "Hủy".<br> 2.2. Hệ thống trả lại thẻ và kết thúc. |
| **9. Exception Flows (Luồng ngoại lệ)** | Các tình huống lỗi hoặc sự cố bất ngờ. | **EF1: Máy ATM hết tiền (Tại bước 5):** <br> 5.1. Hệ thống hiển thị lỗi "Máy tạm thời hết tiền".<br> 5.2. Hệ thống hủy giao dịch và trả lại thẻ.<br><br> **EF2: Không kết nối được với ngân hàng:** <br> 4.1. Hệ thống hiển thị lỗi "Mất kết nối".<br> 4.2. Hủy giao dịch. |

---

## So sánh Alternative Flows và Exception Flows

| Đặc Điểm   | Alternative Flows (Luồng Thay Thế)                                      | Exception Flows (Luồng Ngoại Lệ)                             |
|------------|-------------------------------------------------------------------------|--------------------------------------------------------------|
| **Bản chất**   | Là các kịch bản hợp lệ, có thể dự đoán được.                           | Là các tình huống lỗi, sự cố bất thường.                     |
| **Nguyên nhân**| Do lựa chọn của Actor hoặc một điều kiện nghiệp vụ cụ thể.             | Do hệ thống lỗi, dữ liệu không hợp lệ, hoặc điều kiện ngoài dự kiến. |
| **Mục tiêu**   | Hoàn thành mục tiêu của Use Case theo một cách khác.                  | Xử lý lỗi một cách an toàn và thông báo cho Actor.            |
| **Kết quả**    | Vẫn có thể thành công và đạt được mục tiêu.                           | Thất bại trong việc đạt được mục tiêu chính.                  |
| **Tần suất**   | Có thể xảy ra thường xuyên.                                           | Hy vọng là ít khi xảy ra.                                     |
| **Ví dụ**      | Khách hàng chọn không in hóa đơn.                                     | Máy ATM hết tiền, mất kết nối mạng.                           |

---

## Độ tương quan của Use Case Diagram và use case Scenario

| Đặc Điểm            | Use Case Diagram                                                                 | Use Case Scenario (Detail)                                                                 |
|----------------------|----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| **Mục đích chính**   | Cung cấp cái nhìn tổng quan về chức năng hệ thống và ai tương tác với nó.        | Cung cấp mô tả chi tiết về cách thức một chức năng cụ thể được thực hiện.                   |
| **Mức độ trừu tượng**| Cao - Chỉ hiển thị "What" (Cái gì) và "Who" (Ai).                                | Thấp - Mô tả "How" (Như thế nào), từng bước một.                                           |
| **Thành phần**       | Các hình hình học: Actor (hình que), Use Case (hình bầu dục), đường quan hệ.     | Văn bản có cấu trúc: Preconditions, Postconditions, Basic Flow, Alternative Flows, Exception Flows. |
| **Đối tượng hướng đến**| Tất cả stakeholders (cả kỹ thuật và không kỹ thuật) để thống nhất về phạm vi.   | Nhóm phát triển (BA, Dev, Tester) để hiểu rõ nghiệp vụ và xây dựng hệ thống.               |
| **Tính trực quan**   | Rất cao - Dễ dàng nắm bắt toàn cảnh.                                            | Thấp - Cần đọc và phân tích kỹ.                                                            |

---

## Ví Dụ Đặt Mua Hàng (Place Order)

### Use Case Diagram

```c++ 
     (Khách Hàng)
          |
          |
   +----------------+
   |  Đặt Mua Hàng  |<---------------------------+
   +----------------+                            |
          |                                      |
          | <<include>>                          | <<extend>>
          |                                      |
+------------------+                   +----------------------+
| Xác Minh Địa Chỉ |                   | Áp Dụng Mã Giảm Giá |
| Verify Address   |                   | Apply Coupon        |
+------------------+                   +----------------------+
```

### Use Case Scenario


| **Thành Phần**       | **Mô Tả** |
|-----------------------|-----------|
| **Use Case Name**     | Đặt Mua Hàng (Place Order) |
| **Actor**             | Khách hàng (Customer) |
| **Mô tả**             | Cho phép khách hàng đặt mua các sản phẩm trong giỏ hàng. |
| **Preconditions**     | 1. Khách hàng đã đăng nhập.<br>2. Giỏ hàng có ít nhất một sản phẩm. |
| **Postconditions**    | **Thành công:** Đơn hàng được tạo, trạng thái "Chờ thanh toán". |
| **Basic Flow**        | 1. Khách hàng nhấn nút **"Đặt Hàng"** từ giỏ hàng.<br>2. Hệ thống hiển thị trang xác nhận đơn hàng, bao gồm:<br>&nbsp;&nbsp;– Danh sách sản phẩm.<br>&nbsp;&nbsp;– Xác minh địa chỉ giao hàng và tính phí vận chuyển (`<<include>>`).<br>&nbsp;&nbsp;– Tính tổng tiền đơn hàng (`<<include>>`).<br>3. Khách hàng xem xét và nhấn **"Xác Nhận Đặt Hàng"**.<br>4. Hệ thống tạo đơn hàng, gửi email xác nhận (`<<include>>`).<br>5. Hệ thống hiển thị thông báo **"Đặt hàng thành công"**.<br>6. Use case kết thúc. |
| **Alternative Flows** | **AF1: Áp dụng mã giảm giá (Tại Bước 2)**<br>2.1. Khách hàng nhập mã giảm giá.<br>2.2. Hệ thống kiểm tra tính hợp lệ.<br>2.3. Nếu hợp lệ, cập nhật tổng tiền.<br>2.4. Nếu không hợp lệ, hiển thị thông báo lỗi.<br>2.5. Quay lại Bước 2.<br><br>**AF2: Chỉnh sửa địa chỉ giao hàng (Tại Bước 2)**<br>2.1. Khách hàng nhấn **"Thay đổi"** địa chỉ.<br>2.2. Hệ thống hiển thị popup chọn/thêm địa chỉ.<br>2.3. Khách hàng chọn địa chỉ mới.<br>2.4. Hệ thống xác minh & tính lại phí vận chuyển.<br>2.5. Quay lại Bước 2. |
| **Exception Flows**   | **EF1: Hết hàng (Tại Bước 4)**<br>4.1. Hệ thống phát hiện sản phẩm hết hàng.<br>4.2. Hủy đơn và báo lỗi: *"Sản phẩm [Tên SP] đã hết hàng"*. <br>4.3. Use case kết thúc thất bại. |