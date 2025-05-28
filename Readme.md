Trợ Lý Y Tế Thông Minh dựa trên LLMs, RAG và Flask
Đây là một ứng dụng Web mẫu được viết bằng Flask,
tích hợp một Chatbot Trợ Lý Y Tế được hỗ trợ bởi
Mô Hình Ngôn Ngữ Lớn (LLMs) và Kỹ thuật Truy xuất kết hợp sinh (RAG).

Ứng dụng sử dụng thư viện langchain làm nền tảng, tận dụng agents và tools
của langchain để xây dựng một hệ thống RAG có thể sử dụng các công cụ như kho vector và cơ sở dữ liệu SQL.
Mô hình ngôn ngữ LLM được sử dụng là llama3.1 cung cấp bởi ollama. SQLite là cơ sở dữ liệu nền,
và FAISS là kho lưu trữ vector.
Tất cả các công nghệ này đều chạy cục bộ, không yêu cầu khóa API.

Lưu ý
Đây chỉ là một dự án mẫu, và các câu trả lời từ Trợ Lý Y Tế
không nên được xem là lời khuyên y tế chính thức dưới bất kỳ hình thức nào.

Tính năng
Người dùng có thể trò chuyện với Trợ Lý Y Tế thông qua giao diện chat.
Trợ Lý có thể đưa ra phản hồi hữu ích cho các câu hỏi của người dùng,
kết hợp với dữ liệu bổ sung như một cơ sở tri thức thông qua RAG.

Hệ thống duy trì một cơ sở dữ liệu gồm thông tin bệnh nhân, bác sĩ, lịch hẹn, và lịch sử trò chuyện.

Trợ Lý có thể gợi ý lịch hẹn với bác sĩ phù hợp dựa trên câu hỏi của người dùng.

Trợ Lý có thể hiển thị các khung giờ còn trống để đặt lịch hẹn,
người dùng có thể đặt, xem và chỉnh sửa các cuộc hẹn.

Người dùng có thể tải xuống lịch sử trò chuyện.

Người dùng có thể báo cáo tình huống khẩn cấp về sức khỏe,
và Trợ Lý sẽ ghi nhận tình huống đó cùng với mã màu (ĐỎ, VÀNG, XANH)
để hỗ trợ các chuyên gia y tế xử lý kịp thời (thông qua script src/check_emergencies.py).

Yêu cầu
Python 3.10

Cài đặt thư viện: pip install -r requirements.txt

- Install [Ollama](https://ollama.com/download)

Tối thiểu 8GB RAM

GPU Nvidia với ít nhất 2GB bộ nhớ riêng

Thiết lập
Tải bộ dữ liệu ([MedQuad](https://drive.google.com/drive/folders/1-96u0Wu1yfiJD-hwZ1T3_CmII0vFav69?fbclid=IwY2xjawIVfIFleHRuA2FlbQIxMAABHb4zN6TT1g2LWohYzFuUUK_I3WihZlHAytvYYosqCYq0kA3Or00h5902wA_aem_CK_LVlFk1NRjQ08hZNwXJg)) vào thư mục data. ( tạo thư mục data tại thư mục root -> giải nén dataset này và ném hết tất cả các folder giải nén được vào data ) 

Chuẩn bị chỉ mục vector: chạy src/create_index.py.

Chuẩn bị cơ sở dữ liệu SQLite: chạy src/create_db.py.

Tải mô hình LLM từ Ollama: ollama pull llama3.1.

Khởi động máy chủ: chạy app.py.

Khởi chạy client bằng cách mở trình duyệt và truy cập 127.0.0.1:8080.

Ghi chú
Nếu gặp lỗi liên quan đến gói nltk trong script src/create_index.py,
hãy kiểm tra tập tin src/create_index.py để làm theo hướng dẫn sửa lỗi.

Lưu ý rằng nếu bạn chạy ứng dụng trên phần cứng hạn chế,
Trợ Lý có thể mất một thời gian dài (~10 phút) để đưa ra câu trả lời.
