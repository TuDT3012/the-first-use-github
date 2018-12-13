# Các bước của quy trình khởi động Linux - RHEL / CentOS 7
 
 **Systemd** (/ etc / systemd /) là sự thay thế của quá trình init (/ sbin / init), Hệ thống systemd và trình quản lý dịch vụ chịu trách nhiệm kiểm soát cách các dịch vụ được khởi động, dừng và quản lý khác trên các hệ thống Red Hat Enterprise Linux 7. Mặc dù quy trình systemd thay thế tiến trình init (hoàn toàn theo nghĩa đen, / sbin / init hiện là liên kết tượng trưng đến / usr / lib / systemd / systemd) để bắt đầu dịch vụ khi khởi động và thay đổi cấp độ chạy trong Linux 7, systemd cung cấp nhiều hơn kiểm soát hơn quá trình init và nó vẫn hỗ trợ các tập lệnh init hiện có.
 **Quá trình khởi động Red Hat Linux 7 có thể được chia thành các giai đoạn dưới đây.**
   
**1.BIOS  
2.MBR (Bản ghi khởi động chính)  
3.GRUB2 Bộ tải khởi động  
4.Kernel  
5.Systemd  
6.Runlevel-Target**
- Trên đây là các giai đoạn trên có liên quan đến quá trình khởi động Linux 7 khi hệ thống khởi động.
## 1. BIOS: 
- BIOS - Hệ thống đầu vào / đầu ra cơ bản là giao diện phần sụn không chỉ kiểm soát quá trình khởi động và còn cung cấp tất cả sự kiểm soát của giao diện cấp thấp cho các thiết bị ngoại vi đính kèm. Khi bạn bật nguồn hệ thống của mình, nó sẽ đọc tất cả các cài đặt của thiết bị và thực hiện quy trình POST (Tự kiểm tra khi bật nguồn) để nhận ra các thiết bị Phần cứng để kiểm tra và khởi tạo các thành phần Phần cứng của hệ thống. Sau khi quá trình POST thành công, nó sẽ tải MBR (Master Boot Record) cho quá trình khởi động tiếp theo.
## 2. MBR (Bản ghi khởi động chính):
- Bản ghi khởi động chính được đặt trong khu vực đầu tiên của Ổ cứng khởi động Linux và thông tin này được tải trước vào ROM (Bộ nhớ chỉ đọc) bằng BIOS.  
MBR chỉ có kích thước 512 byte và nó chứa các hướng dẫn mã máy để khởi động Hệ điều hành, nó được gọi là bộ tải khởi động, cùng với bảng phân vùng. Khi BIOS tìm và tải chương trình bộ tải khởi động (GRUB2) vào bộ nhớ (ROM) hoặc Ổ cứng, nó sẽ điều khiển quá trình khởi động vào nó. chỉ cần MBR (Master Boot Record) tải và thực thi bộ tải khởi động GRUB2.
## 3. GRUB2 (Grand Unified Bootloader 2 ) Bootloader:
- GRUB2 là chương trình bộ tải khởi động mặc định trong tất cả các phiên bản mới nhất như Red Hat / CentOS 7 và cả Ubuntu từ phiên bản 9.10. Nó đã được thay thế bởi bộ tải khởi động GRUB còn được gọi là di sản GRUB.  
Tệp cấu hình GRUB2 nằm trong /boot/grub2/grub.cfg và Nó được tạo tự động bởi grub2-mkconfig bằng các mẫu từ /etc/grub.d và cài đặt từ / etc / default / grub. Không khuyến nghị chỉnh sửa tệp cấu hình GRUB2.
- Bộ tải khởi động (GRUB2 cho RHEL 7) khởi động kernel RHEL 7 và đĩa RAM ban đầu (initrd). GRUB 2 được cài đặt trong khu vực khởi động của ổ cứng máy chủ của bạn và được cấu hình để tải kernel Linux và initramfs và initrd là một hệ thống tệp gốc ban đầu sẽ gắn kết trước hệ thống tệp gốc thực trên hệ thống Linux.
## 4. Kernel:
- Linux Kernel là lõi trung tâm của HĐH và nó là chương trình đầu tiên được tải trên hệ thống khởi động. Trong khi hệ thống khởi động hạt nhân tải tất cả các Mô-đun hạt nhân cần thiết và Ổ đĩa từ initrd.img để tải hệ thống xử lý đầu tiên của hệ thống trong Linux 7.
- Câu lệnh giúp chúng ta tìm  **ID** của tiến trình **Systemd**:
**[root @ techinformant grub2] # ps -ef | grep system**
## 5. Systemd:
- Quá trình Systemd là ID tiến trình đầu tiên (PID 1) chạy trên các hệ thống Linux 7, nó khởi tạo hệ thống và khởi chạy tất cả các dịch vụ đã được bắt đầu bởi quy trình init (/etc/init.d) truyền thống. Quá trình Systemd đọc tệp cấu hình của /etc/systemd/system/default.target , sau đó tải hệ điều hành của nó trong runlevel.target được nhắm mục tiêu.  
Điều này nói với systemd để bắt đầu mọi thứ trong /usr/lib/systemd/system/basic.target trước khi bắt đầu các dịch vụ đa người dùng khác.

## 6. Runlevel-Target:
- systemd sử dụng 'mục tiêu' thay vì runlevels. Theo mặc định, có hai mục tiêu chính:

**multi-user.target:** tương tự runlevel 3

**Graphics.target:** tương tự runlevel 5

+ Để xem mục tiêu mặc định hiện tại, hãy chạy:
**[ root @ techinformant ~] # systemctl get-default**
+ Để đặt mục tiêu mặc định: 
**[ root @ techinformant ~] # systemctl set-default Graphics.target**
## Danh sách mục tiêu trong Red Hat Linux 7.
**runlevel0.target -> poweroff.target**

**runlevel1.target -> cứu.target**

**runlevel2.target -> multi-user.target**

**runlevel3.target -> multi-user.target**

**runlevel4.target -> multi-user.target**

**runlevel5.target -> đồ họa.target**

**runlevel6.target -> restart.target**
