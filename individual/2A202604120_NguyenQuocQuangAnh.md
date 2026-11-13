# Báo cáo cá nhân — Nguyễn Quốc Quang Anh

- **Mã học viên:** 2A202604120
- **Lớp:** L3B
- **Nhóm:** Nhóm GODZILLA · T3 Du lịch

## Phần phụ trách theo phân công

Phần **UX khi AI sai và mức tự chủ** đã có trong [spec.md §3–§4](../spec.md). Nội dung dưới đây tổng hợp kết quả đã hoàn thành trong bài chung và các luận điểm cho phần trình bày.

1. Đọc **S1**, câu “Ừ đổi đi, hai mẹ con nhé”. Xác định khách đã nói rõ hai hành khách nhưng chưa chọn BM 201 hay BM 205. Giải thích vì sao trợ lý hỏi một câu, chỉ giữ khi khách chọn và chỉ đổi sau khi khách duyệt.
2. Đọc **S2** và mở ca **Hoàn đã gửi**. Nêu rõ thao tác hoàn không huỷ được sau khi gửi. Bấm **Chuyển nhân viên** để kiểm tra phiếu chứa mã đặt chỗ và trạng thái hoàn. [Ảnh S2](../prototype/02-refund.png)
3. Giải thích bảng năm tool ở §4: giữ chỗ có điều kiện, đổi vé cần duyệt; chỉ S1/S4 để chứng minh vì sao không được tự giữ khi chưa đủ thông tin.

**Ý chính để trình bày:** giữ chỗ có thể nhả, còn đổi vé dùng lần miễn phí duy nhất. Vì vậy trợ lý giữ sau khi khách chọn rõ, còn khách duyệt riêng bước đổi. Ca hoàn đã gửi chuyển nhân viên vì prototype không có quyền rút hoàn.

Các kết quả bên dưới thuộc phần UX và mức tự chủ đã hoàn thành trong bài chung.

## Phân tích đã chuẩn bị cho phần trình bày

| Ca | Bằng chứng | Quyết định và lý do |
|---|---|---|
| **S1 · Khách nói “đổi đi”** | BM 201 và BM 205 đều đủ chỗ. BM 217 chỉ còn một chỗ cho hai khách. | Hỏi đúng mã chuyến, rồi giữ 20 phút sau khi khách chọn. Màn hình duyệt hiện cả hai hành khách và cảnh báo dùng lần đổi miễn phí. Nếu khách đổi lựa chọn, huỷ hoặc để hết hạn, xác nhận cũ hết hiệu lực. |
| **S2 · Hoàn đã gửi** | Yêu cầu hoàn đã gửi. Fixture không cho biết vé còn đổi được hay khoản hoàn sẽ về khi nào. | Nêu giới hạn ngay, chỉ cho chuyển nhân viên để xác minh. Phiếu kèm TRV-7Q2K và trạng thái hoàn. Không tạo yêu cầu hoàn mới. |

**Phương án năm tool trong bài chung:** tra cứu tự làm khi khách đã mở đặt chỗ; giữ chỗ tự làm sau khi chọn đúng và đủ chỗ; đổi vé cần khách duyệt; gửi hoàn mới cần nhân viên xác minh và khách xác nhận; chuyển nhân viên được phép khi khách chọn hỗ trợ hoặc ca vượt quyền. Đây là phương án trong bản chung. Với tool khó xếp nhất, giữ ngay có thể giữ nhầm, còn chờ nhân viên có thể làm mất chỗ phù hợp. Phương án hiện tại cân bằng hai hậu quả bằng một lượt giữ có điều kiện và có thể huỷ. [Bảng tool trong spec.md §4](../spec.md)

**Lời thoại luyện demo:** “Trong S1, cả hai chuyến đều đủ chỗ nên số chỗ không cho biết khách muốn chuyến nào. Sau khi khách chọn, giữ chỗ có thể nhả nên trợ lý làm được ngay. Đổi vé dùng lần miễn phí duy nhất, nên khách phải xem lại và bấm xác nhận riêng. Sang S2, yêu cầu hoàn đã gửi, nên trợ lý nói rõ giới hạn rồi đưa khách tới nhân viên cùng thông tin đặt chỗ.”

## Bằng chứng cho phần trình bày

Nội dung theo phân công của Nguyễn Quốc Quang Anh đã có trong bài chung, với lập luận, đường bấm và bằng chứng nêu ở trên. Tài liệu này tổng hợp phần được phân công để sử dụng khi demo; không ghi thay trải nghiệm hoặc ý kiến cá nhân chưa được cung cấp. Kết quả được cập nhật chung tại §7 sau demo.
