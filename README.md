# HR_Analytic

**1. Nhập và làm sạch dữ liệu:**

Đọc dữ liệu từ file CSV Human_Resources.csv và kiểm tra các giá trị null, xác định các biến cần loại bỏ hoặc mã hóa.

Chuyển đổi các biến dạng chuỗi sang dạng số (ví dụ: biến "Attrition" được chuyển thành 0 và 1 để biểu thị nhân viên ở lại và nghỉ việc).

**2. Phân tích trực quan dữ liệu:**

Sử dụng biểu đồ phân phối dữ liệu để kiểm tra các yếu tố như "DistanceFromHome" (khoảng cách từ nhà đến công ty), "YearsWithCurrManager" (số năm làm việc với quản lý hiện tại), "MonthlyIncome" (thu nhập hàng tháng), và các đặc điểm khác.

![image](https://github.com/user-attachments/assets/e841a297-4ca5-4591-9227-b483c488223b)

Tạo các biểu đồ KDE và Boxplot để kiểm tra mối quan hệ giữa việc nhân viên rời công ty với các yếu tố ảnh hưởng.

![image](https://github.com/user-attachments/assets/8446933e-34d0-40c9-ae89-4bf8a5680da4)

![image](https://github.com/user-attachments/assets/8b0eed81-8b3c-4e9d-87d2-5ad9aa428ff0)

![image](https://github.com/user-attachments/assets/09efe1b8-aa60-41e2-a708-ae7d541e9a05)

![image](https://github.com/user-attachments/assets/bc3cca56-2762-41df-bcdc-e6575b97a5d3)

**3. Xây dựng mô hình dự đoán nghỉ việc (Attrition):**

Chia dữ liệu thành tập huấn luyện và kiểm tra, sau đó xây dựng mô hình phân loại sử dụng Random Forest.

Tính toán độ chính xác và các chỉ số như precision, recall, và f1-score. Tỷ lệ chính xác tổng thể là 85%, tuy nhiên mô hình gặp khó khăn trong việc dự đoán đúng những nhân viên có nguy cơ nghỉ việc (recall thấp cho nhân viên nghỉ việc là 0.07).

<img width="498" alt="Ảnh màn hình 2024-10-25 lúc 20 47 06" src="https://github.com/user-attachments/assets/04002762-e6a9-44e3-8237-b10ba5111d7d">

**4. Xác định các yếu tố ảnh hưởng đến quyết định nghỉ việc:**

Sử dụng Random Forest để xác định tầm quan trọng của các yếu tố (features), kết quả cho thấy 5 yếu tố quan trọng nhất ảnh hưởng đến nghỉ việc bao gồm:

Thu nhập hàng tháng (MonthlyIncome)
Độ tuổi (Age)
Làm thêm giờ (OverTime)
Tổng số năm làm việc (TotalWorkingYears)
Tỷ lệ thu nhập hàng ngày (DailyRate)

![image](https://github.com/user-attachments/assets/2074a0ea-5cf1-4c9e-ac5a-b1403379c756)

Xây dựng mô hình hồi quy logistic để kiểm tra chi tiết hơn về ảnh hưởng của từng yếu tố đối với quyết định nghỉ việc. Kết quả hồi quy cho thấy:

Làm thêm giờ (OverTime) có ảnh hưởng lớn nhất với hệ số dương, tức là nhân viên làm thêm giờ có xu hướng nghỉ việc cao hơn.
Thu nhập hàng tháng (MonthlyIncome) và tuổi tác (Age) có mối quan hệ âm với khả năng nghỉ việc, tức là nhân viên có thu nhập cao hơn và lớn tuổi hơn thường ít nghỉ việc hơn.

<img width="712" alt="Ảnh màn hình 2024-10-25 lúc 20 48 14" src="https://github.com/user-attachments/assets/22db109d-d755-4467-b393-1a6ab62e7f3e">

**5. Phân cụm nhân viên:**

Áp dụng thuật toán KMeans clustering để phân nhóm nhân viên dựa trên các yếu tố như: ('MonthlyIncome', 'TotalWorkingYears', 'YearsAtCompany', 'JobSatisfaction')

Sử dụng phương pháp Elbow và Silhouette Score để xác định số cụm tối ưu. Số cụm tối ưu được chọn là 3, từ đó nhân viên được phân thành 3 nhóm, mỗi nhóm có đặc điểm riêng về thu nhập và mức độ hài lòng.

![image](https://github.com/user-attachments/assets/c946591f-21d4-45af-af27-c162d1daffd8)

**Insight tìm ra:**

<img width="317" alt="Ảnh màn hình 2024-10-25 lúc 20 50 56" src="https://github.com/user-attachments/assets/9251a40d-03cb-4f59-a733-9548608b88ed">

![image](https://github.com/user-attachments/assets/787b5918-4836-4335-b172-4a82aac64db6)

**Thu nhập hàng tháng và làm thêm giờ là yếu tố quyết định:**

Nhân viên có thu nhập thấp và thường xuyên làm thêm giờ có xu hướng nghỉ việc cao hơn.
Điều này có thể do sự không hài lòng về việc phải làm thêm giờ mà không nhận được mức lương xứng đáng.
Mức độ hài lòng trong công việc khác nhau giữa các nhóm:

Nhân viên được phân thành các nhóm như "Nhân viên tiềm năng", "Nhân viên trung cấp", và "Nhân viên cốt lõi" dựa trên thu nhập và mức độ hài lòng.

Nhân viên cốt lõi có mức hài lòng vừa phải nhưng thu nhập cao, trong khi nhân viên tiềm năng có hài lòng cao nhưng thu nhập thấp, dễ có khả năng nghỉ việc nếu không có sự điều chỉnh về lương và chính sách phúc lợi.
Doanh nghiệp cần giải quyết như thế nào:

**Điều chỉnh lương thưởng:**

Nhân viên làm thêm giờ nên được thưởng hoặc trả lương xứng đáng để giảm nguy cơ nghỉ việc. 

Các nhóm nhân viên có tiềm năng (nhân viên mới hoặc nhân viên trẻ) cần được tăng thu nhập và tạo cơ hội thăng tiến để giữ chân họ.

**Cải thiện môi trường làm việc và cân bằng công việc-cuộc sống:**

Những nhân viên có số năm làm việc với quản lý hiện tại thấp hoặc có tổng số năm làm việc ít thường có nguy cơ nghỉ việc cao. Do đó, công ty cần cải thiện mối quan hệ giữa nhân viên và quản lý, đồng thời giúp nhân viên có cảm giác thoải mái và gắn bó với công việc.

**Đưa ra các chính sách hỗ trợ nhân viên có hài lòng thấp:**

Đối với các nhóm nhân viên có mức độ hài lòng thấp nhưng thu nhập cao (nhân viên cốt lõi), cần cung cấp thêm các chính sách hỗ trợ tinh thần hoặc cơ hội thăng tiến để duy trì lòng trung thành của họ.
