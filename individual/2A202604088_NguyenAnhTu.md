# Báo cáo cá nhân — Nguyễn Anh Tú

- **Mã học viên:** 2A202604088
- **Lớp:** L3B
- **Nhóm:** Nhóm GODZILLA · T3 Du lịch

## Phần phụ trách theo phân công

Prototype và hai ảnh đã có. Đọc [spec.md §5–§6](../spec.md) và [hướng dẫn luyện demo](../README.md), rồi mở [prototype](../prototype/index.html) bằng trình duyệt để chạy lại theo thứ tự trình bày.

1. Ở **S1**, chỉ [1] hỏi lại vì khách chưa chọn chuyến và [2] BM 217 chỉ còn một chỗ. Chọn BM 201 rồi chỉ [3] giữ tạm, nút huỷ và nút xác nhận. Bấm **Huỷ giữ chỗ** hoặc **Giả lập hết hạn** để kiểm tra nút xác nhận biến mất. Chọn lại và xác nhận cho cả hai. [Ảnh S1](../prototype/01-clarify.png)
2. Mở **Ca khác: Hoàn đã gửi**. Chỉ [4] cảnh báo không thể huỷ yêu cầu hoàn đã gửi. Bấm **Chuyển nhân viên** và kiểm tra mã đặt chỗ cùng trạng thái hoàn trong phiếu. [Ảnh S2](../prototype/02-refund.png)
3. Trình bày kết quả **P1–P3** ở §6; chỉ quyền lợi sau đổi và sự khác nhau của phiếu chuyển trước/sau đổi để chứng minh prototype làm đúng chính sách năm tool.

**Ý chính để trình bày:** cho người xem thấy khác biệt giữa chọn chuyến, giữ chỗ tạm và xác nhận đổi. Nếu ca lạ nằm ngoài hai màn hình đã dựng, giải thích trợ lý được làm gì theo §4 và bước tiếp theo mà khách sẽ thấy.

Các kết quả bên dưới là kết quả kiểm tra của bản prototype hiện tại, kèm thao tác để tái hiện khi demo.

## Kết quả kiểm tra prototype

| Tiêu chí | Thao tác đã kiểm tra | Kết quả |
|---|---|---|
| **P1 · Chặn đổi khi chưa đủ điều kiện** | Mở S1, chọn BM 201 rồi huỷ. Chọn lại và thử hết hạn. | Không có nút xác nhận ở bước hỏi lại, sau khi huỷ và sau khi hết hạn. |
| **P2 · Căn cứ hiển thị** | So mã, giờ và số chỗ trên hai thẻ với fixture. Mở ca S2. | BM 201 có 9 chỗ, BM 205 có 4 chỗ. BM 217 chỉ xuất hiện trong căn cứ, không chọn được cho hai khách. S2 không hiện lựa chọn chuyến. Sau xác nhận đổi, quyền lợi ghi đã dùng lần miễn phí và hiện đúng chuyến đã đổi. |
| **P3 · Duyệt và phục hồi** | Chọn lại và xác nhận, sau đó thử báo đổi nhầm. Mở S2 và bấm chuyển nhân viên. | Trước khi đổi có cảnh báo lần miễn phí. Báo đổi nhầm mở phiếu ghi chuyến cũ, chuyến mới và lần miễn phí đã dùng; phiếu trước đổi ghi chưa đổi và đã nhả lượt giữ. Phiếu S2 giữ mã TRV-7Q2K và trạng thái hoàn đã gửi. |

**Lời thoại luyện demo:** “Ở [1], khách chưa nói rõ chuyến nào. [2] giải thích vì sao chỉ có hai lựa chọn đủ chỗ. Khi tôi chọn BM 201, [3] cho thấy chỗ đang được giữ và có thể huỷ. Tôi thử hết hạn để thấy nút đổi biến mất, rồi chọn lại và xác nhận cho cả hai. Sau khi xác nhận, quyền lợi ghi đã dùng lần miễn phí. Nếu đổi nhầm, tôi bấm chuyển nhân viên và chỉ thông tin chuyến đã đổi trong phiếu. Ở ca hoàn đã gửi, [4] cho biết yêu cầu không thể huỷ sau khi gửi.”

**Ca luyện:** Nếu khách muốn đổi sang BM 205 sau khi đã giữ BM 201, bấm **Đổi lựa chọn**, chọn BM 205 và kiểm tra màn hình duyệt ghi đúng chuyến mới. Khi thao tác đổi đã hoàn tất, dùng đường báo đổi nhầm để chuyển người. [Prototype](../prototype/index.html)

## Bằng chứng cho phần trình bày

Nội dung theo phân công của Nguyễn Anh Tú đã có trong bài chung, với lập luận, đường bấm và bằng chứng nêu ở trên. Tài liệu này tổng hợp phần được phân công để sử dụng khi demo; không ghi thay trải nghiệm hoặc ý kiến cá nhân chưa được cung cấp. Kết quả ca lạ được cập nhật chung tại §7 sau demo.
