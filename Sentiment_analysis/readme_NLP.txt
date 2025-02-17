Hướng dẫn xây dựng mô hình phân tích cảm xúc bằng NLP:

Bước 1: Load dữ liệu từ folder gốc, trong folder gốc có 2 folder con là train và test, trong 2 folder train và test đều có 2 folder con là neg và pos để gán nhãn cho dữ liệu, những dữ liệu ở trong folder neg được gắn nhãn là neg và tương tự với pos.


Bước 2: Tiền xử lý dữ liệu như chuyển về chữ thường, loại bỏ số, ký tự đặc biệt, khoảng trắng thừa, tách từ tiếng việt.


Bước 3: Vector hóa với Sentence-BERT, với mô hình cụ thể “distiluse-base-multilingual-cased-v1”


Bước 4: Huấn luyện mô hình và thự hiện kiểm tra trên bộ dữ liệu test.


Bước 5: Lưu kết quả của mô hình dùng để chạy cho các lần tiếp theo mà không cần train lại từ đầu


Bước 6: Tiền xử lý và dự đoán trên đoạn test mới


Bước 7: Thực hiện lấy dữ liệu trên mongoDB về thực hiện phân tích cảm xúc của mình luận trong các group hay page.


!!! Lưu ý !!! Nếu muốn chạy mà không cần phải train lại mô hình thì chỉ cần chạy bước 1, 2 và chỉnh lại cho đúng đường dẫn của “model_save_path/sentiment_classifier.pkl” ở bước 6 sau đó thực hiện chạy bước 7 ( lấy dữ liệu từ mongoDB về ) và xem kết quả phân tích cảm xúc của các bình luận đã được cào về và lưu trên mongoDB. 






Hướng dẫn xây dựng mô hình phân tích cảm xúc bằng React của bài viết trên Page

Vì các bài viết trên page được đăng bởi chủ page nên nếu phân tích bằng NLP thì luôn cho ra kết quả tích cực, không thể biết được cảm xúc của người dùng với bài viết đó. Vì thế ta sử dụng các khác để tính điểm cảm xúc của khách hàng, tính bằng công thức sau: 


Sentiment Score = [( Tổng cảm xúc tích cực ) - ( Tổng cảm xúc tiêu cực )] / ( Tổng số cảm xúc )


!!! Lưu ý !!! Sentiment Score nằm trong khoảng -1 đến 1, càng gần về -1 thì cảm xúc càng tiêu cực, càng gần về 1 thì cảm xúc càng tích cực, nếu bằng 0 thì bài viết có cảm xúc cân bằng giữa tích cực và tiêu cực.