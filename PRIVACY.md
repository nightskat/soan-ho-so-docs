# Chính sách quyền riêng tư — Tiện ích "Soạn Hồ Sơ"

*Cập nhật lần cuối: 22/10/2026*

Chào mừng bạn sử dụng **Soạn Hồ Sơ** (sau đây gọi tắt là "Tiện ích"), một tiện ích mở rộng cho Google Sheets (Editor Add-on). Chúng tôi cam kết bảo vệ tuyệt đối sự riêng tư và bảo mật dữ liệu của bạn. Chính sách này giải thích rõ ràng và minh bạch về cách thức tiện ích hoạt động cũng như cách dữ liệu của bạn được xử lý.

---

## 1. Nguyên tắc cốt lõi: Dữ liệu không rời khỏi Google

- **Hoạt động trọn vẹn trong hạ tầng Google:** Tiện ích được xây dựng và thực thi 100% trên nền tảng Google Apps Script thuộc chính tài khoản Google của bạn.
- **Không máy chủ riêng (No external servers):** Chúng tôi không vận hành bất kỳ máy chủ trung gian, cơ sở dữ liệu bên ngoài hay dịch vụ lưu trữ phụ trợ nào.
- **Không gửi dữ liệu cho bên thứ ba:** Mã nguồn tiện ích không gọi bất kỳ yêu cầu mạng nào ra bên ngoài Google (hoàn toàn không sử dụng `UrlFetchApp` tới bên thứ ba). Dữ liệu trong bảng tính, biểu mẫu và tài liệu Google Docs của bạn không bao giờ bị truyền, sao chép hoặc chia sẻ cho nhà phát triển hay bất kỳ tổ chức nào khác.
- **Không sử dụng Trí tuệ nhân tạo (AI):** Phiên bản này của tiện ích hoàn toàn **KHÔNG** tích hợp hay sử dụng bất kỳ mô hình AI, mô hình ngôn ngữ lớn (LLM) hoặc công cụ học máy nào. Dữ liệu của bạn không bao giờ bị đưa vào mô hình AI để xử lý hay dùng để huấn luyện dữ liệu.

---

## 2. Mục đích sử dụng các quyền truy cập Google (OAuth Scopes)

Tiện ích chỉ yêu cầu các phạm vi quyền tối thiểu cần thiết để thực hiện các chức năng mà bạn chủ động yêu cầu:

1. **`https://www.googleapis.com/auth/drive.file` (Phạm vi tệp Drive hạn chế):**
   - Tiện ích chỉ có thể xem, chỉnh sửa hoặc tạo các tệp và thư mục mà bạn **chủ động cấp quyền** thông qua hộp thoại chọn tệp của Google (Google Picker), hoặc các tệp/thư mục do chính tiện ích tạo ra (ví dụ: thư mục *"Hồ sơ đã soạn"* trên Google Drive của bạn).
   - Tiện ích **tuyệt đối KHÔNG có quyền** truy cập, đọc, xem hay chỉnh sửa bất kỳ tệp hoặc thư mục cá nhân nào khác trên Google Drive của bạn.
2. **`https://www.googleapis.com/auth/spreadsheets`:**
   - Được dùng để đọc tiêu đề cột và các dòng dữ liệu trong bảng tính Google Sheets hiện tại nhằm ghép vào văn bản mẫu.
   - Được dùng để ghi đường dẫn liên kết của tài liệu đã tạo và thông báo kết quả xử lý vào cột *"Trạng thái hồ sơ"* trên bảng tính.
3. **`https://www.googleapis.com/auth/documents`:**
   - Được dùng để mở tệp mẫu Google Docs, quét tìm các thẻ trường giữ chỗ dạng `{{ten_truong}}`, và tạo tài liệu văn bản hoàn chỉnh bằng cách điền nội dung tương ứng vào tài liệu mới.
4. **`https://www.googleapis.com/auth/script.container.ui`:**
   - Được dùng để hiển thị giao diện thanh bên (Sidebar) cấu hình và mở hộp thoại phương thức (Modal Dialog) của Google Picker ngay trong giao diện Google Sheets.
5. **`https://www.googleapis.com/auth/script.scriptapp`:**
   - Được dùng để thiết lập hoặc hủy bỏ trình kích hoạt tự động (`onFormSubmit` trigger) khi bạn bật/tắt tính năng tự động sinh hồ sơ mỗi khi có câu trả lời mới từ Google Form gửi về.

---

## 3. Lưu trữ cấu hình và thông tin cài đặt

- Mọi thiết lập của bạn (bao gồm đường link mẫu Google Docs, đường link thư mục xuất Google Drive, bảng ánh xạ giữa cột bảng tính và trường trong mẫu) được lưu trữ trực tiếp trong thuộc tính tài liệu (`DocumentProperties`) của chính tệp Google Sheets mà bạn đang thao tác.
- **Nhật ký lỗi kỹ thuật:** khi tiện ích gặp lỗi chưa xử lý, Google Apps Script tự ghi thông báo lỗi vào Cloud Logging của dự án Google Cloud thuộc nhà phát triển (chỉ để sửa lỗi, tự xoá theo thời hạn lưu mặc định của Google). Thông báo lỗi có thể kèm một đoạn giá trị ô gây lỗi.
- Chúng tôi **không thu thập**, không theo dõi và không lưu trữ thông tin nhận dạng cá nhân (PII), địa chỉ IP, cookies, hay bất kỳ số liệu phân tích hành vi người dùng (telemetry/analytics) nào.

---

## 4. Quyền kiểm soát và xóa dữ liệu của người dùng

- **Quyền sở hữu:** Bạn là chủ sở hữu duy nhất của tất cả dữ liệu bảng tính, biểu mẫu, tệp mẫu và các tài liệu hồ sơ được sinh ra.
- **Xóa dữ liệu:** Bạn có thể tự do chỉnh sửa hoặc xóa bất kỳ tài liệu nào đã sinh trong Google Drive, xóa cột trạng thái trong Google Sheets, hoặc hủy kích hoạt tính năng tự động bất cứ lúc nào.
- **Thu hồi quyền truy cập:** Bạn có thể gỡ bỏ cài đặt tiện ích bất kỳ lúc nào từ menu tiện ích mở rộng của Google Sheets hoặc thu hồi toàn bộ quyền truy cập tài khoản tại trang quản lý bảo mật của Google ([https://myaccount.google.com/permissions](https://myaccount.google.com/permissions)). Khi gỡ tiện ích, toàn bộ quyền truy cập của tiện ích sẽ chấm dứt ngay lập tức.

---

## 5. Trách nhiệm của người dùng

Người dùng chịu trách nhiệm hoàn toàn đối với nội dung và tính hợp pháp của các thông tin, dữ liệu cá nhân hoặc dữ liệu kinh doanh được nhập vào Google Sheets, Google Forms và các tài liệu xuất ra.

---

## 6. Liên hệ

Nếu bạn có bất kỳ câu hỏi, phản hồi hoặc yêu cầu nào liên quan đến Chính sách quyền riêng tư này hoặc quá trình vận hành của tiện ích, xin vui lòng liên hệ:

- **Email hỗ trợ:** `[EMAIL LIÊN HỆ]`
- **Địa chỉ dự án:** Dự án tiện ích Google Sheets "Soạn Hồ Sơ"
