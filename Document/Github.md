# 📖 Hướng dẫn sử dụng GitHub cho dự án

## 1️⃣ Tạo Organization
- Vào [GitHub Organizations](https://github.com/account/organizations).  
- Tạo một **organization** riêng cho nhóm (ví dụ: `HCMUT-TSS`).  
- Đây sẽ là nơi quản lý tất cả repositories của dự án.  

---

## 2️⃣ Mời Thành Viên
- Vào **Settings → People** trong Organization.  
- Mời các thành viên nhóm bằng GitHub username hoặc email.  
- Phân quyền:
  - **Owner**: quản lý toàn bộ (leader).  
  - **Member**: thành viên phát triển.  

---

## 3️⃣ Tạo Các Repositories trong Organization

### 📂 Frontend
- Kết nối với **AI và Figma**.  
- AI có thể hỗ trợ sinh ra code Frontend khá mạnh → chỉ cần tinh chỉnh.  

### 📂 Backend
- Ngôn ngữ khuyến nghị: **NestJS (TypeScript)**.  
- Cấu trúc rõ ràng, dễ học và dễ mở rộng.  

### 📂 HCMUT_SSO (anh sẽ cung cấp bộ API cho các bạn gọi vào)
- Repository quản lý **Single Sign-On (SSO)**.  
- Cung cấp danh sách API cho toàn hệ thống truy cập.  

### 📂 HCMUT_DATACORE (anh sẽ cung cấp bộ API cho các bạn gọi vào)
- Repository quản lý dữ liệu **sinh viên/giảng viên**.  
- Chứa các API để chia sẻ dữ liệu từ hệ thống trung tâm.  

### 📂 HCMUT_LIBRARY (anh sẽ cung cấp bộ API cho các bạn gọi vào)
- Repository quản lý **học liệu, tài liệu, giáo trình**.  
- Chứa các API cho student/tutor truy cập tài nguyên.  

### 📂 DEVOP
- Repository dùng để cấu hình **DevOps**:
  - `docker-compose.yml`  
  - Script cấu hình môi trường local  
  - Hỗ trợ chạy dự án bằng **Docker** → không cần cài đặt phức tạp.  


## 4️⃣ Quy tắc Code (Workflow)

1. **Tạo nhánh mới** cho mỗi tính năng/bug fix:  
2. **Commit code** vào nhánh đó:
3. **Tạo Pull Request (PR)** trên GitHub từ nhánh của bạn → main.
4. **Admin/Leader review và merge**: tránh xung đột (không được push -f main)
