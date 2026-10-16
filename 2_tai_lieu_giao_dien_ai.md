# Tài liệu Giao diện AI Thực thi (AI Execution Interface)

## 1. Tổng quan UI/UX
Giao diện kết hợp giữa **Conversational UI** (Chatbot) và **Dashboard UI** (Trình bày dữ liệu trực quan), mang lại trải nghiệm tương tác tự nhiên nhưng vẫn giữ được sự rõ ràng của thông tin.

## 2. Cấu trúc màn hình chính
- **Cột trái (Chat Window):** Nơi người dùng trò chuyện tự nhiên với hệ thống (Orchestrator Agent). Hỗ trợ hiển thị Streaming text để tạo cảm giác AI đang suy nghĩ và phản hồi theo thời gian thực.
- **Cột phải (Itinerary Dashboard):** 
  - **Tab 1: Tổng quan:** Bản đồ điểm đến, tổng chi phí dự kiến, biểu đồ tròn phân bổ ngân sách.
  - **Tab 2: Lịch trình:** Timeline dạng cây (Tree/Timeline) hiển thị chi tiết lịch trình theo từng ngày, từng giờ. Các khối (cards) hiển thị tên khách sạn, chuyến bay, quán ăn kèm hình ảnh thumbnail và giá dự kiến.
  - **Tab 3: Tùy chỉnh:** Cho phép người dùng kéo thả (drag & drop) để đổi thứ tự điểm đến hoặc bấm "Regenerate" (Tạo lại) cho một điểm tham quan cụ thể.

## 3. Tương tác với Agent
- **Trạng thái đa Agent (Agent Status Indicators):** Hiển thị các chỉ báo loading trực quan khi các Agent đang làm việc: *VD: "Agent Khách sạn đang check giá phòng...", "Agent Lịch trình đang vẽ bản đồ..."*.
- **Human-in-the-loop (Sự tham gia của con người):** Các nút hành động nhanh như [Duyệt kế hoạch], [Đổi chỗ ở], [Giảm ngân sách] sẽ tự động xuất hiện trong khung chat khi AI trình bày xong bản nháp, giúp người dùng điều khiển dễ dàng mà không cần phải gõ phím.
