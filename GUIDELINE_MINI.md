# Mini guideline - nhóm: ______  |  người gán: Đỗ Hoàng Minh  |  ngày: 16/09/2026

> Điền file này **trong lúc** gán nhãn, không phải sau khi xong. Mỗi lần bạn dừng lại
> hơn 10 giây để phân vân, đó là một dòng phải ghi vào đây.

## 1. Luật bắt buộc (đã thống nhất cả lớp - không sửa)

- Bộ 17 điểm COCO, đúng tên, đúng thứ tự. Lấy từ file `.SVG` chung.
- Mọi người trong ảnh đều có **đủ 17 điểm**. Điểm không dùng được thì gắn cờ, không xoá.
- Trái/phải tính theo **cơ thể người**, không theo bức ảnh.
- Bị che, còn trong khung -> `v = 1`, **vẫn đặt chấm** ở vị trí ước lượng.
- Ra ngoài mép ảnh -> `v = 0`, **không** đặt chấm.
- Không dùng `Hidden` (`h`) - nó không được lưu vào file.

## 2. Luật của nhóm bạn (phải điền)

| Tình huống | Luật nhóm bạn chọn | Vì sao |
| --- | --- | --- |
| Hông của người mặc quần áo dài | | |
| Tai bị tóc hoặc mũ bảo hiểm che một phần | | |
| Người bị cắt ở mép ảnh (chỉ thấy từ hông trở lên) | | |
| Cổ tay nằm sau tay lái / sau thân mình | | |
| Hai người chồng lên nhau | | |
| Người nhỏ đến mức nào thì không gán nữa | | |

Với mỗi luật, chèn **một ảnh mẫu** (screenshot từ CVAT) thay vì chỉ viết một câu.
Slide 12 nói rõ: khớp không có bề mặt nhìn thấy được thì phải có ảnh mẫu, không phải
một câu văn chung chung.

## 3. Ba ca mơ hồ đã gặp (bắt buộc, ghi ít nhất 3)

### Ca 1 - ảnh `train_02`, người thứ `person 37`, khớp `mắt, mũi`

- Mơ hồ ở chỗ nào: `Người quay hẳn mặt đi`
- Bạn quyết thế nào: `Đặt điểm ước lượng v=1`
- Vì sao: `Mặt chỉ bị che, chứ không mất trong khung hình`
- Nếu người khác quyết ngược lại thì model học sai cái gì: `Model sẽ học những người quay mặt đi là không có 5 bộ phận trên mặt`

### Ca 2 - ảnh `train_03`, người thứ `person 73`, khớp `tay`

- Mơ hồ ở chỗ nào: `Người đó đứng sau người khác, phần tay bị che đi`
- Bạn quyết thế nào: `Đặt điểm ước lượng v=1`
- Vì sao: `Tay người đó bị che đi, chứ không mất đi`
- Nếu người khác quyết ngược lại thì model học sai cái gì: `Model sẽ học những người đứng sau người khác là không có tay`

### Ca 3 - ảnh `train_04`, người thứ `person 109`, khớp `LEFT_EAR, RIGHT_EAR`

- Mơ hồ ở chỗ nào: `Người đó đội mũ bảo hiểm, phần tai bị che đi`
- Bạn quyết thế nào: `Đặt điểm ước lượng v=1`
- Vì sao: `Người đó đội mũ bảo hiểm nên tai được che lại, chứ không mất đi`
- Nếu người khác quyết ngược lại thì model học sai cái gì: `Model sẽ học những người đội mũ bảo hiểm là không có tai`

## 4. Sau khi so visibility report với bạn cùng nhóm

- Khớp lệch `%v=1` nhiều nhất: `______` (bạn `___%` / họ `___%`)
- Nguyên nhân là **guideline chưa rõ** hay **một trong hai bên gán sai**:
- Luật mới bổ sung vào mục 2 sau khi thống nhất:
