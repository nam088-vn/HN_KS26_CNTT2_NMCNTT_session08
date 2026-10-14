**Bài 2 : Xử lý sự cố Website từ Access Log**

## **Phần 1: Phân tích**

* Lỗi tư duy của An: An đang nhầm lẫn giữa việc tìm tên hoặc vị trí tệp tin với việc tìm nội dung chữ viết bên trong tệp.  
* Lệnh `Get-ChildItem` dùng để liệt kê danh sách các tệp hoặc thư mục, chứ không mở tệp ra đọc chữ bên trong.  
* Lệnh `select-String` mới là công cụ chuyên dụng để quét và tìm kiếm từ khóa *bên trong* nội dung tệp tin 

 **Phần 2: Hoàn thiện**

- Câu lệnh: Select-String \-Path access.log \-Pattern "error"

