# Quiz Platform Workspace

Đây là workspace khởi tạo cho hệ thống web làm quiz online theo mô hình phân quyền 3 vai trò:

- `Student`: làm quiz, xem kết quả, theo dõi lịch sử
- `Teacher`: tạo quiz, quản lý câu hỏi, giao bài, xem kết quả học sinh
- `Admin`: quản lý người dùng, vai trò và kiểm duyệt nội dung

Mục tiêu của cấu trúc này là tách rõ phần giao diện, API và dữ liệu để dễ phát triển theo từng giai đoạn.

## Cấu trúc dự án

### `frontend`
Giao diện người dùng của hệ thống.

- `src/pages/auth`: Login, Register, Forgot Password, Reset Password
- `src/pages/shared`: Landing Page, User Profile
- `src/pages/student`: Dashboard, Quiz List, Quiz Detail, Take Quiz, Result, History, Class
- `src/pages/teacher`: Dashboard, Quiz Management, Question Management, Assignment, Student Results, Class Management
- `src/pages/admin`: Dashboard, User Management, Role Management, Quiz Moderation
- `src/components`: các component dùng chung
- `src/services`: service gọi API
- `src/styles`: style và theme

### `backend`
API server sử dụng ASP.NET Core.

- `Program.cs`: điểm khởi động ứng dụng
- `appsettings.json`: cấu hình tổng
- `appsettings.Development.json`: cấu hình môi trường dev
- `Controllers`: các API controller
- `Models`: entity/model dữ liệu
- `Services`: nghiệp vụ
- `Data`: DbContext, seeding, repository nếu cần
- `DTOs`: request/response model
- `Middleware`: các middleware tùy chỉnh
- `Properties`: cấu hình launch và metadata

### `database`
Nơi lưu schema, migration và ghi chú thiết kế database.

- `schema.sql`: file mô tả schema khởi tạo
- `migrations`: nơi đặt migration scripts

## Cách chạy

### Yêu cầu môi trường

- .NET 8 SDK
- SQL Server hoặc hệ quản trị CSDL tương đương
- Visual Studio Code hoặc Visual Studio

### Chạy backend

```bash
cd backend
dotnet restore
dotnet run
```

Sau khi chạy, API mặc định sẽ có endpoint kiểm tra sức khỏe tại `/health`.

### Chạy frontend

Phần `frontend` hiện mới là cấu trúc khởi tạo. Khi chọn framework cụ thể như React, Vue hoặc Next.js, hãy tạo project trong thư mục này và kết nối với API ở `backend`.

### Database

File `database/schema.sql` đang là placeholder. Khi chốt thiết kế bảng, hãy cập nhật schema và thêm migration tương ứng vào `database/migrations`.

## Quy ước pull GitHub

Để làm việc nhóm ổn định, thống nhất quy trình sau:

1. Luôn pull trước khi bắt đầu làm việc để đồng bộ với nhánh chính.
2. Tạo nhánh riêng cho từng task, không làm trực tiếp trên `main`.
3. Trước khi push, kiểm tra lại code, chạy build hoặc test nếu có.
4. Chỉ tạo pull request khi task đã hoàn chỉnh và không còn lỗi rõ ràng.
5. Không force push nếu không thật sự cần.
6. Nếu có conflict khi pull, xử lý xong conflict rồi mới tiếp tục commit.
7. Commit message nên ngắn gọn, rõ ý, ví dụ: `feat: add quiz detail page`.

## Gợi ý phát triển tiếp

1. Chọn framework cho `frontend`.
2. Thiết kế database chi tiết cho user, quiz, question, class, assignment và result.
3. Xây dựng API cho xác thực, quản lý quiz và phân quyền.
