# Báo cáo cá nhân LAB5 — Phạm Trấn Quốc

| Thông tin | Nội dung |
|---|---|
| Họ và tên | Phạm Trấn Quốc |
| Mã học viên | 2A202604113 |
| Lớp, nhóm | K5-L3B, Nhóm GODZILLA |
| Track | T3 Du lịch — trợ lý đổi chuyến khi chuyến bay bị huỷ |
| Bài chung | [spec.md](../spec.md) |
| Sản phẩm | [Prototype HTML](../prototype/index.html), [ảnh ca đổi chuyến](../prototype/01-clarify.png), [ảnh ca hoàn đã gửi](../prototype/02-refund.png) |

## 1. Phần việc tôi thực hiện

Tôi chuẩn bị bản bài chung của Lab 5 từ lát cắt T3. Tôi phân tích dữ liệu đặt chỗ và năm tool được phát, xác định phạm vi tính năng, viết 11 kịch bản rủi ro, chọn hai ca có hậu quả nặng nhất, thiết kế lời AI và đường xử lý khi sai, đề xuất mức tự chủ cho từng tool, dựng prototype HTML và viết ba tiêu chí Pass/Fail. Tôi đối chiếu các quyết định với [đề track T3](https://github.com/VinUni-AI20k/K5-L3-Day05-AI-Product-UX-Autonomy/blob/7c1f24793008599ac3b77237d5c0c4eb2a89ad36/tracks/t3-travel.md) và [rubric](https://github.com/VinUni-AI20k/K5-L3-Day05-AI-Product-UX-Autonomy/blob/7c1f24793008599ac3b77237d5c0c4eb2a89ad36/04-rubric.md), rồi kiểm tra luồng bấm của prototype.

Theo phân công trình bày, tôi giới thiệu lát cắt, phân tích rủi ro và tiêu chí đánh giá. Tôi đã chuẩn bị các phần UX, mức tự chủ và prototype trong bài chung để nhóm rà soát và trình bày. Báo cáo này mô tả phần tôi trực tiếp xây dựng. Hoàng Minh phụ trách trình bày UX và mức tự chủ; Nguyễn Anh Tú phụ trách thao tác prototype và bằng chứng kiểm tra.

| Hạng mục | Kết quả đã bàn giao | Nơi đối chiếu |
|---|---|---|
| Lát cắt và phạm vi | Giữ đúng người dùng, công việc, quyết định AI và kết quả của track; nêu ba việc ngoài phạm vi | [spec.md §1](../spec.md) |
| Rủi ro | 11 kịch bản phủ bốn lớp, gắn tool hoặc dữ liệu, chọn S1 và S2 | [spec.md §2](../spec.md) |
| UX khi sai | Lời AI nguyên văn, nội dung trên màn hình, bước tiếp theo và đường chuyển người | [spec.md §3](../spec.md) |
| Mức tự chủ | Chính sách cho năm tool và phép thử trên S1, S2, S3 | [spec.md §4](../spec.md) |
| Prototype | Chọn chuyến, giữ chỗ, xác nhận, hết hạn, báo đổi nhầm, chuyển nhân viên | [prototype/index.html](../prototype/index.html) |
| Đánh giá | Ba tiêu chí Pass/Fail và kết quả tự chấm hai ca khó | [spec.md §6](../spec.md) |

## 2. Cách tôi hiểu bài toán

Lát cắt của đề là một hành khách vừa nhận tin chuyến bay bị huỷ, mở **Đặt chỗ của tôi** và nhắn hỏi. AI cần quyết định nên đề xuất chuyến, giữ chỗ, hỏi thêm, đổi vé sau khi được duyệt hay chuyển nhân viên. Kết quả mong muốn là khách tới nơi kịp mà không mất vé hoặc tiền vì thao tác khó đảo. Tôi giữ phạm vi này trong cả bài. Đổi tên người bay, xử lý trẻ bay một mình và hứa bồi thường tiền mặt được đưa ra ngoài phạm vi vì không có tool hoặc căn cứ chính sách phù hợp.

Tôi dùng fixture của T3 làm nguồn sự thật. Đặt chỗ TRV-7Q2K có Nguyễn Minh An, 34 tuổi, và Nguyễn Gia Bình, 5 tuổi. BM 213 Hà Nội → TP.HCM lúc 19:00 ngày 12/11/2026 đã huỷ do bão. BM 217 lúc 21:00 chỉ còn **một chỗ**; BM 201 lúc 07:00 và BM 205 lúc 09:30 ngày hôm sau còn **9** và **4 chỗ**. Khách được đổi miễn phí một lần trong 48 giờ hoặc hoàn toàn bộ. Huỷ do thời tiết không có bồi thường tiền mặt theo chính sách hãng dựng. Các dữ kiện này quyết định lời AI được nói và nút nào được hiện. [Nguồn fixture T3](https://github.com/VinUni-AI20k/K5-L3-Day05-AI-Product-UX-Autonomy/blob/7c1f24793008599ac3b77237d5c0c4eb2a89ad36/tracks/t3-travel.md)

Tôi phân biệt cái giá của hai hướng sai. Nếu AI **đổi vé quá sớm**, khách có thể mất lần đổi miễn phí và lỡ chuyến phù hợp. Nếu AI **chờ nhân viên cho mọi thao tác**, chỗ trống có thể hết trong lúc chờ. Vì vậy, thiết kế tách bước có thể đảo là **giữ chỗ 20 phút** khỏi bước khó đảo là **đổi vé**. Bước đổi chỉ mở sau khi khách xác nhận mã chuyến và hai hành khách.

## 3. Cách tôi xây dựng kịch bản rủi ro

Tôi bắt đầu từ ba tin mồi và mục Hard tests của track, rồi viết thành những câu chat ngắn giống hoàn cảnh khách đang vội. Mỗi dòng S1–S11 ghi câu khách nói, lỗi AI có thể mắc, tool hoặc dòng fixture liên quan, cách sản phẩm nên xử lý và mức hại. Tôi tự kiểm độ phủ theo bốn lớp như sau.

| Lớp | Kịch bản tôi đưa vào | Lý do cần kiểm tra |
|---|---|---|
| ① Nguồn sự thật | S3 hỏi giờ bay, S4 chọn BM 217, S7 hỏi bồi thường | AI phải đọc cả trạng thái, số chỗ và lý do huỷ. Chỉ đọc giờ 19:00 mà bỏ trạng thái **đã huỷ** sẽ làm khách hiểu sai. |
| ② Mơ hồ hoặc thiếu thông tin | S1 “đổi đi”, S5 “sáng mai”, S6 “huỷ hết” | Có hai chuyến sáng hôm sau và hai hành khách. Một câu đồng ý chung chưa xác định đủ hành động khó đảo. |
| ③ Ngoài phạm vi hoặc thẩm quyền | S2 đòi rút hoàn đã gửi, S8 đổi tên, S10 tự xưng nhân viên hãng | Không có tool rút hoàn hoặc đổi tên. Lời tự xưng trong chat không tạo quyền bỏ qua xác nhận. |
| ④ Rủi ro đặc thù du lịch | S4 một chỗ cho hai người, S9 trẻ bay một mình, S11 báo đổi nhầm | Chỗ trống, điều kiện bay của trẻ và lần đổi miễn phí ảnh hưởng trực tiếp đến khả năng đi chuyến khác. |

Tôi chọn **S1** và **S2** vì chúng nằm ở hai thời điểm quanh một quyết định khó đảo. S1 xảy ra **trước** khi đổi, nên một bước hỏi và xác nhận có thể ngăn mất lần đổi miễn phí. S2 xảy ra **sau** khi yêu cầu hoàn đã gửi, nên trải nghiệm cần dừng lời hứa sai và mở đường hỗ trợ thực tế. S4 suýt được chọn vì BM 217 chỉ có một chỗ cho hai người. Tuy nhiên, điều kiện “số chỗ phải đủ số hành khách” có thể chặn S4 trực tiếp. S1 khó hơn vì cả BM 201 và BM 205 đều đủ chỗ mà AI vẫn không biết khách muốn chuyến nào. Lập luận này được ghi trong [spec.md §2](../spec.md).

## 4. Quyết định UX cho hai ca khó nhất

### S1 — “Ừ đổi đi, hai mẹ con nhé”

Tôi xem câu này là **xác nhận mơ hồ** vì khách nói rõ hai người nhưng chưa chọn BM 201 lúc 07:00 hay BM 205 lúc 09:30. AI hỏi đúng một việc còn thiếu bằng hai thẻ có mã chuyến, giờ và số chỗ. Lời AI nói rõ “mình chưa biết bạn muốn chuyến nào” và giải thích trình tự **chọn chuyến → giữ 20 phút → kiểm tra → xác nhận đổi**. Nhãn “Chưa xác định chuyến” ở **[1]** cho biết vì sao chưa có nút đổi. Căn cứ ở **[2]** cho biết BM 217 chỉ còn một chỗ, không phù hợp với hai người. [Ảnh S1](../prototype/01-clarify.png)

Sau khi khách chọn chuyến đủ chỗ, màn hình giữ chỗ hiện mã chuyến, ngày giờ, hai hành khách và cảnh báo sẽ dùng lần đổi miễn phí duy nhất nếu xác nhận. Tôi thêm nút **Đổi lựa chọn**, **Huỷ giữ chỗ** và **Chuyển nhân viên** trước điểm xác nhận. Bộ đếm 20 phút làm rõ thời hạn giữ. Nếu hết hạn, nút xác nhận biến mất và khách phải chọn lại. Các nút ở **[3]** cho khách sửa ngay khi chọn nhầm, trước khi dùng lần đổi miễn phí (G9).

Tôi cân nhắc cho AI tự chọn chuyến để nhanh hơn, nhưng cách đó có thể dùng sai lần đổi miễn phí. Chuyển nhân viên ngay có thể làm lỡ chỗ phù hợp. Hỏi lại bằng hai lựa chọn cụ thể xử lý đúng thông tin còn thiếu, sau đó cho giữ chỗ tạm mà chưa đổi vé. Nếu AI coi “đổi đi” là đồng ý với một chuyến cụ thể, đó là **lỗi ngữ cảnh của thiết kế**. Lời xin lỗi sau khi đổi nhầm không trả lại lần đổi miễn phí; cách cứu là khóa `doi_chuyen_bay` đến khi có xác nhận rõ ràng.

### S2 — “Tôi bấm gửi hoàn rồi, huỷ hoàn đi để đổi chuyến”

Tool `gui_yeu_cau_hoan_ve` **không đảo được** theo đề. Tôi không đặt nút “Huỷ hoàn” hoặc “Đổi vé” trong trạng thái này. Trợ lý nói rằng yêu cầu đã gửi, không thể huỷ sau khi gửi và chưa thể bảo đảm vé còn đổi được. **[4]** cho thấy trạng thái, hậu quả và nút chuyển nhân viên. Khi khách bấm chuyển, prototype hiện phiếu hỗ trợ mô phỏng với mã đặt chỗ, trạng thái hoàn và nội dung cần kiểm tra. Tôi không hứa thời gian phản hồi của nhân viên vì fixture không cung cấp. [Ảnh S2](../prototype/02-refund.png)

Tôi cân nhắc hỏi lại để thử huỷ hoàn, nhưng không có tool cho thao tác đó. Tôi loại lời hứa “vé vẫn đổi được” vì không có dữ liệu trạng thái xử lý. Trong S2 gốc, chưa có bằng chứng AI đã tư vấn sai. Chỉ biến thể AI từng nói yêu cầu hoàn có thể rút mới là **lỗi hệ thống** và cần nhận lỗi rõ ràng. Sửa câu chữ chỉ giải quyết lời thông báo; sản phẩm còn phải khóa các hành động vượt quyền và chuyển ca cùng ngữ cảnh cho nhân viên.

## 5. Lập luận mức tự chủ theo cái giá khi sai

Với từng tool, tôi đặt ba câu hỏi. **Ai chịu thiệt nếu AI làm sai? Có đảo lại được không? Chờ người duyệt có làm khách mất gì không?** Bảng đầy đủ cùng phương án đã loại nằm trong [spec.md §4](../spec.md).

| Tool | Mức đề xuất | Lý do và điều kiện |
|---|---|---|
| `tra_cuu_dat_cho` | Tự làm | Chỉ đọc đặt chỗ khách đã mở. Chờ nhân viên để biết trạng thái và chỗ trống có thể làm khách lỡ chuyến. UI phải hiện cả giờ gốc và trạng thái **đã huỷ**. |
| `giu_cho_chuyen_moi` | Tự làm có điều kiện | Khách đã chọn mã chuyến và chuyến đủ chỗ cho hai người. Giữ tối đa 20 phút rồi tự nhả; khách có thể huỷ. |
| `doi_chuyen_bay` | Cần khách duyệt | Dùng lần đổi miễn phí duy nhất và khó đảo. Màn hình duyệt hiện chuyến, thời gian, hai hành khách và hậu quả. Giữ chỗ hết hạn thì không được đổi. |
| `gui_yeu_cau_hoan_ve` | Cần khách xác nhận và nhân viên kiểm tra | Gửi rồi không rút được. Fixture thiếu số tiền và phương thức nhận, nên AI chưa đủ căn cứ để tự gửi hoặc tạo màn hình xác nhận đầy đủ. |
| `chuyen_nhan_vien` | Tự làm | Chuyển thừa tốn thời gian xử lý; không chuyển ca vượt quyền AI có thể gây thiệt hại lớn hơn. |

Tool khó xếp nhất đối với tôi là **`giu_cho_chuyen_moi`**. Tự giữ ngay khi nghe “đổi đi” có thể chiếm sai chỗ. Luôn chờ nhân viên có thể làm BM 201 hoặc BM 205 hết chỗ. Tôi chọn ranh giới ở **lựa chọn mã chuyến cụ thể của khách**. Với S1, AI chưa giữ khi khách chưa chọn. Với S4, BM 217 không đủ chỗ nên không hiện như lựa chọn bấm được. Bảng năm tool cùng các phương án cho tool khó nhất đã được tổng hợp trong bài chung để Minh giải thích quyết định và Tú chỉ hành vi tương ứng trên prototype.

Tôi thử chính sách trên S1, S2 và S3 bình thường. S1 không gọi đổi vé trước khi khách duyệt. S2 không tạo thêm yêu cầu hoàn hoặc đổi vé, chỉ mở đường chuyển người. S3 đọc đặt chỗ để trả lời ngay rằng chuyến gốc 19:00 đã huỷ. Như vậy, lời hứa với khách được diễn đạt chính xác hơn: **trợ lý có thể giữ chỗ sau khi khách chọn; đổi vé chỉ diễn ra sau khi khách duyệt bản tóm tắt**.

## 6. Tôi chuyển lập luận thành prototype như thế nào

Tôi viết prototype bằng HTML, CSS và JavaScript trong một file để mở trực tiếp bằng trình duyệt. Cột trái chứa lời AI, lựa chọn chuyến và nút hành động. Cột phải giữ thông tin đặt chỗ, trạng thái huỷ, hành khách, quyền đổi và số chỗ. Khách có thể nhìn căn cứ ngay lúc quyết định. Tôi không dùng tỷ lệ kiểu “AI tự tin 92%” vì fixture không có cơ sở để tính tỷ lệ đó. Mã chuyến, số chỗ và trạng thái là bằng chứng khách có thể tự kiểm.

Luồng S1 đi từ hỏi lại đến chọn chuyến, giữ chỗ, xác nhận hoặc sửa. Nhánh hết hạn khóa xác nhận và yêu cầu chọn lại. Nhánh báo đổi nhầm chuyển nhân viên. Tab S2 mở trạng thái yêu cầu hoàn đã gửi, không tạo thao tác rút hoàn giả. Giao diện ghi rõ **Mô phỏng** và chỉ dùng dữ liệu dựng. Ba nguyên tắc được chỉ trực tiếp là **G10 ở [1]** để hỏi khi chưa chắc, **G11 ở [2]** để giải thích căn cứ, và **G9 ở [3]** để sửa trước khi xác nhận. Vị trí [4] là đường hỗ trợ khi không thể huỷ yêu cầu hoàn. [Mở prototype](../prototype/index.html)

## 7. Kiểm tra và giới hạn

Tôi đặt ba tiêu chí có thể chấm bằng hành vi trên giao diện trong [spec.md §6](../spec.md). **P1** kiểm tra nút xác nhận chỉ xuất hiện khi giữ đúng chuyến và còn hiệu lực; ca hoàn đã gửi không có nút đổi hoặc gửi lại. **P2** đối chiếu mã chuyến, giờ và số chỗ với fixture, đồng thời kiểm tra ca hoàn đã gửi không đưa ra lựa chọn chuyến. **P3** kiểm tra cảnh báo trước bước duyệt và nội dung phiếu khi chuyển nhân viên. Tôi tách kết quả mô phỏng khỏi yêu cầu cần kiểm chứng với hệ thống vé thật.

Bản mẫu được kiểm tra bằng Chrome. Bảng dưới ghi các trạng thái quan sát được và cách tái hiện trong [prototype](../prototype/index.html).

| Kiểm tra | Thao tác | Kết quả quan sát được |
|---|---|---|
| P1 · Chọn, huỷ và hết hạn | Bấm BM 201, huỷ giữ. Chọn BM 205 rồi bấm giả lập hết hạn. | Nút xác nhận biến mất ở cả hai nhánh. Muốn đổi phải chọn lại. |
| P2 · Dữ liệu và số chỗ | Kiểm tra hai thẻ chuyến và bảng căn cứ. Chuyển sang ca hoàn đã gửi. | BM 201 và BM 205 có đúng giờ và số chỗ. BM 217 chỉ hiện làm căn cứ. Ca hoàn không có lựa chọn chuyến. |
| P3 · Chuyển nhân viên trước khi đổi | Giữ BM 201 rồi bấm “Chuyển nhân viên” tại màn hình duyệt. | Trước khi bấm có cảnh báo lần đổi miễn phí. Phiếu giữ lại mã chuyến liên quan, lượt giữ tạm kết thúc và chưa phát sinh đổi. |
| P3 · Phục hồi sau thao tác khó đảo | Xác nhận đổi rồi bấm “Báo đổi nhầm”. Ở ca S2, bấm “Chuyển nhân viên”. | S1 có đường hỗ trợ mà không cam kết khôi phục lần đổi. S2 có phiếu ghi TRV-7Q2K và trạng thái hoàn đã gửi. |

Số chỗ và trạng thái hoàn trong prototype là dữ liệu cố định. Một sản phẩm thật phải tra lại chỗ ở thời điểm khách bấm xác nhận và xử lý trường hợp chỗ vừa hết. Fixture thiếu số tiền và phương thức nhận hoàn, nên tôi không dựng luồng gửi hoàn mới như thể đã đủ căn cứ. Prototype không có lời gọi AI thật hoặc API key. Ca lạ do TA hoặc giảng viên đưa ra sẽ được ghi vào bài chung sau demo thực tế.

### Các điểm sửa sau vòng review

Ở bản trước, sau khi xác nhận đổi, cột quyền lợi vẫn hiện “đổi miễn phí 1 lần”. Phiếu chuyển nhân viên cũng giống nhau giữa lúc chưa đổi và lúc báo đổi nhầm. Bản cập nhật lưu riêng chuyến đã xác nhận, cập nhật quyền lợi ngay sau đổi và giữ trạng thái đó khi chuyển nhân viên. Phiếu báo đổi nhầm nêu chuyến cũ, chuyến mới, hai hành khách và lần miễn phí đã dùng; phiếu trước đổi ghi rõ chưa phát sinh đổi vé.

Kiểm tra lại bằng hai đường bấm cùng chọn BM 201 nhưng chuyển hỗ trợ ở hai thời điểm khác nhau cho thấy phiếu đã phân biệt đúng. Lỗi này cho thấy chỉ kiểm tra “có nút chuyển người” chưa đủ: P3 cần kiểm tra cả thông tin người tiếp nhận nhìn thấy. P2 cũng được bổ sung điều kiện quyền lợi sau đổi. Bảng HAX được sửa định dạng; S3 và S8 được nâng mức hại vì thông tin sai có thể khiến khách lỡ chuyến hoặc bị từ chối vận chuyển.

Việc soạn và chỉnh prototype có hỗ trợ của công cụ AI. Các kết quả mô phỏng được đối chiếu với dữ liệu của đề; không coi đó là kết quả vận hành với hãng bay thật. Nội dung theo phân công cho Minh và Tú đã được chuẩn bị trong bài chung và tài liệu trình bày tương ứng.

## 8. Điều tôi rút ra

Một câu trả lời nghe hợp lý vẫn có thể dẫn đến hành động sai nếu hệ thống không kiểm tra ý định và quyền thực hiện. Với “đổi đi”, **đúng mã chuyến và đúng hai hành khách** quan trọng hơn việc AI đoán nhanh. Giữ chỗ là thao tác tạm thời có thể tự nhả nên được phép sau khi khách chọn; đổi vé dùng một quyền lợi chỉ có một lần nên cần duyệt rõ. Tôi dùng cùng tiêu chí hậu quả để đặt hai hành động vào hai mức tự chủ khác nhau.

Khi dựng màn hình, tôi phát hiện chỗ `spec.md` nói “chuyển nhân viên” cần có nút bấm thực tế. Bản hiện tại có đường chuyển ở bước hỏi lại, bước giữ chỗ, bước hết hạn và ca hoàn đã gửi. Đây là bằng chứng tôi có thể chỉ trực tiếp khi giải thích quyết định thiết kế cho người chấm.
