**Bài 1 : Xử lý Log máy chủ dung lượng lớn**  
**Phần 1: Phân tích**

* Vì Notepad cố gắng tải toàn bộ tệp 800MB vào bộ nhớ RAM cùng một lúc, làm quá tải bộ nhớ và treo máy.  
* Vì CMD truyền thống của Windows không có lệnh cat   
* Vì trong PowerShell, cat thực chất chỉ là một tên viết tắt (alias) được tạo sẵn để trỏ đến lệnh chính hãng Get-Content.

**Phần 2: Bộ lệnh chuẩn trên PowerShell**

- xem toàn bộ thư mục: Get-Content server\_log\_800MB.log | more  
- xem 10 dòng cuối cùng: Get-Content server\_log\_800MB.log \-Tail 10


