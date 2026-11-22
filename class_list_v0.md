# Danh sách lớp v0 — Cao Quang Linh · G01

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `eye_state` (left & right) | open / closed / unknown | Phát hiện dấu hiệu buồn ngủ, vi mô ngủ (microsleep khi mắt nhắm quá 1.5 - 2s) để kích hoạt còi cảnh báo rung ghế/âm thanh | Có, trừ khi tròng kính bị đốm phản xạ LED hồng ngoại che khuất |
| 2 | `gaze_zone` | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện mất tập trung (distraction): cảnh báo nếu tài xế nhìn xuống đùi (lap) hoặc nhìn màn hình giải trí (center) quá 3 giây khi xe đang chạy | Có, kết hợp hướng xoay đầu (head pose) và vị trí con ngươi mắt |
| 3 | `glasses` | none / clear / sun / unknown | Tự động kích hoạt bộ lọc triệt tiêu phản xạ lóa tròng kính trên camera hồng ngoại; nhận biết kính râm để chuyển sang theo dõi tư thế đầu | Có; ánh sáng hồng ngoại gần (NIR) thậm chí có thể nhìn xuyên qua một số loại kính râm |
| 4 | `face13` (facial keypoints) | 13 tọa độ giải phẫu (mắt, mũi, miệng) | Ước lượng chính xác góc nghiêng đầu 3D (yaw, pitch, roll); tính tỷ lệ EAR (mở mắt) và MAR (mở miệng - phát hiện ngáp) | Có, các điểm bị che bởi tay/vật cản thì gán cờ `occluded` |
| 5 | `hand_on_wheel` | yes / no / unknown | Giám sát mức độ sẵn sàng tiếp quản quyền điều khiển (Hands-On Detection) trong các hệ thống lái tự động cấp độ L2/L3 ADAS | Có, phân biệt rõ ranh giới bàn tay và vành vô lăng |
| 6 | `phone_state` | held / mounted / lap | Phát hiện hành vi sử dụng điện thoại trái quy định khi tham gia giao thông (nghe điện thoại áp tai, cầm tay nhắn tin) | Có, nhận diện qua hình chữ nhật phẳng có độ phản xạ đặc trưng và tư thế bàn tay cầm |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `occupancy_state` | empty / person / child_seat / infant_seat / object | Quản lý logic an toàn khoang cabin: bật/tắt nhắc nhở thắt dây an toàn cho từng ghế và phân loại tải trọng cho túi khí thông minh | Có, dựa vào đặc trưng hình học 3D của đối tượng |
| 2 | `seatbelt` | worn_correct / worn_incorrect / not_worn / unknown | Cảnh báo hành khách chưa thắt dây an toàn hoặc thắt sai quy cách (luồn sau lưng, dưới nách) gây nguy hiểm khi va chạm | Có, dựa trên vệt phản xạ chéo của dải dây dệt qua ngực |
| 3 | `infant_seat_facing` | rear / front | Tự động vô hiệu hóa túi khí phía trước nếu phát hiện nôi em bé quay ngược (rear-facing), tránh nguy cơ túi khí nổ chấn thương trẻ | Có, nhận biết qua quai xách và góc nghiêng của nôi |
| 4 | `child_seat_occupied` | no / unknown / yes | Phát hiện trẻ em ngồi trên ghế an toàn (Child Presence Detection - CPD theo chuẩn Euro NCAP), kích hoạt cảnh báo chống bỏ quên trẻ trong xe | Có, nhận biết qua hình thể trẻ hoặc cử động bên trong ghế |
| 5 | `leftover_object` | bag / box / cup / other | Cảnh báo bỏ quên đồ đạc giá trị (túi xách, ba lô, laptop) hoặc cảnh báo vật thể nguy hiểm có thể lăn trượt trong cabin | Có, nhận dạng theo khối hình học |
| 6 | `passenger_position` | normal / out_of_position (OOP) | Xác định hành khách ngồi sai tư thế (nằm ngửa, nhoài người về trước) để điều chỉnh lực bung túi khí hai giai đoạn phù hợp | Có, theo dõi qua bounding box cơ thể và vị trí đầu/mặt |

## 2 câu hỏi leo thang

Câu hỏi gửi Product Owner / Lead thiết kế guideline:

1. **Câu hỏi:** Trong Guideline Cabin v1.0, tại sao thuộc tính `occupied` của nhãn `child_seat` chỉ có 2 giá trị là `no` (trống) và `unknown` mà không có giá trị `yes` khi quan sát thấy rõ ràng có trẻ em/hình nộm đang ngồi bên trong?  
   **Khung ví dụ:** `S03_rgb.png` (có hình nộm bé trai ngồi trên ghế trẻ em) và `S05_rgb.png` (cả 2 ghế trẻ em đều có hình nộm ngồi).  
   **Bạn tạm gán thế nào và vì sao:** Tạm gán `occupied = yes` (sau khi được Coach cho phép) hoặc gán `occupied = unknown` theo đúng schema v1.0, vì việc có nhãn `yes` là cực kỳ quan trọng cho tính năng an toàn CPD (Child Presence Detection) của OMS.

2. **Câu hỏi:** Trong tập dữ liệu SVIRO, toàn bộ các khung hình đều không có người thắt dây an toàn (`seatbelt` chỉ là `not_worn` hoặc `unknown`). Với tập dữ liệu huấn luyện hoàn toàn thiếu mẫu dương tính (positive samples) cho hành vi thắt dây đúng (`worn_correct`), mô hình sẽ gặp hiện tượng mất cân bằng dữ liệu nghiêm trọng. Đội dự án dự định bổ sung dữ liệu thực tế hay giải pháp nào cho lớp `worn_correct`?  
   **Khung ví dụ:** `S02_rgb.png` và `S04_rgb.png`.  
   **Bạn tạm gán thế nào và vì sao:** Tạm gán `seatbelt = not_worn` đúng theo thực tế ảnh quan sát được, không suy đoán.
