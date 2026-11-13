# K5-L3B-DAY05-T3-GODZILLA

**LAB5 · T3 Du lịch · Nhóm GODZILLA · Lớp L3B**

Bài thiết kế và prototype cho tính năng **Đặt chỗ của tôi** khi chuyến bay bị huỷ. Trợ lý giúp hành khách chọn chuyến còn đủ chỗ, giữ tạm và xem lại thông tin trước khi quyết định đổi vé. Nếu yêu cầu hoàn đã gửi, trợ lý giải thích giới hạn và chuyển nhân viên kiểm tra.

## Mở bài và chạy demo

- [Bài thiết kế và phân công](spec.md)
- [Prototype bấm được](prototype/index.html)
- [Ảnh S1: hỏi lại và giữ chỗ trước duyệt](prototype/01-clarify.png)
- [Ảnh ca hoàn đã gửi](prototype/02-refund.png)
- [Báo cáo và tài liệu theo phân công](individual/)

1. Mở `prototype/index.html` trực tiếp bằng trình duyệt. Ca mặc định là **S1**: khách đã nói “Ừ đổi đi, hai mẹ con nhé” nhưng chưa chọn chuyến cụ thể.
2. Bấm **Chọn và giữ BM 201**. Kiểm tra mã chuyến, hai hành khách, bộ đếm 20 phút và cảnh báo về lần đổi miễn phí. Thử **Chọn chuyến khác (nhả chỗ đang giữ)** hoặc **Huỷ giữ chỗ, chưa đổi vé**. Nút **Giả lập hết 20 phút giữ chỗ** cho thấy quyền xác nhận biến mất.
3. Chọn lại chuyến rồi bấm **Xác nhận đổi vé sang BM 201 cho cả hai**. Bấm **Báo đổi nhầm BM 201 cho nhân viên** để xem phiếu ghi chuyến đã đổi và lần miễn phí đã dùng. Cột quyền lợi cũng được cập nhật.
4. Bấm **S2 · Hoàn đã gửi**. Bước đầu cho biết yêu cầu hoàn **đã gửi lúc 15:10**; đây không phải nút gửi hoàn mới. Bấm **Mô phỏng khách hỏi: huỷ hoàn để đổi chuyến** để xem nguyên văn tin khách, lời AI và các hành động bị chặn. Sau đó bấm **Chuyển nhân viên kiểm tra yêu cầu hoàn** để xem phiếu có mã đặt chỗ, hai hành khách, trạng thái hoàn và nội dung cần xác minh.

**Thử thêm trong cùng giao diện:** dùng mục **Tình huống demo** để chọn S3–S11. S4 cho thấy nút **Không thể giữ BM 217** bị khoá vì chỉ còn một chỗ. Sau khi giữ BM 201, bấm **Giả lập BM 201 vừa hết chỗ** để xem trợ lý huỷ xác nhận cũ và yêu cầu chọn lại. S6/S8/S9 có nút chuyển nhân viên nêu rõ lý do; S10 không bỏ qua xác nhận; S11 có nút báo đổi nhầm BM 205. Các nhánh dùng dữ liệu và lời thoại dựng sẵn, không nhận câu hỏi tự do.

Prototype chạy bằng HTML, CSS và JavaScript, với dữ liệu dựng của track T3. Giữ chỗ, đổi vé và tạo phiếu hỗ trợ đều là mô phỏng. Có thể mở file trực tiếp, không cần tài khoản, máy chủ hay API key.

## Đọc bằng chứng trong spec

| Mục | Bằng chứng |
|---|---|
| **R1–R2 · §1–§2** | Lát cắt, ba việc ngoài phạm vi, 11 kịch bản phủ bốn lớp và lý do chọn S1, S2. |
| **R3–R4 · §3–§4** | Lời trợ lý, cách xử lý hai ca khó, nguyên tắc HAX, quyền của năm tool và phép thử trên S1, S2, S3. |
| **R5–R6 · §5–§6** | Hai ảnh đánh số, quyết định hiển thị, ba tiêu chí Pass/Fail và kết quả tự kiểm trên S1, S2. |
| **R7 · §7** | Kết quả xử lý ca lạ và quyết định sau demo. Lịch trình và ca luyện nằm trong README này. |

