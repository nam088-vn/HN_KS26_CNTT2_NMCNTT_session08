**Bài 4 : Xây dựng quy trình lưu nhật ký hệ thống**

**Phần 1:** 

| Tiêu chí | Toán tử \> (Ghi đè) | Toán tử \>\> (Ghi nối tiếp) |
| :---- | :---- | :---- |
| **Cơ chế hoạt động** | Tương đương lệnh Out-File, **ghi đè toàn bộ** nội dung cũ bằng nội dung mới. Nếu tệp chưa có, tệp sẽ được tạo mới. | Tương đương lệnh Out-File \-Append, **ghi nối tiếp** nội dung mới vào cuối tệp hiện có mà không làm mất dữ liệu cũ. |
| **Rủi ro mất dữ liệu** | **Rất cao.** Nếu gõ nhầm vào cuối tháng khi tệp đã tích lũy dữ liệu 30 ngày, toàn bộ lịch sử trước đó sẽ bị xóa sạch hoàn toàn. | **Thấp.** An toàn cho việc tích lũy dữ liệu theo thời gian. |
| **Ngữ cảnh sử dụng** | Phù hợp khi tạo báo cáo mới từ đầu, chạy lại một phiên làm việc độc lập (ghi đè kết quả cũ). | Phù hợp theo dõi hệ thống 24/7, gom log/lỗi phát sinh liên tục trong ngày. |
| **Encoding file đầu ra** | Mặc định mã hóa theo chuẩn **UTF-16** (do dùng Out-File). Có thể gây lỗi hiển thị ký tự trên một số công cụ đọc không hỗ trợ. | Mặc định mã hóa theo chuẩn **UTF-16** (do dùng Out-File \-Append). |

**Phần 2:**  
**Giải pháp được chọn:** Sử dụng cơ chế ghi nối tiếp (`>>` hoặc `Out-File -Append` / `Add-Content`).  
**Lập luận:** Đối với việc giám sát hệ thống 24/7, nhật ký lỗi cần được tích lũy liên tục theo thời gian để kỹ sư tra cứu lịch sử sự cố. Việc dùng lệnh ghi đè (`>`) sẽ làm mất toàn bộ các bản ghi trước đó trong ngày.  
