# Tài liệu Nghiệp vụ: Hệ thống Multi-Agent hỗ trợ lập kế hoạch du lịch

## 1. Mục tiêu dự án
Xây dựng một hệ thống AI tự động hóa hoàn toàn quá trình lập kế hoạch du lịch, giúp người dùng tiết kiệm thời gian tìm kiếm chuyến bay, khách sạn và lên lịch trình tham quan.

## 2. Đối tượng người dùng
- Khách du lịch tự túc.
- Những người bận rộn không có thời gian lên kế hoạch chi tiết.
- Các gia đình/nhóm bạn cần tối ưu hóa ngân sách và lịch trình.

## 3. Các tính năng cốt lõi (Core Features)
1. **Thu thập yêu cầu:** Chatbot AI trò chuyện tự nhiên để lấy thông tin: địa điểm, thời gian, ngân sách, sở thích (ví dụ: chữa lành, mạo hiểm, ẩm thực).
2. **Tìm kiếm phương tiện di chuyển:** Tự động tìm vé máy bay/xe khách tối ưu chi phí và thời gian.
3. **Tìm kiếm nơi lưu trú:** Đề xuất khách sạn/homestay phù hợp với tiêu chí và vị trí các điểm tham quan.
4. **Lập lịch trình chi tiết:** Sắp xếp các điểm tham quan, quán ăn theo từng ngày, tối ưu hóa cung đường (tránh tình trạng di chuyển vòng vèo).
5. **Kiểm soát ngân sách:** Đảm bảo tổng chi phí dự kiến không vượt quá ngân sách người dùng đề ra.

## 4. Luồng nghiệp vụ (Business Flow)
1. User nhập yêu cầu -> Hệ thống phân tích -> Tạo các Task song song.
2. Các Agent (Di chuyển, Lưu trú, Lịch trình) tự động tìm kiếm thông tin thông qua API bên thứ ba.
3. Agent Giám sát tổng hợp, tính toán lại tổng chi phí.
4. Xuất bản nháp kế hoạch cho người dùng xem xét -> Người dùng có thể yêu cầu sửa đổi một phần (ví dụ: "Đổi khách sạn khác").
5. Chốt lịch trình -> Trả về danh sách liên kết đặt vé/phòng.