## Phân công và nội dung đã hoàn thành

Bài chung đã có đầy đủ phần thiết kế, mức tự chủ, prototype, ảnh và kết quả kiểm tra, bao gồm cả các hạng mục phân công cho Quang Anh và Tú. Phần triển khai bản chung do Phạm Trấn Quốc đảm nhiệm; phân công dưới đây xác định phần từng người phụ trách trình bày.

| Họ và Tên | Mã Học Viên | Phần việc theo phân công và kết quả trong bài chung |
|---|---|---|
| Phạm Trấn Quốc | 2A202604113 | Phân tích lát cắt và 11 kịch bản, xây dựng phương án UX và mức tự chủ, dựng prototype và tự kiểm theo ba tiêu chí Pass/Fail. |
| Nguyễn Quốc Quang Anh | 2A202604120 | Phụ trách UX và mức tự chủ (§3–§4): lời thoại S1/S2, phân loại lỗi, HAX, chính sách năm tool và lập luận giữ chỗ/đổi vé/chuyển người. Nội dung đã hoàn thành trong bài chung; trình bày phần quyết định thiết kế khi demo. |
| Nguyễn Anh Tú | 2A202604088 | Phụ trách prototype và đánh giá (§5–§6): hai luồng S1/S2, ảnh đánh số HAX, ba tiêu chí P1–P3 và kết quả kiểm tra. Nội dung đã hoàn thành trong bài chung; thao tác prototype và chỉ bằng chứng khi demo. |

## Repo nộp bài

