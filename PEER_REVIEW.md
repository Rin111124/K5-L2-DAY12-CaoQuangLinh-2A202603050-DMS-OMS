# Peer review — G01 (Cao Quang Linh)

Người gán nhãn: **Cao Quang Linh** · Người review: **Nguyen Hai Dang**. Hai export V2 được đối chiếu bằng `cabin_check diff`. Export peer chỉ dùng làm tham chiếu, không đưa vào gói nộp của Cao Quang Linh.

## Kết quả

- Export sau review của mình: 22 ảnh, 0 lỗi, 0 cảnh báo (`check_final_v2.txt`).
- Export trước review: 22 ảnh, 0 lỗi, 2 cảnh báo ở mắt D05. `check_final.txt` giải thích hai cảnh báo; V2 chuyển `eye_left` và `eye_right` thành `unknown`.
- Diff hiện tại còn 26 dòng. Theo xác nhận của người học, hai bạn thống nhất ghi các dòng còn lại là `ambiguous`; từng dòng có guideline và cách xử lý trong `disagreement_log.csv`. Điều này không có nghĩa hai export giống nhau.
- Hai khác biệt `gaze_zone` ở S02 không thuộc tiêu chí thuộc tính OMS; log ghi rõ không cần sửa chỉ để ép khớp.
- Hai dòng box `phone` D05 là một cặp box có IoU 0.36. Hai dòng `face` S04_ir là một cặp box có IoU 0.23. S04_rgb: export của mình không có box face, export peer có box; log ghi nhận đây là ca `ambiguous`.

## Ghi chú

`verdict=ambiguous` ghi nhận cách hai bạn xử lý các khác biệt còn lại. Nếu coach yêu cầu chọn một nhãn duy nhất, làm theo coach. Không dùng export của peer làm E1 của mình.
