
LAB 6 — pfSense + Active Directory + Access Policies
Trạng thái ngày 17/10/2026.

Họ tên: Võ Huỳnh Phúc Huy
MSSV: 1150080055
Lớp: 11_ĐH_THMT

Bài thực hành được triển khai trên VMware Workstation thay vì VirtualBox như tài liệu, với bốn mạng ảo tương đương: VMnet8 làm WAN dải 192.168.250.0/24, VMnet1 làm MGMT dải 192.168.56.0/24 đã tắt DHCP, và hai LAN Segment tên Lab6-lan và Lab6-dmz thay cho Internal Network.

Năm máy ảo đã dựng xong và chạy đúng. pfSense được đưa về mặc định bằng factory reset để loại bỏ cấu hình còn sót của LAB 5, sau đó gán bốn interface theo MAC address: WAN lấy DHCP, MGMT 192.168.56.254, LAN 10.6.0.1 và DMZ 172.16.6.1, tất cả đều tắt DHCP server. WebGUI truy cập từ máy thật qua địa chỉ quản trị, đăng nhập admin với mật khẩu mặc định pfsense.

DC01 mang địa chỉ 10.6.0.10, đã cài AD DS và DNS, tạo forest lab6.test cùng OU LAB6-Users chứa hai tài khoản sv_a và sv_b, và một service account svc_pfsense_ldap đặt trong container Users chỉ thuộc nhóm Domain Users. DMZ-WEB là máy Ubuntu Server chạy Nginx, mang bốn địa chỉ 172.16.6.10, .20, .30 và .40 trên card ens192 để mô phỏng bốn nhóm website. Hai máy trạm Client-A và Client-B lần lượt dùng 10.6.0.21 và 10.6.0.22.

Tám alias và ba schedule đã tạo đủ theo tài liệu. Bốn kịch bản chính sách đầu tiên đã triển khai và kiểm thử, toàn bộ chín phép thử đều cho kết quả đúng như dự đoán: Client-A bị chặn JOB_SITE nhưng vào được GENERAL_SITE, cả hai máy đều bị chặn RESTRICTED_SITE, Client-B chỉ vào được SOCIAL_SITE khi schedule đang hiệu lực, và ngoài giờ hành chính thì mọi lưu lượng web cũng bị rule chặn cuối ruleset loại bỏ.

Ruleset trên tab LAN
Thứ tự rule là một phần của chính sách, không được xáo trộn. Sau rule Anti-Lockout mặc định là: chặn CLIENT_A tới JOB_SITE có bật log, chặn POLICY_CLIENTS tới RESTRICTED_SITE có bật log, cho phép CLIENT_B tới SOCIAL_SITE kèm schedule LUNCH_WINDOW, chặn CLIENT_B tới SOCIAL_SITE, cho phép CLIENT_A và POLICY_CLIENTS tới GENERAL_SITE, cho phép POLICY_CLIENTS đi bất kỳ đâu trên WEB_PORTS kèm schedule WORK_HOURS, và cuối cùng là rule chặn POLICY_CLIENTS đi bất kỳ đâu có bật log.

Hai rule Default allow LAN to any của IPv4 và IPv6 bắt buộc phải tắt, nếu không rule chặn cuối cùng sẽ không bao giờ được xét tới và kịch bản 4 sẽ ra kết quả sai.

Khi kiểm thử phải Reset States trước mỗi lần, vì pfSense là firewall stateful nên kết nối cũ vẫn đi theo state cũ mà không duyệt lại ruleset.
