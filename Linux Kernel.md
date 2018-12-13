Linux Kernel
==

## 1. Khái niệm :
- Khái niệm **kernel** ở đây nói đến những phần mềm, ứng dụng ở mức thấp (_low-level_) trong hệ thống, có khả năng thay đổi linh hoạt để phù hợp với phần cứng. Chúng tương tác với tất cả ứng dụng và hoạt động trong chế độ **user mode**, cho phép các quá trình khác – hay còn gọi là **server**, nhận thông tin từ các thành phần khác qua **inter-process communication (IPC)**.
 ## 2.   Các loại kernel
 - **Kernel** được chia ra làm 3 loại là : _**monolithic**_, _**microkernel**_, và _**hybrid**_
 - **Linux** sử dụng **kernel monolithic** trong khi **OS X (XNU)** và **Windows 7** sử dụng **kernel hybrid**.
 ## 3. Microkernel
 - **Microkernel** có đầy đủ các tính năng cần thiết để quản lý bộ vi xử lý, bộ nhớ và IPC. Có rất nhiều thứ khác trong máy tính có thể được nhìn thấy, tiếp xúc và quản lý trong chế độ người dùng
 - Ưu điểm:
	 + Tính linh hoạt cao
	 + Bảo mật
	 + Sử dụng ít footprint cài đặt và lưu trữ
- Nhược điểm: 
	+ Phần cứng đôi khi “khó hiểu” hơn thông qua hệ thống driver  
	+ Phần cứng hoạt động dưới mức hiệu suất thông thường vì các trình điều khiển ở trong chế độ user mode  
	+  Các tiến trình phải chờ đợi để được nhận thông tin  
	+  Các tiến trình không thể truy cập tới những ứng dụng khác mà không phải chờ đợi
## 4. Monolithic Kernel
- Với Monolithic thì khác, chúng có chức năng bao quát rộng hơn so với microkernel, không chỉ tham gia quản lý bộ vi xử lý, bộ nhớ, IRC, chúng còn can thiệp vào trình điều khiển driver, tính năng điều phối file hệ thống, các giao tiếp qua lại giữa server... Monolithic tốt hơn khi truy cập tới phần cứng và đa tác vụ, bởi vì nếu 1 chương trình muốn thu thập thông tin từ bộ nhớ và các tiến trình khác, chúng cần có quyền truy cập trực tiếp và không phải chờ đợi các tác vụ khác kết thúc. Nhưng đồng thời, chúng cũng là nguyên nhân gây ra sự bất ổn vì nhiều chương trình chạy trong chế độ supervisor mode hơn, chỉ cần 1 sự cố nhỏ cũng khiến cho cả hệ thống mất ổn định.
- Ưu điểm : 
	+ Truy cập trực tiếp đến các phần cứng  
	+ Dễ dàng xử lý các tín hiệu và liên lạc giữa nhiều thành phần với nhau  
	+  Nếu được hỗ trợ đầy đủ, hệ thống phần cứng sẽ không cần cài đặt thêm driver cũng như phần mềm khác  
	+  Quá trình xử lý và tương tác nhanh hơn vì không cần phải chờ đợi
- Nhược điểm :
	+ Tiêu tốn nhiều footprint cài đặt và lưu trữ  
	+  Tính bảo mật kém hơn vì tất cả đều hoạt động trong chế độ giám sát - supervisor mode
## 5. Hybrid Kernel
- Khác với 2 loại kernel trên, Hybrid có khả năng chọn lựa và quyết định những ứng dụng nào được phép chạy trong chế độ user hoặc supervisor. Thông thường, những thứ như driver và file hệ thống I/O sẽ hoạt động trong chế độ user mode trong khi IPC và các gói tín hiệu từ server được giữ lại trong chế độ supervisor. Tính năng này thực sự rất có ích vì chúng đảm bảo tính hiệu quả của hệ thống, phân phối và điều chỉnh công việc phù hợp, dễ quản lý.
- Ưu điểm : 
	+ Các nhà phát triển có thể chọn và phân loại những ứng dụng nào sẽ chạy trong chế độ thích hợp  
	+ Sử dụng ít footprint hơn so với monolithic kernel  
	+  Có tính linh hoạt và cơ động cao nhất
- Nhược điểm:
	+ Có thể bị bỏ lại trong quá trình gây treo hệ thống tương tự như với microkernel  
	+  Các trình điều khiển thiết bị phải được quản lý bởi người dùng
