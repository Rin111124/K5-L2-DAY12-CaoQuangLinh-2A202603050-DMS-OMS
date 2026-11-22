# Tự đánh giá — Cao Quang Linh · G01

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_ir.png | child_seat | `seat_flip` | Thuộc tính `seat` bị CVAT tự điền mặc định `driver`; đã sửa lại thành `rear_left` | Đã sửa |
| S02_rgb.png | frame_meta | `missing` | Thiếu tag `frame_meta` khi bắt đầu gán nhãn cảnh S02 | Đã sửa |
| D01.png | face / face13 | `flag` | 4 điểm skeleton mắt phải bị lóa kính chưa bật cờ `occluded` tương ứng với `eye_right=unknown` | Đã sửa |
| D02.png | hand | `ok` | Hai bàn tay cầm chai nước và thẻ được gán đúng `whose=driver`, `side` chuẩn xác | Không có lỗi |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Quên kiểm tra lại thuộc tính mặc định (`seat = driver`) do CVAT tự động điền giá trị đầu danh sách khi vẽ box mới, và quên gắn tag `frame_meta` trước khi vẽ box.

Vì sao mình mắc: Thao tác vẽ hình liên tục theo quán tính và tập trung vào viền bao mà quên mở tab DETAILS ở thanh bên phải để rà soát từng trường thuộc tính.

Lần sau tránh bằng cách: Tuân thủ quy trình chuẩn 4 bước: (1) Đặt tag `frame_meta` ngay khi mở ảnh -> (2) Đọc to vị trí ghế theo hệ toạ độ xe -> (3) Vẽ box và chỉnh ngay DETAILS -> (4) Chạy `cabin_check.py` sau mỗi cảnh để phát hiện lỗi tức thì.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó:
Ở cảnh S03, bạn phát hiện ra chiếc cốc nước nhỏ (`cup`) nằm ngang trên đệm ghế bên trái (`rear_right`) mà lúc đầu mình nhìn lướt qua tưởng là phần bóng đổ của ghế. Mình học được bài học phải quan sát kỹ từng góc nhỏ của đệm ghế và tăng độ sáng (Brightness) trên canvas khi gặp các vật thể màu tối.
