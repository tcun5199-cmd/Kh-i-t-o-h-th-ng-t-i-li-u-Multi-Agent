# Tài liệu Kỹ thuật AI phía Frontend

## 1. Công nghệ sử dụng
- **Framework:** Next.js (React) + TypeScript.
- **Styling:** Tailwind CSS + Shadcn UI (cho các component giao diện đẹp và chuẩn).
- **State Management:** Zustand hoặc Redux Toolkit (quản lý state phức tạp của lịch trình và lịch sử hội thoại).
- **Kết nối AI:** Server-Sent Events (SSE) hoặc WebSockets để nhận dữ liệu streaming liên tục từ backend.

## 2. Xử lý Streaming Output từ LLM
- Bản chất của AI tạo sinh là sinh ra dữ liệu từng từ (token) một. Frontend cần sử dụng kỹ thuật stream rendering để hiển thị ngay lập tức văn bản thay vì chờ phản hồi hoàn tất.
- Khi AI trả về cấu trúc dữ liệu JSON của lịch trình dưới dạng luồng, Frontend cần có một cơ chế phân tích cú pháp một phần (partial JSON parsing) để render dần các khối lịch trình (thẻ khách sạn, thẻ quán ăn) lên màn hình ngay cả khi JSON chưa đóng dấu ngoặc cuối cùng.

## 3. Cấu trúc Component cốt lõi (Component Architecture)
- `ChatContainer`: Chứa danh sách tin nhắn (`MessageList`) và khu vực nhập liệu (`MessageInput`).
- `AgentTypingIndicator`: Component trực quan hóa luồng tư duy của nhiều Agent cùng lúc.
- `ItineraryBoard`: Khu vực hiển thị kết quả.
  - `DayTimeline`: Render danh sách các hoạt động trong một ngày.
  - `ItemCard`: Component hiển thị chi tiết 1 địa điểm tham quan/chuyến bay.
- `MapView`: Tích hợp Google Maps JS API hoặc Mapbox để vẽ các mốc tọa độ (lat, lng) tạo thành tuyến đường du lịch (Routing).
