# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602329
- Ngày / CVAT local: 17/09/2026
- Công cụ đã dùng: CVAT local

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Người phụ nữ mặc áo dài trắng đang đi bộ qua đường ở giữa ảnh (PERSON 6).
- Class và quy tắc tôi dùng để chọn biên: Lớp `person`. Tôi dùng Polygon vẽ sát mép phần cơ thể và tà áo nhìn thấy, không tự đoán phần chân bị bóng che mờ, cẩn thận không ăn lấn sang người đàn ông đi xe máy ở phía sau.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: Không dùng gợi ý. Hoàn toàn tự chấm Polygon bằng tay.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình: Không dùng gợi ý. Vẽ sát mép tà áo vì đây là phần thân thuộc về đối tượng người này.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: hard_panoptic (hoặc easy_semantic), vùng cần cẩu trên nóc tòa nhà đang xây phía bên phải.
- Lỗi thuộc loại: sai lớp / biên.
- Bằng chứng tôi nhìn thấy: Đường viền màu xanh dương của lớp `sky` (bầu trời) nằm luồn xuống dưới cần cẩu, khiến toàn bộ cần cẩu bị gán nhầm thành bầu trời.
- Quy tắc và hành động sửa: Cần cẩu gắn liền với công trình nên thuộc về `building`. Dùng Polygon kéo lại đường biên của `building` bọc lấy cần cẩu, và thu hẹp mask `sky` lại.
- Sau sửa đã Save và export lại chưa? Đã Save và export lại file ZIP mới.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): Chưa có điểm.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1. Dải phân cách giữa đường | Gờ bê tông bao quanh mảng cỏ (`vegetation`) là `road` hay `sidewalk`? | Bó vỉa nhô cao, phân định chức năng rõ ràng với lòng đường xe chạy. | Quyết định gán là `sidewalk` vì nó có tính chất của gờ bó vỉa/lề cách ly. |
| 2. Cần cẩu trên nóc nhà | Khung thép mảnh nhìn xuyên thấu: bao trọn vào `building` hay đục lỗ vùng trống thành `sky`? | Vẽ bám theo viền ngoài của vật thể, không tự khoét lỗ nếu lỗ quá nhỏ. | Gán trọn vào `building` để mask không bị nát vỡ vụn. Xin coach xác nhận quy tắc với khung thép rỗng. |
| 3. Cột đèn ngang qua đường | Cột siêu mảnh vắt ngang trời: vẽ tách riêng hay bỏ qua do quá nhỏ? | Quy tắc vẽ mọi phần nhìn thấy rõ. | Dùng Polygon vẽ nét mảnh. Lưỡng lự ranh giới giao nhau giữa cột ngang và nền tòa nhà phía sau. |
