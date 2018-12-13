SeLinux là gì
==


## **1. SELinux là gì?**

**SELinux**  (**Security-Enhanced Linux**) là một mô đun bảo mật ở nhân của Linux, cung cấp cơ chế hỗ trợ các chính sách bảo mật kiểm soát truy cập (access control) , bao gồm các điều khiển truy nhập bắt buộc theo phong cách Bộ Quốc phòng Hoa Kỳ (MAC).

## 2. SELinux Modes

SELinux có 3 chế độ hoạt động cơ bản, trong đó  **Enforcing**  là chế độ mặc định khi cài đặt. Tuy nhiên, có một bộ định tính bổ sung của các mục tiêu hoặc các ml kiểm soát cách các quy tắc SELinux phổ biến được áp dụng, với mục tiêu là mức độ ít nghiêm ngặt hơn.

-   **Enforcing**: Chế độ mặc định sẽ cho phép và thực thi chính sách bảo mật SELinux trên hệ thống, từ chối các hành động truy cập và ghi nhật ký
-   **Permissive**: Trong chế độ Permissive, SELinux được kích hoạt nhưng sẽ không thực thi chính sách bảo mật, chỉ cảnh báo và ghi lại các hành động. Chế độ Permissive hữu ích cho việc khắc phục sự cố SELinux
-   **Disabled**: SELinux bị vô hiệu hóa hoặc bị tắt đi.
## 3. vì sao mọi người thường tắt SELinux đi ?
- **SELinux** gây chậm cho hệ thống, và một số ứng dụng thì sẽ trở nên khó cài đặt hơn
