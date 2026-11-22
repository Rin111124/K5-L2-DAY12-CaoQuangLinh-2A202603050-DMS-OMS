# Báo cáo QC — Day12 G01 (Cao Quang Linh)

## Hồ sơ

- Người nộp: **Cao Quang Linh**, mã G01.
- Người review chéo: **Nguyen Hai Dang**.
- Hai export trong gói nộp đều thuộc người nộp. Export của peer chỉ dùng để so sánh và không được đưa vào E1 của Cao Quang Linh.

## Kết quả tự kiểm

| File | Ảnh | Lỗi | Cảnh báo | Ghi chú |
|---|---:|---:|---:|---|
| `export_final.zip` | 22 | 0 | 2 | Hai cảnh báo mắt D05 được giải thích trong `check_final.txt`; V2 đã sửa hai thuộc tính mắt thành `unknown`. |
| `export_final_v2.zip` | 22 | 0 | 0 | Export của người nộp sau review. |
| `export_extra.zip` | 4 | 0 | 0 | Phần mở rộng tùy chọn. |

Các export chỉ chứa `annotations.xml`, không kèm ảnh.

## Review chéo

Diff giữa V2 của Cao Quang Linh và peer có **26 dòng**. `disagreement_log.csv` ghi đủ verdict, guideline và hành động. Theo xác nhận mới nhất của người học, hai bạn thống nhất ghi các khác biệt còn lại là `ambiguous`; log không tuyên bố hai export khớp nhau hoặc đã chứng minh nhãn nào đúng theo pixel. Hai dòng `gaze_zone` ở S02 được ghi rõ là ngoài phạm vi chấm OMS.

Hai dòng phone ở D05 là một cặp box cho cùng vật thể (IoU 0.36). Hai dòng face ở S04_ir là một cặp box cho cùng khuôn mặt (IoU 0.23). Đây là sai khác hình học, không phải hai đối tượng riêng.

## E1–E5

- **E1:** Có export gốc và export V2 của người nộp; V2 qua checker.
- **E2:** Có checkpoint A/B, check final giải thích hai cảnh báo, và check V2 sạch.
- **E3:** Có 26 dòng peer review với verdict/rule/action.
- **E4:** `ir_log.csv` có 6 quan sát, tách `real_IR` và `IR_sim`.
- **E5:** `class_list_v0.md` có 6 lớp DMS, 6 lớp OMS và 2 câu hỏi leo thang kèm ví dụ.
- Có self review, exit ticket, TEAM và khai báo AI.

Không có ảnh cabin nào được gửi cho AI.
