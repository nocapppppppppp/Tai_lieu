
# Class diagram

**Class diagram (sơ đồ lớp)** là một **sơ đồ UML** mô tả **cấu trúc của hệ thống** thông qua các **lớp (class)**, **thuộc tính (attributes)**, **phương thức (methods)**, và **mối quan hệ** giữa các lớp.

![](https://www.uml-diagrams.org/class-diagrams/class-diagram-implementation-elements.png)

## **1. Class (Lớp)**

* Là **mô hình tổng quát (template)** mô tả một **đối tượng (object)**.
* Gồm:
  * **Tên lớp**
  * **Thuộc tính (attributes / properties)**
  * **Phương thức (methods / operations)**
* Ví dụ:

  ```plaintext
  +--------------------+
  |    Student         |
  +--------------------+
  | - name: String     |
  | - id: int          |
  +--------------------+
  | + enroll(): void   |
  | + study(): void    |
  +--------------------+
  ```

---

## **2. Interface**

* Là **bộ khung (contract)** định nghĩa **các hành vi (methods)** mà lớp **phải triển khai (implement)**.
* Không chứa dữ liệu cụ thể, chỉ chứa khai báo.
* Dùng để tạo tính **đa hình (polymorphism)**.

![](https://www.uml-diagrams.org/class-diagrams/class-interface-compartments.png)


---

## **3. Data Type**

* Là **kiểu dữ liệu cơ bản hoặc tự định nghĩa** dùng trong các thuộc tính/lớp.
* Ví dụ: `int`, `string`, `float`, hoặc kiểu tự tạo như `Date`, `Address`.

---

## **4. Property (Attribute)**

* Là **thuộc tính / biến dữ liệu** của lớp.
* Mô tả **đặc điểm** của đối tượng.
* Ví dụ: `name`, `age`, `price`, `balance`.

---

## **5. Operation (Method)**

* Là **hành vi hoặc chức năng** mà lớp có thể thực hiện.
* Gồm **tên**, **tham số**, **kiểu trả về**.
* Ví dụ:

```plaintext
+ withdraw(amount: double): void
```

---

## **6. Multiplicity**

* Mô tả **số lượng đối tượng** trong một mối quan hệ.
* Ví dụ:

  * `1` → một đối tượng duy nhất
  * `0..1` → có thể có hoặc không
  * `1..*` → ít nhất một
  * `*` → nhiều (không giới hạn)
* Ví dụ: Một `Department` có `1..* Employee`.

---

## **7. Visibility**

* Chỉ rõ **mức độ truy cập (access modifier)** của thuộc tính hoặc phương thức.
  | Ký hiệu | Loại | Ý nghĩa |
  |----------|--------|----------|
  | `+` | public | Truy cập được ở mọi nơi |
  | `-` | private | Chỉ trong cùng lớp |
  | `#` | protected | Trong lớp và lớp con |
  | `~` | package | Trong cùng gói |

![](https://www.uml-diagrams.org/class-diagrams/class-operation-visibility.png)

---

## **8. Constraint (Ràng buộc)**

* Mô tả **điều kiện hoặc quy tắc** phải thỏa mãn.
* Viết trong dấu ngoặc nhọn `{}`.

![](https://www.uml-diagrams.org/class-diagrams/class-constraint-attribute.png)

---

## **9. Object**

* Là **thể hiện cụ thể (instance)** của một lớp.
* Biểu diễn trong UML bằng tên:

  ```
  student1: Student
  ```

---

## **10. Generalization (Kế thừa – inheritance)**

* Mô tả mối quan hệ **is-a** giữa lớp cha và lớp con.
* Biểu diễn bằng **mũi tên rỗng hướng lên trên**.
* Ví dụ:

  ```
  Animal ⟵ Dog
  Animal ⟵ Cat
  ```

---

## **11. Dependency (Phụ thuộc)**

* Một lớp **phụ thuộc tạm thời** vào lớp khác (dùng trong method, truyền tham số,...).
* Biểu diễn bằng **mũi tên nét đứt →**.
* Ví dụ:

  * `Student → Course` (Student dùng Course trong hàm `register()`)

---

## **12. Abstraction**

* Là khái niệm trừu tượng hóa (abstract class / interface).
* Dùng để **định nghĩa khung hành vi** mà lớp con cụ thể sẽ **thực thi**.
* Ký hiệu bằng chữ nghiêng hoặc `{abstract}`.
  Ví dụ:

  ```
  abstract class Shape
  + area(): double
  ```

---

## **13. Nested Classifiers (Lớp lồng nhau)**

* Một lớp được **định nghĩa bên trong lớp khác**.
* Dùng để nhóm các lớp có liên quan chặt chẽ.
* Ví dụ:

  ```plaintext
  class University {
      class Department {
      }
  }
  ```
## **14. Association – Aggregation – Composition**

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhSejrYsJxJYXxrG9iDCPCAaT6hffYlrJjXeUPy7G_RvnthyAaAv31n4aLRRDS8twoiRwWK-Otp1Fwu9N3TzqGx8RqPUFQUbd-PPsviXqH5z3wSc59QbaOE9fAD81_W73lLWPtAuNJ8PDHi/s1600/Association,+Composition+UML.JPG)

| **Tiêu chí**                   | **Association (Kết hợp)**                                                                                                   | **Aggregation (Tập hợp)**                                                                                      | **Composition (Thành phần)**                                                                            |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Định nghĩa**                 | Là **mối quan hệ tổng quát** giữa hai lớp, biểu thị rằng các đối tượng của lớp này **liên quan** đến đối tượng của lớp kia. | Là **mối quan hệ “whole–part” (toàn thể–bộ phận)**, trong đó **các phần có thể tồn tại độc lập** với toàn thể. | Là **mối quan hệ “whole–part” mạnh hơn**, trong đó **các phần không thể tồn tại độc lập** với toàn thể. |
| **Độ chặt (mức độ phụ thuộc)** | Quan hệ **lỏng lẻo**, chỉ là sự kết nối logic.                                                                              | Quan hệ **trung bình**, có liên kết “has-a” nhưng vẫn độc lập.                                                 | Quan hệ **chặt chẽ**, ràng buộc sinh–tử (“owns-a” hoặc “contains-a”).                                   |
| **Ký hiệu UML**                | Đường kẻ đơn giản giữa hai lớp.                                                                                             | Đường kẻ có **hình thoi rỗng (◇)** ở đầu lớp “toàn thể”.                                                       | Đường kẻ có **hình thoi đặc (◆)** ở đầu lớp “toàn thể”.                                                 |
| **Vòng đời (lifecycle)**       | Các đối tượng tồn tại **độc lập** nhau.                                                                                     | “Phần” có thể tồn tại **độc lập** với “toàn thể”.                                                              | “Phần” **phụ thuộc hoàn toàn** vào “toàn thể”; nếu “toàn thể” bị hủy, “phần” cũng bị hủy.               |
| **Ví dụ thực tế**              | `Student` ↔ `Course` – Sinh viên có thể học nhiều khóa, khóa có nhiều sinh viên.                                            | `Department` ◇– `Teacher` – Giáo viên thuộc một khoa, nhưng giáo viên vẫn tồn tại nếu khoa bị xóa.             | `House` ◆– `Room` – Phòng không thể tồn tại nếu căn nhà bị phá.                                         |
| **Loại quan hệ**               | “Uses” hoặc “knows”                                                                                                         | “Has-a” (sở hữu yếu)                                                                                           | “Owns-a” (sở hữu mạnh)                                                                                  |
| **Tính kế thừa**               | Không có quan hệ sở hữu                                                                                                     | Có quan hệ sở hữu một phần                                                                                     | Có quan hệ sở hữu hoàn toàn                                                                             |

---

# Method descriptions

**Method descriptions** nghĩa là **mô tả chi tiết cho từng phương thức (method)** trong các lớp của sơ đồ lớp (class diagram).
Nói cách khác, khi anh đã có **class diagram** — tức là đã biết mỗi lớp có những **thuộc tính (attributes)** và **phương thức (methods)** nào — thì phần **method descriptions** chính là **phần tài liệu hóa chi tiết** cách mà từng phương thức hoạt động.