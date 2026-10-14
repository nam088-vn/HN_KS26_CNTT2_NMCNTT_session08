**Bài 5 : Tối ưu quy trình xử lý Log hằng ngày**

**Phần 1: Thiết Kế**

1: Header block  
\# Tên script: auto\_report.ps1  
\# Tác giả: Kỹ sư DevOps  
\# Ngày tạo: 2026-10-14

2: Biến cấu hình  
\$log\_file \= "server.log"   
\$report\_file \= "daily\_report.txt"

3: Thông báo tiến trình  
Write-Host "Dang lọc log 404..." \-ForegroundColor Cyan

4: Logic xử lý  
Đọc tệp log (`Get-Content`), lọc lỗi 404 (`Select-String`), ghi tiêu đề và kết quả vào tệp báo cáo.

**Phần 2**  
\# Khai báo file  
\$log \= "server.log"  
\$report \= "daily\_report.txt"

\# Báo cáo trạng thái  
Write-Host "Dang loc log..." \-ForegroundColor Yellow

\# Ghi tiêu đề và lọc lỗi 404  
"=== HE THONG TU DONG LOC LOG \===" | Out-File \$report \-Encoding utf8  
Get-Content \$log | Select-String "404" | Out-File \$report \-Append \-Encoding utf8

\# Hoàn tất  
Write-Host "Xong\! Da luu vao \$report" \-ForegroundColor Green  
