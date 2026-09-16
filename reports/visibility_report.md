# Visibility report

- Thư mục nhãn: `dataset\labels\train`
- 20 ảnh, 28 skeleton, trung bình 16.32 khớp có v > 0 mỗi người
- Tổng: v=2 315 | v=1 142 | v=0 19

| # | Khớp | v=2 | v=1 | v=0 | %v=1 |
| ---: | --- | ---: | ---: | ---: | ---: |
| 0 | nose | 22 | 6 | 0 | 21% |
| 1 | left_eye | 19 | 9 | 0 | 32% |
| 2 | right_eye | 20 | 8 | 0 | 29% |
| 3 | left_ear | 11 | 17 | 0 | 61% |
| 4 | right_ear | 17 | 11 | 0 | 39% |
| 5 | left_shoulder | 24 | 4 | 0 | 14% |
| 6 | right_shoulder | 26 | 2 | 0 | 7% |
| 7 | left_elbow | 21 | 7 | 0 | 25% |
| 8 | right_elbow | 20 | 8 | 0 | 29% |
| 9 | left_wrist | 20 | 8 | 0 | 29% |
| 10 | right_wrist | 19 | 9 | 0 | 32% |
| 11 | left_hip | 19 | 9 | 0 | 32% |
| 12 | right_hip | 14 | 14 | 0 | 50% |
| 13 | left_knee | 17 | 8 | 3 | 29% |
| 14 | right_knee | 17 | 9 | 2 | 32% |
| 15 | left_ankle | 16 | 5 | 7 | 18% |
| 16 | right_ankle | 13 | 8 | 7 | 29% |

## Đọc bảng này thế nào

1. Khớp nào có **%v=1 cao**: khớp hay bị che. Cổ tay và hông thường là hai vị trí cần xem lại guideline trước khi kết luận.
2. Khớp nào có **v=0 cao bất thường**: mọi người đang dùng Outside ở chỗ đáng lẽ là Occluded. Đó là lỗi số 3 của slide 46, và nó xoá thẳng khớp đó khỏi bảng điểm OKS.
3. Khi so hai người: **lệch lớn = bất đồng về guideline**, không phải về bức ảnh. Sửa guideline trước, sửa nhãn sau.
