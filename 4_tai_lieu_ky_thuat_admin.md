# Tài liệu Kỹ thuật AI phía Admin

## 1. Tổng quan
Hệ thống Admin Panel là trung tâm điều khiển giúp quản trị viên theo dõi luồng giao tiếp nội bộ của các Agent, quản lý chi phí API, và điều chỉnh/tinh chỉnh hành vi của hệ thống AI.

## 2. Công nghệ sử dụng
- **Framework Frontend:** React SPA (Vite) / Next.js Admin Template.
- **Biểu đồ & Thống kê:** Recharts hoặc Chart.js (Theo dõi token usage và request).
- **Backend tương tác:** Python FastAPI / Node.js Express.

## 3. Các module chức năng chính
1. **Agent Monitoring (Giám sát Agent):**
   - Theo dõi System Logs của các cuộc hội thoại giữa các Agent (Agent-to-Agent communication) - nội dung thường được ẩn khỏi người dùng cuối.
   - Xác định và debug Agent nào đang gây ra lỗi (ví dụ: Transport Agent gọi API bị timeout, hoặc Critic Agent đi vào vòng lặp vô tận).
2. **Prompt Management (Quản lý Prompt):**
   - Cung cấp giao diện trực quan cho phép cập nhật System Prompt của từng Agent (Orchestrator, Critic, Transport...) ngay trên UI mà không cần deploy lại code.
   - Hỗ trợ Version Control cho Prompt (Lưu lại lịch sử thay đổi để rollback khi cần).
3. **API Keys & Cost Dashboard:**
   - Cấu hình và xoay vòng (rotate) các API Key an toàn: OpenAI, Gemini, Google Maps, Amadeus.
   - Hiển thị thống kê số lượng Token đã tiêu thụ, tính toán chi phí thực tế (USD) theo ngày/tuần/tháng để cảnh báo giới hạn.
4. **User Feedback & Evaluation (Đánh giá chất lượng):**
   - Thu thập và lưu trữ các kế hoạch bị người dùng đánh giá kém (Thumb down).
   - Cung cấp tính năng "Re-run test" cho admin để đưa ngữ cảnh lỗi vào chạy lại, nhằm điều chỉnh lại tham số của Agent cho chính xác hơn.
