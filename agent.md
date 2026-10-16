# Tài liệu Cấu trúc Kỹ thuật Multi-Agent (Agent Architecture)

## 1. Mô hình kiến trúc cốt lõi
Hệ thống sử dụng mô hình luồng làm việc đồ thị dựa trên trạng thái (State-based Graph Workflow), khuyến nghị sử dụng **LangGraph** (vì kiểm soát flow cực tốt) hoặc **CrewAI**.

## 2. Các Agent tham gia (The Crew)

### 2.1. Orchestrator Agent (Điều phối viên)
- **Vai trò:** Là bộ não tiếp xúc trực tiếp với người dùng. Phân tích ngôn ngữ tự nhiên để hiểu ngữ cảnh, trích xuất thực thể (Điểm đến, Ngày giờ, Ngân sách).
- **Hành động:** 
  - Nếu thiếu thông tin: Gọi tool trả lời để hỏi thêm người dùng.
  - Nếu đủ thông tin: Phân rã yêu cầu (Task Breakdown) và phân công cho các sub-agents.
- **Prompt định hướng:** *"Bạn là Điều phối viên Du lịch. Nhiệm vụ của bạn là nhận yêu cầu của người dùng, làm rõ thông tin và chuyển giao nhiệm vụ cho Transport, Accommodation và Itinerary agents."*

### 2.2. Transport Agent (Đại lý Di chuyển)
- **Vai trò:** Chuyên môn hóa việc tìm kiếm thông tin vé máy bay, xe khách dựa trên địa điểm xuất phát và đích đến.
- **Công cụ (Tools Call):** `search_flights(origin, dest, date)`, `search_bus(origin, dest, date)`.

### 2.3. Accommodation Agent (Đại lý Lưu trú)
- **Vai trò:** Tìm kiếm khách sạn/homestay. Đặc biệt phải có khả năng hiểu ngữ nghĩa các yêu cầu về phong cách (chill, vintage, sôi động).
- **Công cụ (Tools Call):** `search_hotels(location, check_in, check_out, max_budget)`.

### 2.4. Itinerary Agent (Đại lý Lịch trình & Địa phương)
- **Vai trò:** Chuyên gia địa phương. Sắp xếp các điểm tham quan, ăn uống theo từng ngày, đảm bảo tính logic về khoảng cách địa lý và thời gian mở cửa.
- **Công cụ (Tools Call):** `search_places_api(location, type)`, `calculate_routing_distance(place_A, place_B)`.

### 2.5. Critic / Budget Agent (Giám sát viên)
- **Vai trò:** Agent độc lập có nhiệm vụ "bắt lỗi". Nó sẽ nhận kết quả từ 3 Agent trên để kiểm tra chéo (Cross-check).
- **Hành động:** 
  - Cộng tổng chi phí -> So sánh với Ngân sách. Vượt -> Báo lỗi yêu cầu tìm lại.
  - Kiểm tra tính logic di chuyển (VD: Máy bay đáp lúc 14h nhưng lịch trình có đi ăn trưa lúc 12h ở điểm đến -> Phi logic -> Báo lỗi sửa lại).
  - Nếu duyệt (Pass), sẽ đóng gói dữ liệu đẩy về Orchestrator.

## 3. Cấu trúc Quản lý Trạng thái (Shared State Schema)
Các Agent không nói chuyện phiếm, chúng cập nhật chung vào một bảng trạng thái trung tâm. Dưới đây là cấu trúc State:
```typescript
interface TravelState {
    user_request: string;
    constraints: {
        budget_vnd: number;
        start_date: string;
        end_date: string;
        destination: string;
    };
    transport_plan: Array<object>;
    accommodation_plan: object | null;
    itinerary_plan: Array<object>;
    total_estimated_cost: number;
    agent_status: 'gathering_info' | 'fetching_data' | 'critic_reviewing' | 'completed';
}
```
