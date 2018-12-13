# Làm việc với thư mục trên CentOS


 Chú ý là trên hệ điều hành linux có phân biệt hoa thường, vì thế khi di chuyển, tạo file, thư mục trên CentOS … bạn cần chú ý hoa thường nhé.

Tuy sử dụng sFTP Client bạn có thể quản lý file, thư mục trên Centos dễ dàng, trực quan nhưng có những trường bạn vẫn phải sửa dụng dòng lệnh, bài viết này sẽ giúp bạn hiểu những dòng lệnh quản lý folder đơn giản và thường dùng. 
### 1. Di chuyển đến một thư mục khác
**cd /home/(thư mục cần đến)**
- để trở lại ta dùng câu lệnh **cd**
- Trở về thư mục gốc của server : **cd /**
### 2. Xem thư mục, file ls
 -   ls : hiển thị file, thư mục (không hiển thị file ẩn)
-   ls -a : Xem tất cả file, thư mục kể cả file ẩn
-   ls -al : xem tất cả file, thư mục ẩn và thông tin chi tiết.
### 3. Tạo, xóa, copy, di chuyển thư mục trên Centos

**Tạo thư mục**

Để đơn giản, muốn tạo thư mục moz trong thư mục /home, mình sẽ di chuyển đến thư mục home trước rồi dùng lệnh : **mkdir [thư mục cần tạo]**
**Xóa thư mục**
sử dụng câu lệnh : **rm  -rf  [tên  thư  mục]:  Xóa  tất  cả  thư  mục**
**Di chuyển thư mục**
sử dụng câu lệnh : **mv  [thư  mục  chuyển]  [thư  mục  đến]**
**Copy thư mục**
sử dụng câu lệnh :  **cp  -r  [thư  mục  copy]  [thư  mục  mới]**
## các câu lệnh hiện thị thư mục trong centos
### 1. Các câu lệnh hiện thị thông tin file và thư mục


![enter image description here](https://lh3.googleusercontent.com/B6f9u3L8khMgBpk-oCwl5LN2-GZn-zR06AS3mjp4qRQAzYQAgI57JPxqHr0wyAK35GLIDABjXZmI)


### 2. các câu lệnh thao tác file với thư mục 
![enter image description here](https://lh3.googleusercontent.com/58e_wJ4siNIsP1W96fo2EbDNCbMZtWZ9NBqkmNlsNW5M5p0Pfby0ySz67MrSaS1pefyaMBwP711G)
### 3. các câu lệnh sử lý nội dung file 
![enter image description here](https://lh3.googleusercontent.com/g_pdaK8AV-kRMFJZAA7Is2PvIQpJARcOPOJYZ2d70uy3ExSP4C88I88HnNgQguuiVEtSOPimhXKH)
### 4. lệnh nén và giải nén trong centos
![enter image description here](https://lh3.googleusercontent.com/uRA_CiVTlxH7uAQrjdXaTAnThIl2TbctJePcykOJs44oQklDZVy54sYOUSz-1xLPTOK1oBjyIwqc)
