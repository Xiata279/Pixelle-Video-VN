# 🙋‍♀️ Câu Hỏi Thường Gặp - Pixelle-Video

### Làm thế nào để tích hợp workflow tùy chỉnh?

Nếu bạn muốn tích hợp workflow ComfyUI của riêng mình, hãy làm theo các bước sau:

1.  **Chạy cục bộ trước**: Đảm bảo workflow chạy đúng trong ComfyUI của bạn.
2.  **Gắn tham số**: Tìm node Text (CLIP Text Encode hoặc node nhập văn bản tương tự) nơi prompt cần được truyền động bởi chương trình.
    -   Chỉnh sửa **Tiêu đề (Title)** của node đó.
    -   Đổi tiêu đề thành `$prompt.text!` hoặc `$prompt.value!` (tùy thuộc vào kiểu đầu vào mà node chấp nhận).
     <img src="https://github.com/user-attachments/assets/ddb1962c-9272-486f-84ab-8019c3fb5bf4" width="600" alt="Ví dụ gắn tham số" />

    -   *Tham khảo: Xem cách chỉnh sửa các file JSON có sẵn trong thư mục `workflows/selfhost/`.*
3.  **Định dạng xuất**: Xuất workflow đã chỉnh sửa dưới dạng **API Format** (Save (API Format)).
4.  **Đặt tên file**: Đặt file JSON xuất vào thư mục `workflows/` và tuân theo các tiền tố đặt tên sau:
    -   **Workflow Hình ảnh**: Tiền tố phải là `image_` (ví dụ: `image_my_style.json`)
    -   **Workflow Video**: Tiền tố phải là `video_`
    -   **Workflow TTS**: Tiền tố phải là `tts_`

### Làm thế nào để debug workflow RunningHub trên máy cục bộ?

Nếu bạn muốn kiểm tra trên máy cục bộ các workflow ban đầu dành cho RunningHub đám mây:

1.  **Lấy ID**: Mở file workflow RunningHub và tìm ID.
2.  **Tải Workflow**: Dán ID vào cuối URL RunningHub (ví dụ: https://www.runninghub.cn/workflow/1983513964837543938) để vào trang workflow.
  <img src="https://github.com/user-attachments/assets/e5330b3a-5475-44f2-81e4-057d33fdf71b" width="600" alt="Ví dụ tải workflow" />


3.  **Tải xuống máy**: Tải workflow dưới dạng file JSON từ workbench.
4.  **Kiểm tra cục bộ**: Kéo file đã tải vào canvas ComfyUI cục bộ để kiểm tra và debug.

### Các Lỗi Thường Gặp và Cách Khắc Phục

#### 1. Lỗi TTS (Chuyển Văn Bản Thành Giọng Nói)
-   **Nguyên nhân**: Edge-TTS mặc định gọi giao diện miễn phí của Microsoft, có thể thất bại thường xuyên do mạng không ổn định.
-   **Giải pháp**:
    -   Kiểm tra kết nối mạng của bạn.
    -   Nên chuyển sang workflow **ComfyUI TTS** (chọn workflow có tiền tố `tts_`) để ổn định hơn.

#### 2. Lỗi LLM (Mô Hình Ngôn Ngữ Lớn)
-   **Các bước khắc phục**:
    1.  Kiểm tra xem **Base URL** có đúng không (đảm bảo không có dấu cách thừa hoặc hậu tố sai).
    2.  Kiểm tra xem **API Key** có hợp lệ và còn đủ số dư không.
    3.  Kiểm tra xem **Tên Model** có viết đúng chính tả không.
    -   *Mẹo: Tham khảo tài liệu API chính thức của nhà cung cấp model của bạn (ví dụ: OpenAI, DeepSeek, Google, v.v.) để có cấu hình chính xác.*

#### 3. Lỗi "Could not find a Chrome executable..."
-   **Nguyên nhân**: Hệ thống máy tính của bạn thiếu lõi trình duyệt Chrome, khiến các tính năng phụ thuộc vào trình duyệt bị lỗi.
-   **Giải pháp**: Tải và cài đặt trình duyệt Google Chrome.

### Video được tạo lưu ở đâu?

Tất cả video được tạo tự động lưu trong thư mục `output/` trong thư mục dự án. Sau khi hoàn thành, giao diện sẽ hiển thị thời lượng video, kích thước file, số cảnh quay và link tải xuống.

### Tài Nguyên Cộng Đồng

-   **Kho GitHub**: https://github.com/AIDC-AI/Pixelle-Video
-   **Báo lỗi**: Gửi lỗi hoặc yêu cầu tính năng qua GitHub Issues.
-   **Hỗ trợ Cộng đồng**: Tham gia nhóm thảo luận để được hỗ trợ và chia sẻ kinh nghiệm.
-   **Đóng góp**: Dự án theo giấy phép Apache 2.0 và chào đón mọi đóng góp.

💡 **Mẹo**: Nếu bạn không tìm thấy câu trả lời trong FAQ này, hãy gửi issue trên GitHub hoặc tham gia thảo luận cộng đồng. Chúng tôi sẽ tiếp tục cập nhật FAQ dựa trên phản hồi của người dùng!
