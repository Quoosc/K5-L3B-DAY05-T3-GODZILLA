# K5-L3B-DAY05-T3-GODZILLA

**LAB5 · T3 Du lịch · Nhóm GODZILLA · Lớp L3B**

Bài thiết kế và prototype cho tính năng **Đặt chỗ của tôi** khi chuyến bay bị huỷ. Trợ lý giúp hành khách chọn chuyến còn đủ chỗ, giữ tạm và xem lại thông tin trước khi quyết định đổi vé. Nếu yêu cầu hoàn đã gửi, trợ lý giải thích giới hạn và chuyển nhân viên kiểm tra.

## Mở bài và chạy demo

- [Bài thiết kế và phân công](spec.md)
- [Prototype bấm được](prototype/index.html)
- [Ảnh S1: hỏi lại và giữ chỗ trước duyệt](prototype/01-clarify.png)
- [Ảnh ca hoàn đã gửi](prototype/02-refund.png)
- [Tài liệu bổ trợ cho buổi luyện](individual/)

1. Mở `prototype/index.html` trực tiếp bằng trình duyệt. Ca mặc định là **S1**: khách đã nói “Ừ đổi đi, hai mẹ con nhé” nhưng chưa chọn chuyến cụ thể.
2. Chọn **BM 201**. Kiểm tra màn hình hiển thị đúng chuyến, hai hành khách, bộ đếm 20 phút và cảnh báo sẽ dùng lần đổi miễn phí duy nhất. Thử **Đổi lựa chọn** hoặc **Huỷ giữ chỗ**. Có thể bấm **Giả lập hết hạn** để kiểm tra không còn nút xác nhận.
3. Chọn lại chuyến rồi bấm **Xác nhận đổi cho cả hai**. Nếu bấm **Báo đổi nhầm · Chuyển nhân viên**, bản mẫu hiển thị phiếu ghi chuyến đã đổi và lần miễn phí đã dùng, không tự đổi lần nữa. Kiểm tra cột quyền lợi cũng đã cập nhật.
4. Mở **Ca khác: Hoàn đã gửi** để thử **S2**. Kiểm tra cảnh báo không thể huỷ yêu cầu hoàn đã gửi và bấm **Chuyển nhân viên** để thấy phiếu có mã đặt chỗ cùng trạng thái yêu cầu.

Prototype chạy bằng HTML, CSS và JavaScript, với dữ liệu dựng của track T3. Giữ chỗ, đổi vé và tạo phiếu hỗ trợ đều là mô phỏng. Có thể mở file trực tiếp, không cần tài khoản, máy chủ hay API key.

## Đọc bằng chứng trong spec

| Mục | Bằng chứng |
|---|---|
| **R1–R2 · §1–§2** | Lát cắt, ba việc ngoài phạm vi, 11 kịch bản phủ bốn lớp và lý do chọn S1, S2. |
| **R3–R4 · §3–§4** | Lời trợ lý, cách xử lý hai ca khó, nguyên tắc HAX, quyền của năm tool và phép thử trên S1, S2, S3. |
| **R5–R6 · §5–§6** | Hai ảnh đánh số, quyết định hiển thị, ba tiêu chí Pass/Fail và kết quả tự kiểm trên S1, S2. |
| **R7 · §7** | Kết quả xử lý ca lạ và quyết định sau demo. Lịch trình và ca luyện nằm trong README này. |

## Phân công và nội dung đã hoàn thành

Bài chung đã có đầy đủ phần thiết kế, mức tự chủ, prototype, ảnh và kết quả kiểm tra, bao gồm cả các hạng mục phân công cho Minh và Tú. Phần triển khai bản chung do Phạm Trấn Quốc đảm nhiệm; phân công dưới đây xác định phần từng người phụ trách trình bày.

| Thành viên | Phần phụ trách | Nội dung sẵn sàng cho demo |
|---|---|---|
| **Phạm Trấn Quốc** | Lát cắt, rủi ro và tổng hợp bài | 11 kịch bản, lý do chọn S1/S2, liên hệ hậu quả và tiêu chí đánh giá. [Báo cáo](individual/2A202604113_PhamTranQuoc.md) |
| **Hoàng Minh** | UX và mức tự chủ (§3–§4) | Lời thoại hai ca, nguyên tắc HAX, năm tool, các phương án giữ chỗ và lý do chọn. [Nội dung theo phân công](individual/2A202604103_HoangMinh.md) |
| **Nguyễn Anh Tú** | Prototype và kiểm tra (§5–§6) | Hai luồng bấm, ảnh đánh số, kết quả P1–P3, quyền lợi sau đổi và phiếu hỗ trợ. [Nội dung theo phân công](individual/2A202604088_NguyenAnhTu.md) |

## Repo nộp bài

