Ở đây chúng ta xây dựng mô hình dự đoán giá cổ phiếu bằng mạng LSTM (Long Short Term Memory) làm qua Google Colab. Kết nối Google Colab với drive để sau khi train xong model, ta có thể lưu lại vào drive. 
Ở bước Prepare data, ta chia tỷ lệ giá cổ phiếu trong khoảng (0,1) để dễ tính toán hơn. Sau đó, chia tập dữ liệu ban đầu thành x_train và y_train.Trong đó, x_train là danh sách bao gồm các tập chứa giá trị của 60 ngày liên tiếp. Ví dụ: (1,...,60), (2,...,61), (3,...,62)... . y_train là danh sách gồm các giá trị của ngày tiếp theo. Ví dụ: 61, 62, 63, ... Mục đích là để cho model học được: cứ 60 time steps trong x_train sẽ dự đoán được time steps 61 chứa trong y_train. 
Ở đây tạo 1 LSTM với 50 tế bào thần kinh và 3 lớp ẩn. Cuối cùng có 1 lớp đầu ra để dự đoán giá cổ phiếu. Để tránh sai số, chúng ta dùng hàm SME và công cụ tối ưu hóa Adam.Sau khi train xong model được lưu vào drive.
File MSN Historical Data.csv là dữ liệu từ 25/12/2017 đến 22/12/2020 để train model. Còn file MSN Historical Data (1) là dữ liệu thực tế của cổ phiếu MSN từ 25/12/2017 đến 31/12/2021 để so sánh với dự báo của model
