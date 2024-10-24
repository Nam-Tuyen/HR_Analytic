# HR_Analytic
File này thực hiện phân tích dữ liệu nhân sự nhằm hiểu rõ các yếu tố ảnh hưởng đến việc nhân viên rời công ty và đề xuất mức lương hợp lý cho năm kế tiếp.

**1. Mô tả cơ bản về file**
File này thực hiện phân tích dữ liệu nhân sự nhằm hiểu rõ các yếu tố ảnh hưởng đến việc nhân viên rời công ty và đề xuất mức lương hợp lý cho năm kế tiếp. Quy trình bao gồm các bước sau:

- Đọc và kiểm tra dữ liệu: Dữ liệu nhân sự được nạp từ một tệp CSV và kiểm tra các thông tin cơ bản như kiểu dữ liệu, mô tả thống kê và xử lý các giá trị thiếu.
- Trực quan hóa dữ liệu: Các biểu đồ phân phối được sử dụng để hiểu rõ hơn về các đặc trưng như tuổi, mức lương, số năm làm việc, mức độ hài lòng công việc và tỷ lệ nhân viên rời công ty.
- Xử lý và chuẩn bị dữ liệu: Dữ liệu được chuẩn hóa và mã hóa bằng cách sử dụng các kỹ thuật như OneHotEncoder và MinMaxScaler để chuẩn bị cho việc phân tích và mô hình hóa.
- Phân tích tầm quan trọng của các đặc trưng: Mô hình Random Forest được sử dụng để xác định những yếu tố quan trọng nhất ảnh hưởng đến việc nhân viên rời đi, bao gồm mức lương, số năm làm việc, và sự hài lòng trong công việc.
- Phân cụm nhân viên: KMeans được sử dụng để phân nhóm nhân viên theo mức lương và số năm kinh nghiệm, từ đó đưa ra gợi ý về mức tăng lương cho năm kế tiếp nhằm giữ chân nhân sự.
- Đề xuất mức lương: Tính toán mức tăng lương dựa trên mức lương trung bình hiện tại và giả định mức tăng 10% cho nhóm có nguy cơ rời đi cao.

**2. Quy trình thực hiện**

Bước 1: Đọc dữ liệu và kiểm tra thông tin

Đầu tiên, file CSV chứa thông tin về nhân viên được nạp vào dưới dạng DataFrame. Sau đó, dữ liệu được kiểm tra để phát hiện các giá trị thiếu và kiểm tra mô tả cơ bản về dữ liệu như kiểu dữ liệu và phân bố của các cột.

Bước 2: Trực quan hóa dữ liệu

Sử dụng seaborn và matplotlib để vẽ các biểu đồ giúp dễ dàng quan sát các đặc trưng quan trọng như lương, số năm làm việc và tỷ lệ nhân viên nghỉ việc. Các biểu đồ này giúp chúng ta hiểu rõ hơn về sự phân bố của các biến và sự khác biệt giữa các nhân viên rời đi và ở lại.

Bước 3: Xử lý dữ liệu

Dữ liệu dạng chuỗi được mã hóa bằng kỹ thuật One-Hot Encoding và các biến số được chuẩn hóa bằng MinMaxScaler để đưa về cùng một thang giá trị, giúp tăng hiệu quả của các thuật toán học máy.

Bước 4: Xác định các yếu tố quan trọng

Sử dụng mô hình Random Forest để xác định những đặc trưng quan trọng nhất ảnh hưởng đến quyết định rời công ty của nhân viên. Kết quả phân tích cho thấy các yếu tố như Mức lương hàng tháng và Số năm làm việc là những yếu tố then chốt.

Bước 5: Phân cụm nhân viên

Sử dụng KMeans clustering để phân nhóm nhân viên dựa trên Mức lương, Số năm kinh nghiệm, Sự hài lòng trong công việc và các yếu tố liên quan khác. Các nhóm nhân viên được xác định và gán nhãn bằng cột SalaryCluster.

Bước 6: Đề xuất mức lương cho năm tới

Dựa trên mức lương trung bình của từng nhóm, hệ thống đề xuất mức tăng lương hợp lý cho năm tiếp theo. Với giả định rằng các nhóm nhân viên có nguy cơ rời công ty cao sẽ được tăng lương khoảng 10% để giữ chân họ
