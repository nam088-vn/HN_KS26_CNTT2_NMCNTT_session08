**Bài 6 : Rà soát Script bảo trì hệ thống**

## **Phần 1: Phân tích**

* **Điểm nguy hiểm:** Đoạn mã AI gợi ý yêu cầu xóa toàn bộ gốc ổ đĩa `C:\`, có khả năng quét và xóa sạch toàn bộ hệ điều hành Windows, phần mềm và dữ liệu quan trọng.  
* **Giải thích:**  
  1. `-Path "C:\*"`: Chỉ định phạm vi tác động là toàn bộ thư mục và tệp gốc trong ổ `C`.  
  2. `-Recurse`: Quét sâu vào tất cả các thư mục con bên trong.  
  3. `-Force`: Ép xóa cả các tệp ẩn, tệp hệ thống hoặc tệp đang bị khóa mà không hiện bảng hỏi xác nhận.  
* **Hậu quả:** Làm hỏng hệ thống, máy tính sập nguồn hoặc không thể khởi động lại được nữa.  
* **Áp dụng 3 Nguyên tắc "Vàng" thẩm định mã AI:**  
  1. *Không bao giờ chạy trực tiếp mã AI khi chưa đọc hiểu.*  
  2. *Kiểm tra kỹ các ký tự đại diện và đường dẫn hệ thống (`C:\*`).*  
  3. *Khoanh vùng phạm vi hoạt động của lệnh xóa bên trong thư mục cụ thể.*

## **Phần 2: Triển khai** 

## Mã nguồn an toàn:

\# Chuyển đến thư mục logs của dự án Set-Location ".\\logs" 

\# Lọc dòng chứa WARNING từ system.log ra tệp issues.txtGet-Content system.log | Select-String "WARNING" | Out-File issues.txt \-Encoding utf8 

\# Xóa giới hạn các tệp .tmp bên trong thư mục hiện tại (an toàn) Remove-Item \-Path "\*.tmp" \-Force

## **Phần 3: Kiểm thử**

## Các lệnh kiểm tra kết quả trên PowerShell:

- kiểm tra nội dung tệp: Get-Content issues.txt  
- xác nhận tệp bị xoá : Get-ChildItem  
- kiểm tra nhanh tệp còn tồn tại không: Test-Path issues.txt

