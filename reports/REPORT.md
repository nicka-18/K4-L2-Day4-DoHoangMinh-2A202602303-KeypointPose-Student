# Báo cáo Ngày 4 - Keypoint & Pose

Họ tên: `Đỗ Hoàng Minh`   Nhóm: ______   Ngày: `16/09/206`
> Cách dùng: copy file này thành `reports/REPORT.md`. Điền bằng số liệu do công cụ sinh ra;
> không tự ước lượng hoặc sửa số trong file JSON.

## 1. Nhãn của tôi

<!-- Lấy số từ reports/visibility_report.md hoặc outputs/visibility_report.json sau Chặng 4.
Số ảnh phải là 20; số skeleton là tổng số người trong 20 ảnh. Thời gian trung bình = tổng
thời gian gán / 20. -->

| Chỉ số | Giá trị |
| --- | ---: |
| Số ảnh đã gán |`20`|
| Số skeleton |`28`|
| v=2 / v=1 / v=0 | |
| Thời gian trung bình mỗi ảnh |`2`|

Ba khớp có `%v=1` cao nhất (chép từ `reports/visibility_report.md`):

1.
2.
3.

Chúng có đúng là những khớp bạn thấy khó gán nhất không? Nếu không, giải thích.

<!-- Trả lời 2–4 câu. Phân biệt “hay bị che” với “khó xác định vị trí giải phẫu”; nêu bằng
chứng nhìn thấy thay vì chỉ nêu cảm giác. -->

## 2. Chấm với gold

<!-- Lấy hai cột từ outputs/eval_vs_gold.json: một lần ngay khi protected release mở và một
lần sau rework. Đếm số phần tử trong từng danh sách lỗi, không tự làm tròn. -->

| Chỉ số | Trước rework | Sau rework |
| --- | ---: | ---: |
| OKS trung bình |`0.953`|
| OKS@0.50 |`0.966`|
| OKS@0.75 |`0.966`|
| Lỗi `dao_trai_phai` | | |
| Lỗi `nham_nguoi` | | |
| Lỗi `xoa_khop_bi_che` | | |

**Tôi đã sửa gì giữa hai lần chạy** (ghi cụ thể: ảnh nào, người thứ mấy, khớp nào):

<!-- Mỗi dòng phải có: tên ảnh + người thứ mấy + keypoint + thao tác sửa. Không viết “đã sửa
lại một số lỗi”. -->

-
-
-

**Lỗi đảo trái/phải của tôi xảy ra ở ảnh nào?** Ảnh đó dễ hay khó? Nếu là ảnh dễ,
bạn nghĩ vì sao mình vẫn sai?

<!-- Nếu không có lỗi, ghi rõ “Không có lỗi đảo trái/phải trong toàn bộ 20 ảnh.” -->

## 3. Kiểm chéo

Bạn cùng nhóm: ______

Khớp lệch `%v=1` nhiều nhất giữa hai bảng đếm:

| Khớp | Bạn | Họ | Lệch | Nguyên nhân (guideline hay gán sai?) |
| --- | ---: | ---: | ---: | --- |
| | | | | |
| | | | | |

Luật mới đã bổ sung vào `GUIDELINE_MINI.md` sau khi thống nhất:

<!-- Viết một rule kiểm chứng được: điều kiện nhìn thấy/căn cứ vị trí → chọn v=1 hoặc v=0.
Không chỉ ghi “cẩn thận hơn khi gán”. -->

-

## 4. Model

<!-- Chép số từ outputs/eval_model.json sau Chặng 6. “Chênh” = sau fine-tune trừ baseline;
đây là quan sát trên tập test, không phải chất lượng sản phẩm. -->

| Chỉ số | yolo26n-pose gốc | Sau fine-tune | Chênh |
| --- | ---: | ---: | ---: |
| pose_mAP50 |` 0.8450          0.8450   +0.0000`|
| pose_mAP50-95 |`0.6853        0.6908   +0.0055` |
| pose_precision | `0.9734          0.9792   +0.0058` |
| pose_recall | `0.8462          0.8462   +0.0000` |
| box_mAP50-95 | `0.8119          0.8041   -0.0078` |

### Trả lời năm câu hỏi ở cuối notebook

> Mỗi câu cần trỏ tới ảnh/chỉ số cụ thể. Một con số thấp không tự chứng minh nhãn sai;
> kiểm lại bằng bằng chứng thị giác và kết quả gold.

1. `pose_mAP50-95` thay đổi bao nhiêu? Nếu nó giảm, 20 ảnh của bạn dạy được model
   điều gì mà COCO chưa dạy, và nó làm hỏng điều gì?

   `Mức thay đổi: pose_mAP50-95 tăng +0.0055 (từ $0.6853$ lên $0.6908$).Giải thích: Do chỉ số này tăng chứ không giảm, điều này chứng tỏ quá trình fine-tune trên 20 ảnh của bạn đã giúp mô hình học và dự đoán vị trí các khớp chính xác hơn so với mô hình gốc.`

