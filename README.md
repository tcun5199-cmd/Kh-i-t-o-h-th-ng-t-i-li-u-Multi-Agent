# Dự án: Hệ thống Multi-Agent hỗ trợ lập kế hoạch du lịch tự động

Dự án này là hệ thống phần mềm ứng dụng trí tuệ nhân tạo thế hệ mới, sử dụng kiến trúc **Multi-Agent** (nhiều đại lý AI phối hợp với nhau) để tự động hóa toàn bộ quy trình lên kế hoạch du lịch. Hệ thống có khả năng tương tác với người dùng, phân tích sở thích, tìm chuyến bay, khách sạn, vẽ lịch trình và tính toán ngân sách hoàn toàn tự động.

## Cấu trúc tài liệu (Documentation)
Thư mục này chứa toàn bộ các file đặc tả phân tích và thiết kế hệ thống bao gồm:
1. `1_tai_lieu_nghiep_vu.md`: Yêu cầu nghiệp vụ, tính năng lõi và luồng hoạt động.
2. `2_tai_lieu_giao_dien_ai.md`: Thiết kế trải nghiệm người dùng (UX) và giao diện AI thực thi.
3. `3_tai_lieu_ky_thuat_frontend.md`: Chi tiết công nghệ kiến trúc phía Frontend (React/Next.js).
4. `4_tai_lieu_ky_thuat_admin.md`: Tài liệu hệ thống giám sát và quản trị AI (Monitoring & Cost).
5. `agent.md`: Đặc tả chi tiết về cấu trúc các Agent (LangGraph/CrewAI) và luồng dữ liệu truyền tải.

---

## Hướng dẫn sử dụng thư mục này trên VS Code và đẩy lên GitHub

### Bước 1: Khởi tạo trên VS Code
1. Cài đặt **Visual Studio Code** và **Git** trên máy tính.
2. Giải nén toàn bộ các file `.md` này vào một thư mục (ví dụ: `AI-Travel-Agent-Docs`).
3. Mở VS Code -> Chọn `File` -> `Open Folder...` -> Chọn thư mục vừa giải nén.
4. Bấm `Ctrl + \`` (hoặc `Cmd + \`` trên Mac) để mở Terminal tích hợp trong VS Code.

### Bước 2: Khởi tạo kho lưu trữ Git (Git Init)
Tại Terminal, chạy lần lượt các lệnh sau:
```bash
# Khởi tạo repository cục bộ
git init

# Thêm tất cả các file tài liệu vào vùng chờ (staging area)
git add .

# Tạo commit đầu tiên
git commit -m "Init: Khởi tạo tài liệu dự án Multi-Agent Travel Planning"
```

### Bước 3: Đẩy mã nguồn lên GitHub (Push to GitHub)
1. Truy cập vào tài khoản [GitHub](https://github.com/), bấm dấu `+` góc trên bên phải và chọn **New repository**.
2. Đặt tên (ví dụ: `ai-travel-docs`), để chế độ Public/Private tùy ý và bấm **Create repository**.
3. Quay lại Terminal trên VS Code, chạy các lệnh cấu hình và đẩy code lên:
```bash
# Định dạng nhánh chính là main
git branch -M main

# Thay đổi <url-cua-repo> thành link GitHub của bạn (vd: https://github.com/username/ai-travel-docs.git)
git remote add origin <url-cua-repo>

# Đẩy mã nguồn lên GitHub
git push -u origin main
```
Xong! Bây giờ bạn đã có thể gửi link GitHub cho giảng viên hoặc thành viên nhóm để xem các tài liệu Markdown này một cách cực kỳ chuyên nghiệp.
