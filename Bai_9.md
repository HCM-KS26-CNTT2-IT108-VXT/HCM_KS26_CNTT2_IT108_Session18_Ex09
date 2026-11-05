# BÀI 9: THIẾT KẾ KIẾN TRÚC KÉT SẮT SỐ BITWARDEN VÀ CHÍNH SÁCH MẬT KHẨU GAME STUDIO

## Phần 1: Báo cáo phân tích kiến trúc an ninh mật khẩu

### Câu 1. Vì sao lưu mật khẩu trên Google Chrome lại nguy hiểm khi máy tính bị nhiễm mã độc Infostealer?

* Mật khẩu lưu trong Chrome có thể bị mã độc Infostealer tìm cách đánh cắp.
* Hacker có thể lấy dữ liệu đăng nhập và cookie trình duyệt.
* Từ đó, hacker có thể truy cập GitHub, AWS hoặc các tài khoản công việc.
* Nếu dùng chung mật khẩu, nhiều tài khoản có thể bị chiếm cùng lúc.

### Câu 2. Giải thích kiến trúc Zero-Knowledge và Client-side Decryption.

* **Zero-Knowledge:** Bitwarden không biết và không thể đọc mật khẩu bên trong két sắt của người dùng.
* **Client-side Decryption:** Dữ liệu được mã hóa và chỉ giải mã trên thiết bị của người dùng.
* Nếu máy chủ Bitwarden bị hacker tấn công, hacker chỉ lấy được dữ liệu đã mã hóa, không thể đọc trực tiếp mật khẩu nếu không có khóa giải mã.

## Phần 2: Thiết kế Chính sách và Kịch bản Chuyển đổi

### Câu 3. Thiết kế cách tạo Master Passphrase đạt chuẩn và đưa ra 1 ví dụ.

* Sử dụng một câu gồm nhiều từ ngẫu nhiên, dễ nhớ nhưng khó đoán.
* Độ dài tối thiểu 20 ký tự.
* Không sử dụng tên, ngày sinh hoặc thông tin cá nhân.
* Không dùng lại mật khẩu này cho tài khoản khác.

**Ví dụ:** `MayXanh!BayQuaBien2026`

Đây là ví dụ minh họa, khi sử dụng thực tế nên tạo một cụm từ ngẫu nhiên riêng.

### Câu 4. Xây dựng bảng cấu hình Generator trong Bitwarden cho 40 tài khoản.

|Tiêu chí|Cấu hình|
|-|-|
|Độ dài mật khẩu|24 ký tự|
|Chữ in hoa (A-Z)|Có|
|Chữ thường (a-z)|Có|
|Chữ số (0-9)|Có|
|Ký tự đặc biệt|Có|
|Không trùng mật khẩu|Mỗi tài khoản một mật khẩu riêng|
|Lưu trữ|Lưu trực tiếp trong Bitwarden|

### Câu 5. Vì sao Auto-fill của Bitwarden chống Phishing tốt hơn con người?

* Bitwarden kiểm tra tên miền website trước khi tự động điền mật khẩu.
* Chỉ tự động điền khi tên miền phù hợp với thông tin đã lưu.
* Ví dụ: Mật khẩu GitHub chỉ được điền vào `github.com`, không tự động điền vào `githúb.com`.
* Nhờ đó, hạn chế việc gửi mật khẩu cho website giả mạo.

### Câu 6. Thiết lập quy trình lưu trữ Khóa Cấp cứu (Emergency Kit).

* Sau khi tạo tài khoản Bitwarden, lưu thông tin Emergency Kit.
* In một bản giấy và cất trong két sắt tại văn phòng.
* Chỉ Trưởng nhóm và người được ủy quyền mới được tiếp cận.
* Không gửi Emergency Kit qua nhóm chat hoặc email thông thường.
* Thiết lập quyền truy cập khẩn cấp hoặc cơ chế quản trị tài khoản tổ chức để Trưởng nhóm có thể xử lý khi Trưởng phòng Kỹ thuật gặp sự cố.