- **Repo:** [Quoosc/K5-L3B-DAY05-T3-GODZILLA](https://github.com/Quoosc/K5-L3B-DAY05-T3-GODZILLA).
- **Nội dung chính:** [spec.md](spec.md) và [prototype/](prototype/), gồm HTML chạy trực tiếp và hai ảnh đánh số.
- **Tài liệu bổ trợ:** README hướng dẫn chạy và luyện demo; [individual/](individual/) chứa báo cáo Quốc và nội dung trình bày theo phân công của Quang Anh, Tú.
- Repo được khởi tạo mới cho bài nộp; không sao chép tài liệu đề hoặc lịch sử Git của bản chuẩn bị.
- **Demo:** nhóm đã trình bày trên lớp. Với ca chung vừa muốn đổi chuyến vừa có yêu cầu hoàn đã gửi, nhóm chọn chuyển nhân viên vì vượt phạm vi xử lý của trợ lý; phần ghi nhận và căn cứ nằm ở [spec.md, mục §7](spec.md). Hướng dẫn bên dưới dùng để chạy lại và đối chiếu hành vi.
- **Hạn L3B theo đề:** 23:59 ngày 13/11/2026. Nộp link repo qua kênh giảng viên thông báo.

Yêu cầu nộp bài tham chiếu [README đề lab](https://github.com/VinUni-AI20k/K5-L3-Day05-AI-Product-UX-Autonomy/blob/7c1f24793008599ac3b77237d5c0c4eb2a89ad36/README.md) và [guide §7.3](https://github.com/VinUni-AI20k/K5-L3-Day05-AI-Product-UX-Autonomy/blob/7c1f24793008599ac3b77237d5c0c4eb2a89ad36/02-guide.md).

## Kiểm tra bản cuối và giới hạn

Prototype phân biệt phiếu chuyển trước đổi với phiếu báo đổi nhầm; quyền lợi và chuyến đã đổi được giữ nhất quán khi chuyển hỗ trợ. Ảnh S1 ghép hai trạng thái để thấy trực tiếp câu hỏi G10 và các nút sửa G9. Ảnh S2 thể hiện giới hạn thao tác hoàn đã gửi. Ba tiêu chí trong spec bao gồm kiểm tra thông tin sau đổi và nội dung bàn giao.

Các nút đổi ca, giả lập hết hạn và làm lại là điều khiển cho buổi demo, không phải quyền hoàn tác giao dịch thật. Mỗi ca dùng dữ liệu độc lập; làm lại khởi tạo phiên mô phỏng mới. Số chỗ dùng dữ liệu dựng; nút giả lập hết chỗ chỉ thay đổi dữ liệu trong phiên thử, không kết nối tồn chỗ thật. Chưa có backend, nhân viên thật hoặc lời gọi AI; không tính bonus AI. Nội dung kỹ thuật đã được chuẩn bị cho cả ba phần phân công. Phần ghi nhận demo đã có ở §7; link repo cần được nộp theo kênh giảng viên thông báo.

## Hướng dẫn luyện demo

Lịch trình tham khảo cho nhóm; không phải nội dung bắt buộc ghi trong spec.

| Thời gian dự kiến | Người trình bày | Việc nói hoặc bấm |
|---|---|---|
| 0:00–0:30 | Phạm Trấn Quốc | Giới thiệu lát cắt: chuyến gốc đã huỷ, hai hành khách cần đi cùng nhau, đổi nhầm làm mất lần đổi miễn phí duy nhất. Nêu S1 là câu xác nhận mơ hồ. |
| 0:30–1:45 | Nguyễn Anh Tú | Từ S1, chỉ [1] hỏi lại và [2] căn cứ số chỗ. Chọn BM 201, chỉ [3] và bấm huỷ hoặc giả lập hết hạn để thấy nút duyệt biến mất. Chọn lại và xác nhận để hoàn thành ca chính. |
| 1:45–2:45 | Nguyễn Quốc Quang Anh | Giải thích vì sao giữ được tự làm sau khi chọn, còn đổi phải chờ duyệt. Chuyển S2, chỉ [4] và nêu thông tin nhân viên nhận. |
| Thời gian còn lại | Cả nhóm | Nhận ca lạ, nêu điều kiện đã thay đổi, chỉ hành động được phép và bước người dùng thấy tiếp theo. Trình bày hoặc bấm nếu bản mẫu có nhánh phù hợp. |

**Ca luyện trước demo:** Nếu khách đã giữ BM 201 nhưng nhắn “đổi sang BM 205 luôn đi”, nhóm sẽ cho nhả BM 201, kiểm tra và giữ BM 205 sau khi khách chọn, rồi hiện lại màn hình xác nhận. Lời đồng ý trước đó không dùng lại cho BM 205. Nếu khách tự xưng là nhân viên và yêu cầu bỏ qua duyệt, nhóm giữ nguyên điều kiện xác nhận. Đây là ca luyện; phần ghi nhận ca lạ trên lớp nằm riêng ở spec §7.

**Ca luyện bổ sung:**

| Thay đổi đầu vào | Phản ứng cần giải thích |
|---|---|
| BM 201 vừa hết chỗ | Không tiếp tục đổi dựa trên số chỗ cũ; tra lại, nêu thay đổi và hỏi chọn BM 205 nếu còn đủ. Có thể bấm: chọn S4 → giữ BM 201 → **Giả lập BM 201 vừa hết chỗ** → chọn lại BM 205. Đây là thay đổi dữ liệu mô phỏng. |
| Khách chỉ muốn đổi cho bé Bình | Dừng đổi, không dùng xác nhận cho cả hai; chuyển nhân viên kiểm tra điều kiện trẻ bay một mình. |
| Khách báo đổi nhầm sau xác nhận | Bấm báo đổi nhầm; chỉ chuyến đã đổi và quyền lợi đã dùng trong phiếu, không hứa quay về BM 213 đã huỷ. |
| Khách yêu cầu huỷ hoàn qua nhân viên | Nhân viên chỉ kiểm tra tình trạng và phương án còn lại, không được hứa huỷ thao tác mà tool quy định không đảo được. |

**Khi nhiều điều kiện cùng xuất hiện:** nếu cùng một đặt chỗ vừa muốn đổi chuyến, vừa có yêu cầu hoàn đã gửi, áp dụng S2 trước. Trợ lý không mở bước giữ/đổi như S1; chuyển nhân viên kiểm tra trạng thái vé. Chọn tab S1 là mở ca mô phỏng độc lập, không phải cách bỏ qua trạng thái hoàn của S2.
