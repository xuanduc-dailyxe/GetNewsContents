Hãy đóng vai một chuyên gia lập trình Frontend. Viết cho tôi toàn bộ mã nguồn của một ứng dụng web gói gọn trong một file index.html duy nhất. Ứng dụng này là một công cụ scrape và xử lý dữ liệu HTML, hình ảnh từ website khác.

Tech stack bắt buộc:

HTML5, CSS3.

Tailwind CSS (qua CDN) để dựng layout UI nhanh và chuẩn.

jQuery (qua CDN) để thao tác DOM và xử lý sự kiện.

Ace Code Editor (qua CDN) để hiển thị code HTML.

Lưu ý: Trình duyệt của tôi đã cài extension bypass CORS, nên bạn chỉ cần dùng fetch hoặc $.ajax thông thường, không cần viết proxy.

Yêu cầu Giao diện & Tính năng (Layout 3 cột):

1. Cột trái (Sidebar - Quản lý cấu hình website):

Hiển thị danh sách các "Profile Website" đã lưu.

Góc trên bên phải có một icon dấu Cộng (+) để thêm profile.

Khi bấm thêm, hiển thị form (modal hoặc hiển thị ngay trong cột) nhập 3 thông tin:

Tên miền (Domain).

Class/ID của thẻ chứa Tiêu đề bài viết.

Class/ID của thẻ cha chứa Nội dung bài viết.

Lưu toàn bộ danh sách cấu hình này vào localStorage. Khi load lại trang phải hiển thị lại danh sách. Có thể click vào một cấu hình trong danh sách để chọn nó làm cấu hình đang active.

2. Cột giữa (Xử lý và hiển thị nội dung):

Phía trên cùng: 1 Input nhập URL bài viết và 1 Button "Get content".

Khi click "Get content", dựa vào URL và Profile đang active, tiến hành fetch HTML của trang web đó. Dùng DOMParser để bóc tách tiêu đề và nội dung HTML theo Class/ID đã định nghĩa.

Bên dưới hiển thị:

1 Input Text chứa Tiêu đề tin tức (tự động điền từ kết quả fetch).

1 Input Text chứa Mô tả tin tức (cho phép người dùng tự nhập).

Bên dưới cùng: Trình soạn thảo Ace Editor.

Hiển thị mã HTML của phần nội dung tin tức vào đây.

Logic quan trọng: Mã HTML trước khi đưa vào Ace Editor phải được format sạch sẽ: Xoá bỏ TOÀN BỘ các thuộc tính bên trong tất cả các thẻ (ví dụ <div class="a" style="b"> thành <div>), CHỈ GIỮ LẠI duy nhất thuộc tính src của thẻ <img> và href của thẻ <a>.

3. Cột phải (Sidebar - Quản lý và xử lý hình ảnh):

Cột này quét toàn bộ các thẻ <img> có trong phần nội dung HTML vừa lấy được ở trên và hiển thị chúng dưới dạng danh sách thumbnail.

Phía trên cùng của cột cung cấp một thẻ Select hoặc Radio buttons để chọn tỉ lệ hình ảnh: 4:3, 3:2, 16:9.

Trên mỗi thumbnail, ở góc dưới hiển thị một icon/nút Download.

Logic quan trọng khi Download:

Khi người dùng click download một ảnh, dùng Canvas API để tải ảnh gốc.

Tự động tính toán crop (cắt) ảnh canh ngay chính giữa (center crop) dựa trên tỉ lệ đã chọn ở trên.

Convert ảnh kết quả sau khi crop sang định dạng .jpg.

Tự động trigger tải file ảnh .jpg đó xuống máy người dùng.

Yêu cầu về Code:

Gộp toàn bộ HTML, CSS (style bổ sung nếu cần) và JS vào đúng 1 file index.html.

Code Javascript cần chia function rõ ràng, có comment giải thích, đặc biệt là ở phần xử lý xoá thuộc tính HTML và tính toán crop ảnh trên Canvas.