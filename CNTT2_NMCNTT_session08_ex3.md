**Bài 3 : Thống kê sự cố TIMEOUT trên máy chủ**

## **Phần 1: Phân tích**

Sơ đồ luồng dữ liệu qua Pipeline trong PowerShell:

\[Đọc tệp tin\] ──\> Get-Content log.txt   
 │   
 v   
\[Lọc từ khóa\] ──\> Select-String "TIMEOUT"   
 │                  | Where-Object { \$\_ \-notmatch "NOT TIMEOUT" }   
 v  
\[Đếm kết quả\] ──\> ( ... ).Count

**Phần 2: Triển khai**

- PowerShell: (Get-Content server\_log.log | Select-String "TIMEOUT" | Where-Object { \$\_ \-notmatch "NOT TIMEOUT" }).Count

