# State Machine Diagram (Statechart Diagram)

**State Machine Diagram** (hoặc **Statechart Diagram**) là **behavioral diagram** mô tả **sự thay đổi trạng thái của một đối tượng** khi có các **sự kiện (events)** xảy ra.

| Loại | Giải thích | Ứng dụng |
|------|-------------|-----------|
| **Behavioral State Machine** | Mô tả hành vi của một đối tượng thông qua trạng thái và chuyển tiếp. | ATM, đơn hàng, luồng actor |
| **Protocol State Machine** | Mô tả quy tắc giao tiếp giữa các đối tượng. | Quy tắc API, protocol giao tiếp |

---

**Thành phần chính**

| Thành phần | Ký hiệu / Mô tả |
|-------------|------------------|
| **State** | Trạng thái của đối tượng (Idle, Processing, Completed, …) |
| **Transition** | Mũi tên chỉ ra sự chuyển đổi giữa các trạng thái |
| **Event / Trigger** | Sự kiện gây ra chuyển đổi |
| **Guard [ ]** | Điều kiện để chuyển đổi xảy ra |
| **Action / Effect** | Hành động được thực hiện khi chuyển đổi |
| **Initial State (●)** | Trạng thái bắt đầu |
| **Final State (◎)** | Trạng thái kết thúc |
| **Composite State** | Trạng thái chứa các trạng thái con |
| **Submachine State** | Tham chiếu đến một state machine khác |

![](https://guides.visual-paradigm.com/wp-content/uploads/2023/09/state-machine-diagram-explained.png)

**Các loại Pseudostate**

| Loại | Ký hiệu | Ý nghĩa |
|------|----------|----------|
| **Initial** | ● | Bắt đầu |
| **Final** | ◎ | Kết thúc |
| **Choice** | ◆ | Rẽ nhánh theo điều kiện động |
| **Junction** | ● nhỏ | Nối nhiều nhánh thành một |
| **Fork / Join** | ▬ | Chia hoặc hợp luồng song song |
| **Entry / Exit Point** | ⊙ / ⊗ | Điểm vào hoặc ra của composite state |
| **Shallow History (H)** | H | Ghi nhớ trạng thái con cuối |
| **Deep History (H\*)** | H* | Ghi nhớ toàn bộ cấu hình trước đó |

![](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/UML-state-diagram-tutorial/state_diagram_scheduling_system-740x860.pngg)