2. `box_mAP` và `pose_mAP` chênh nhau bao nhiêu? Model tìm *người* dễ hơn hay tìm
   *khớp* dễ hơn? Vì sao?
   `Mức chênh lệch (sau fine-tune):Ở mốc AP50: box_mAP50 ($0.9600$) cao hơn pose_mAP50 ($0.8450$) là 0.1150 (11.5%).Ở mốc AP50-95: box_mAP50_95 ($0.8041$) cao hơn pose_mAP50_95 ($0.6908$) là 0.1133 (11.33%).Kết luận: Model tìm người (box) dễ hơn tìm khớp (pose). Lý do là việc phát hiện tổng thể một vùng thân người ít bị ảnh hưởng bởi điểm che khuất hơn so with việc phải định vị chính xác vị trí của từng khớp nhỏ (như cổ tay, cổ chân).`

3. Một ảnh test model đoán sai - gọi tên lỗi theo bốn loại của slide 43
   (lệch nhẹ / đảo trái/phải / nhầm người / trượt hẳn):
    `-Ảnh bị lỗi điển hình: test_02.jpg (ảnh trắng đen có con chim trên cột và người tập thể dục)`
    `-test_02.jpg (Lỗi Dự đoán thừa / False Positive):`
    `Hiện tượng: Ở góc dưới bên trái của bức ảnh test_02.jpg, model nhận diện một vệt đen trên bờ tường thành một người (person 0.31) và vẽ các chấm keypoint màu cam/xanh ra khoảng trống.`

4. Ảnh nào có OKS thấp nhất giữa nhãn của bạn và model? Ai đúng, và bạn dựa vào đâu?
    `Ảnh có OKS thấp nhất: train_15.jpg (điểm OKS chỉ đạt 0.641).`
    `Bạn đúng (Nhãn người gán đúng chuẩn hơn):Căn cứ: Mô hình YOLO chỉ được fine-tune trên 20 ảnh nên vẫn bị giới hạn khả năng nhận diện các tư thế khó/khuất. Trong khi đó, nhãn của bạn được làm thủ công bằng mắt, tuân thủ đúng quy tắc giải phẫu cơ thể người (giơ tay trái tính theo cơ thể người chứ không tính theo góc nhìn ảnh) và đã được chấm với tập Gold đạt mức OKS trung bình rất cao là 0.953 (Xuất sắc).  Ngoài ra, ở các ảnh phức tạp đông người như train_03, train_10, train_13, model bị lỗi dự đoán thừa người (ví dụ train_03 model đoán 4 người trong khi thực tế bạn gán 2 người), dẫn đến điểm OKS bị kéo xuống thấp.`
5. Ảnh bạn gán tệ nhất có *cũng* là ảnh model đoán tệ nhất không? Nếu có, điều đó
   nói gì về bức ảnh đó?
  
   `Dữ liệu thực tế của bạn: Ảnh bạn gán tệ nhất so với Gold là train_13.jpg (OKS = 0.000 do bị "Thiếu hẳn một người" - người #1).Đối chiếu với Model ở Mục 6:Nếu Model cũng đoán tệ ảnh train_13.jpg: Điều này khẳng định train_13.jpg là một ảnh rất khó (ví dụ: người bị che khuất gần hết, góc chụp quá tối hoặc người quá nhỏ) khiến cả người làm nhãn lẫn mô hình AI đều dễ bỏ sót.  Nếu Model nhận diện được người #1 trong train_13.jpg: Điều này nói lên rằng ảnh không khó, nhưng bạn đã phạm lỗi chủ quan do làm sót người trong quá trình gán nhãn thủ công. `

## 5. Một rule evidence bạn đã dùng

Chọn một keypoint trong ảnh core mà bạn phải quyết định giữa `v=1` và `v=0`. Nêu ảnh, người,
khớp, bằng chứng nhìn thấy và lý do chọn trạng thái đó trong 3-5 câu.

<!-- Cấu trúc gợi ý: (1) train_XX + người thứ mấy + keypoint; (2) căn cứ thị giác như phần cơ
thể liền kề, trang phục hoặc vật che; (3) vì sao khớp còn trong khung (v=1) hay đã ra khỏi
khung (v=0). -->

-train_04.jpg, person 109, LEFT_EAR-RIGHT_EAR.
-Căn cứ vào phần mắt, mũi liền kề-->dự đoán phần tai có khả năng.
-Người còn trong ảnh. Vì: Khuôn mặt và vai còn trong ảnh.`