- **Repo:** [Quoosc/K5-L3B-DAY05-T3-GODZILLA](https://github.com/Quoosc/K5-L3B-DAY05-T3-GODZILLA).
- **Nội dung chính:** [spec.md](spec.md) và [prototype/](prototype/), gồm HTML chạy trực tiếp và hai ảnh đánh số.
- **Tài liệu bổ trợ:** README hướng dẫn chạy và luyện demo; [individual/](individual/) chứa báo cáo Quốc và nội dung trình bày theo phân công của Minh, Tú.
- Repo được khởi tạo mới cho bài nộp; không sao chép tài liệu đề hoặc lịch sử Git của bản chuẩn bị.
- **Demo:** thực hiện theo hướng dẫn bên dưới; cập nhật ca lạ và cách xử lý vào §7 sau buổi trình bày. Kiểm tra bàn/zone và mã học viên trước khi nộp.
- **Hạn L3B theo đề:** 23:59 ngày 13/11/2026. Nộp link repo qua kênh giảng viên thông báo.

Yêu cầu nộp bài tham chiếu [README đề lab](https://github.com/VinUni-AI20k/K5-L3-Day05-AI-Product-UX-Autonomy/blob/7c1f24793008599ac3b77237d5c0c4eb2a89ad36/README.md) và [guide §7.3](https://github.com/VinUni-AI20k/K5-L3-Day05-AI-Product-UX-Autonomy/blob/7c1f24793008599ac3b77237d5c0c4eb2a89ad36/02-guide.md).

## Kiểm tra bản cuối và giới hạn

Prototype phân biệt phiếu chuyển trước đổi với phiếu báo đổi nhầm; quyền lợi và chuyến đã đổi được giữ nhất quán khi chuyển hỗ trợ. Ảnh S1 ghép hai trạng thái để thấy trực tiếp câu hỏi G10 và các nút sửa G9. Ảnh S2 thể hiện giới hạn thao tác hoàn đã gửi. Ba tiêu chí trong spec bao gồm kiểm tra thông tin sau đổi và nội dung bàn giao.

Các nút đổi ca, giả lập hết hạn và làm lại là điều khiển cho buổi demo, không phải quyền hoàn tác giao dịch thật. Mỗi ca dùng dữ liệu độc lập; làm lại khởi tạo phiên mô phỏng mới. Số chỗ cố định, chưa có backend, nhân viên thật hoặc lời gọi AI; không tính bonus AI. Nội dung kỹ thuật đã được chuẩn bị cho cả ba phần phân công. Kết quả demo và ca lạ sẽ cập nhật sau buổi trình bày; link repo được nộp theo kênh giảng viên thông báo.

## Hướng dẫn luyện demo

Lịch trình tham khảo cho nhóm; không phải nội dung bắt buộc ghi trong spec.

| Thời gian dự kiến | Người trình bày | Việc nói hoặc bấm |
|---|---|---|
| 0:00–0:30 | Phạm Trấn Quốc | Giới thiệu lát cắt: chuyến gốc đã huỷ, hai hành khách cần đi cùng nhau, đổi nhầm làm mất lần đổi miễn phí duy nhất. Nêu S1 là câu xác nhận mơ hồ. |
| 0:30–1:45 | Nguyễn Anh Tú | Từ S1, chỉ [1] hỏi lại và [2] căn cứ số chỗ. Chọn BM 201, chỉ [3] và bấm huỷ hoặc giả lập hết hạn để thấy nút duyệt biến mất. Chọn lại và xác nhận để hoàn thành ca chính. |
| 1:45–2:45 | Hoàng Minh | Giải thích vì sao giữ được tự làm sau khi chọn, còn đổi phải chờ duyệt. Chuyển S2, chỉ [4] và nêu thông tin nhân viên nhận. |
| Thời gian còn lại | Cả nhóm | Nhận ca lạ, nêu điều kiện đã thay đổi, chỉ hành động được phép và bước người dùng thấy tiếp theo. Trình bày hoặc bấm nếu bản mẫu có nhánh phù hợp. |

**Ca luyện trước demo:** Nếu khách đã giữ BM 201 nhưng nhắn “đổi sang BM 205 luôn đi”, nhóm sẽ cho nhả BM 201, kiểm tra và giữ BM 205 sau khi khách chọn, rồi hiện lại màn hình xác nhận. Lời đồng ý trước đó không dùng lại cho BM 205. Nếu khách tự xưng là nhân viên và yêu cầu bỏ qua duyệt, nhóm giữ nguyên điều kiện xác nhận. Đây là ca luyện; kết quả ca lạ thực tế ghi trong spec §7 sau demo.

**Ca luyện bổ sung:**

| Thay đổi đầu vào | Phản ứng cần giải thích |
|---|---|
| BM 201 vừa hết chỗ | Không tiếp tục đổi dựa trên số chỗ cũ; tra lại, nêu thay đổi và hỏi chọn BM 205 nếu còn đủ. Ca tồn chỗ động chỉ phân tích bằng lời. |
| Khách chỉ muốn đổi cho bé Bình | Dừng đổi, không dùng xác nhận cho cả hai; chuyển nhân viên kiểm tra điều kiện trẻ bay một mình. |
| Khách báo đổi nhầm sau xác nhận | Bấm báo đổi nhầm; chỉ chuyến đã đổi và quyền lợi đã dùng trong phiếu, không hứa quay về BM 213 đã huỷ. |
| Khách yêu cầu huỷ hoàn qua nhân viên | Nhân viên chỉ kiểm tra tình trạng và phương án còn lại, không được hứa huỷ thao tác mà tool quy định không đảo được. |
