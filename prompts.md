# Khai báo dùng AI — Cao Quang Linh

Không dùng AI thì xóa bảng và ghi: **Không dùng.**

Nhắc lại: không đưa ảnh cabin hay ảnh tài xế (kể cả ảnh chụp màn hình) cho bất kỳ công cụ AI nào.

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | Antigravity AI (Google DeepMind) | Giải thích quy tắc gọi tên ghế OMS theo hệ quy chiếu xe và quy tắc trái/phải trên ảnh DMS xoay 90° | Áp dụng để định vị đúng ghế `rear_right` (trái ảnh) và `rear_left` (phải ảnh) trong SVIRO, xác định mắt trái có y lớn hơn mắt phải | Có, kiểm tra lại bằng tài liệu GUIDE.md và sơ đồ xe BMW X5 |
| 2 | Antigravity AI (Google DeepMind) | Hướng dẫn sửa lỗi `cabin_check.py` khi gặp cảnh báo về cờ occluded của `face13` và thuộc tính `occupied` | Điều chỉnh lại logic cờ `occluded` cho mắt bị lóa kính trên ảnh D01 và cập nhật schema chấp nhận `occupied = yes` | Có, chạy lại lệnh `python scripts/cabin_check.py` đạt 0 lỗi |
| 3 | Antigravity AI (Google DeepMind) | Gợi ý ý tưởng cho 6 lớp chức năng DMS, 6 lớp OMS và 2 câu hỏi leo thang trong `class_list_v0.md` | Hoàn thiện bảng chức năng cho model an toàn cabin xe hơi và câu hỏi về positive samples cho dây an toàn | Có, đối chiếu với slide bài giảng Ngày 12 |
| 4 | ChatGPT (Codex) | Đối chiếu export CVAT và các file QC/review; hoàn thiện báo cáo | Dùng diff/check và guideline để cập nhật log, check reports, TEAM và gói nộp; nhãn ambiguous giữ theo thỏa thuận | Có, chạy cabin_check và đối chiếu GUIDE/RULES; không gửi ảnh cabin cho AI |
