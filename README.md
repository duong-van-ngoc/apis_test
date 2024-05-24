# apis_test
# Giới thiệu:
Mục tiêu của bài tập này là thực hành kiểm thử API bằng cách sử dụng Postman. Bài tập bao gồm các bước từ việc lựa chọn một API thực tế, phân tích tài liệu API, viết các trường hợp kiểm thử, thực hiện kiểm thử và ghi lại kết quả kiểm thử.
# api được chọn 
API được lựa chọn cho bài tập này là  Random Data API
# phân tích tài liệu api 
Để hiểu rõ các chức năng và điểm cuối của OpenWeatherMap API, tài liệu API đã được tham khảo:

Điểm cuối chính: https:https://random-data-api.com/api/v2
Phương thức: GET
Tham số bắt buộc:
beers
beersType=light

# Các trường hợp kiểm thử API
Việc kiểm thử với Random Data API là một phương pháp quan trọng để đảm bảo tính toàn vẹn và độ tin cậy của ứng dụng. Dưới đây là một số trường hợp kiểm thử bạn có thể áp dụng khi sử dụng Random Data API:

1. Kiểm thử dữ liệu đầu vào hợp lệ
Mục tiêu: Đảm bảo API hoạt động đúng khi nhận dữ liệu hợp lệ.

Thực hiện: Gửi yêu cầu với dữ liệu đầu vào hợp lệ theo định dạng yêu cầu của API.
Kết quả mong đợi: API trả về kết quả chính xác và không có lỗi.
2. Kiểm thử dữ liệu đầu vào không hợp lệ
Mục tiêu: Xác định cách API xử lý các trường hợp dữ liệu đầu vào không hợp lệ.

Thực hiện: Gửi yêu cầu với dữ liệu đầu vào không hợp lệ, ví dụ như kiểu dữ liệu sai, thiếu trường bắt buộc, hoặc dữ liệu vượt quá giới hạn.
Kết quả mong đợi: API trả về lỗi phù hợp và thông báo lỗi chi tiết.
3. Kiểm thử tải trọng cao (Stress Testing)
Mục tiêu: Xem xét hiệu suất của API khi chịu tải cao.

Thực hiện: Gửi một số lượng lớn yêu cầu tới API trong một khoảng thời gian ngắn.
Kết quả mong đợi: API xử lý yêu cầu mà không bị gián đoạn hoặc lỗi nghiêm trọng, thời gian phản hồi trong giới hạn cho phép.
4. Kiểm thử tải ổn định (Load Testing)
Mục tiêu: Đánh giá hiệu suất của API dưới tải trọng ổn định.

Thực hiện: Gửi yêu cầu liên tục tới API với tải trọng ổn định trong một khoảng thời gian dài.
Kết quả mong đợi: API duy trì hiệu suất ổn định, không có sự suy giảm đáng kể trong thời gian phản hồi.
5. Kiểm thử giới hạn tần suất (Rate Limiting)
Mục tiêu: Đảm bảo API thực hiện đúng các giới hạn tần suất yêu cầu.

Thực hiện: Gửi yêu cầu vượt quá giới hạn tần suất quy định của API.
Kết quả mong đợi: API trả về lỗi giới hạn tần suất (thường là HTTP 429 Too Many Requests).
6. Kiểm thử bảo mật
Mục tiêu: Kiểm tra các lỗ hổng bảo mật trong API.

Thực hiện: Thực hiện các bài kiểm thử bảo mật như SQL injection, XSS, và kiểm tra xác thực/ủy quyền.
Kết quả mong đợi: API an toàn trước các lỗ hổng bảo mật, không bị khai thác bởi các tấn công phổ biến.
7. Kiểm thử tính toàn vẹn của dữ liệu
Mục tiêu: Đảm bảo dữ liệu trả về bởi API luôn chính xác và không bị lỗi.

Thực hiện: Gửi các yêu cầu ngẫu nhiên và kiểm tra tính toàn vẹn của dữ liệu trả về.
Kết quả mong đợi: Dữ liệu trả về phải chính xác, đầy đủ và không bị lỗi.
# Các trường hợp kiểm thử với postman
Trường Hợp Kiểm Thử 1: Truy vấn dữ liệu người dùng ngẫu nhiên hợp lệ
Điểm cuối: https://random-data-api.com/api/users/random_user
Phương thức: GET
Kết quả mong đợi: Mã trạng thái 200 và dữ liệu người dùng ngẫu nhiên hợp lệ.

Trường Hợp Kiểm Thử 2: Truy vấn dữ liệu không tồn tại
Điểm cuối: https://random-data-api.com/api/nonexistent_endpoint
Phương thức: GET
Kết quả mong đợi: Mã trạng thái 404 và thông báo lỗi không tìm thấy endpoint.

Trường Hợp Kiểm Thử 3: Sử dụng API key không hợp lệ và không có API key
Điểm cuối: https://random-data-api.com/api/users/random_user?apikey=invalidapikey và https://random-data_api.com/api/users/random_user
Phương thức: GET
Kết quả mong đợi: Mã trạng thái 401 và thông báo lỗi xác thực.

Trường Hợp Kiểm Thử 4: Yêu cầu không có thông số bắt buộc
Điểm cuối: https://random-data-api.com/api/users/random_user?size=
Phương thức: GET
Kết quả mong đợi: Mã trạng thái 400 và thông báo lỗi thiếu thông số bắt buộc.

Hướng dẫn cụ thể cho từng trường hợp kiểm thử:
Trường Hợp Kiểm Thử 1: Truy vấn dữ liệu người dùng ngẫu nhiên hợp lệ
Mở Postman và tạo một yêu cầu mới.
Chọn phương thức GET và nhập URL: https://random-data-api.com/api/users/random_user.
Bấm "Send" để gửi yêu cầu.
Kiểm tra kết quả mong đợi:
javascript

# Trường Hợp Kiểm Thử 1:
![image](https://github.com/duong-van-ngoc/apis_test/assets/96899294/a49793ef-75ca-4580-9313-16317080d563)

# Trường Hợp Kiểm Thử 2:
![image](https://github.com/duong-van-ngoc/apis_test/assets/96899294/eb5ee02b-4764-40d4-953e-b89b38b42bf1)
#Trường Hợp Kiểm Thử 3:
![image](https://github.com/duong-van-ngoc/apis_test/assets/96899294/f156dc37-5a58-40b5-95ef-7989db52148e)
# Trường Hợp Kiểm Thử 4:
![image](https://github.com/duong-van-ngoc/apis_test/assets/96899294/c1e5efee-fec5-4f46-be4d-dcf647244f16)

# Báo cáo chi tiết
Mục Tiêu Kiểm Thử:

Xác định và xác thực các phản hồi của Random Data API dựa trên các truy vấn khác nhau.
Phạm Vi Kiểm Thử:

Các điểm cuối liên quan đến việc lấy dữ liệu ngẫu nhiên từ API.
Kết Quả Kiểm Thử:

Tất cả các trường hợp kiểm thử được thực hiện và kết quả phù hợp với mong đợi.
API hoạt động đúng với các yêu cầu hợp lệ và xử lý các lỗi một cách thích hợp khi cung cấp dữ liệu không hợp lệ hoặc khi không có quyền truy cập.
Khuyến Nghị:

API hoạt động tốt và xử lý các lỗi đúng cách.
Duy trì tài liệu chi tiết và cung cấp các ví dụ cụ thể để hỗ trợ người dùng API.
