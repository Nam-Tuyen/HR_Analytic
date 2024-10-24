# HR_Analytic
File này thực hiện phân tích dữ liệu nhân sự nhằm hiểu rõ các yếu tố ảnh hưởng đến việc nhân viên rời công ty và đề xuất mức lương hợp lý cho năm kế tiếp.

**1. Mô tả cơ bản về file**
File này thực hiện phân tích dữ liệu nhân sự nhằm hiểu rõ các yếu tố ảnh hưởng đến việc nhân viên rời công ty và đề xuất mức lương hợp lý cho năm kế tiếp. Quy trình bao gồm các bước sau:

**Bước 1:** Đọc dữ liệu và kiểm tra thông tin

Đầu tiên, file CSV chứa thông tin về nhân viên được nạp vào dưới dạng DataFrame. Sau đó, dữ liệu được kiểm tra để phát hiện các giá trị thiếu và kiểm tra mô tả cơ bản về dữ liệu như kiểu dữ liệu và phân bố của các cột.

![image](https://github.com/user-attachments/assets/f12f23d5-f104-4b63-888d-93ea5e6892b1)


**Bước 2: Trực quan hóa dữ liệu**

Sử dụng seaborn và matplotlib để vẽ các biểu đồ giúp dễ dàng quan sát các đặc trưng quan trọng như lương, số năm làm việc và tỷ lệ nhân viên nghỉ việc. Các biểu đồ này giúp chúng ta hiểu rõ hơn về sự phân bố của các biến và sự khác biệt giữa các nhân viên rời đi và ở lại.

![image](https://github.com/user-attachments/assets/65f0d978-3844-4f20-a5f4-8647a5001a6a)


**Bước 3: Xử lý dữ liệu**

Dữ liệu dạng chuỗi được mã hóa bằng kỹ thuật One-Hot Encoding và các biến số được chuẩn hóa bằng MinMaxScaler để đưa về cùng một thang giá trị, giúp tăng hiệu quả của các thuật toán học máy.


**Bước 4: Xác định các yếu tố quan trọng**

Sử dụng mô hình Random Forest để xác định những đặc trưng quan trọng nhất ảnh hưởng đến quyết định rời công ty của nhân viên. Kết quả phân tích cho thấy các yếu tố như Mức lương hàng tháng và Số năm làm việc là những yếu tố then chốt.

![image](https://github.com/user-attachments/assets/51488656-5306-45eb-b0e5-b2da95b1acba)


**Bước 5: Phân cụm nhân viên**

Sử dụng KMeans clustering để phân nhóm nhân viên dựa trên Mức lương, Số năm kinh nghiệm, Sự hài lòng trong công việc và các yếu tố liên quan khác. Các nhóm nhân viên được xác định và gán nhãn bằng cột SalaryCluster.

![image](https://github.com/user-attachments/assets/1c98fbde-ee9b-40d7-844f-431e56473728)


**Bước 6: Đề xuất mức lương cho năm tới**

Dựa trên mức lương trung bình của từng nhóm, hệ thống đề xuất mức tăng lương hợp lý cho năm tiếp theo. Với giả định rằng các nhóm nhân viên có nguy cơ rời công ty cao sẽ được tăng lương khoảng 10% để giữ chân họ

<img width="512" alt="Ảnh màn hình 2024-10-25 lúc 03 38 21" src="https://github.com/user-attachments/assets/5e797989-4398-4f76-818c-2c4ff6719ff9">

