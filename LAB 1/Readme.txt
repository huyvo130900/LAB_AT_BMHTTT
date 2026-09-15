LAB 1 — Bắt gói tin Telnet - SSH
Thông tin sinh viên
- Họ và tên:Võ Huỳnh Phúc Huy 
- Mã số sinh viên: 1150080055
- Lớp:11_ĐH_THMT
- Tên bài Lab: Lab 1 - Bắt gói tin Telnet - SSH

Nội dung đã thực hiện
Dựng mô hình mạng 4 máy trên VirtualBox (Host-only Network 192.168.56.0/24): Windows 10 (Client), Windows Server 2022 (Server SSH), Ubuntu Server 24.04 (Server Telnet), máy thật Win11 (Attacker chạy Wireshark). Cấu hình dịch vụ Telnet/SSH, tạo tài khoản thử nghiệm, bắt và phân tích gói tin 2 giao thức, so sánh mức độ bảo mật, demo xác thực bằng public-key.

 Kết quả thực hiện
- Telnet: đọc được plaintext username/password/lệnh gõ qua Follow TCP Stream.
- SSH: chỉ thấy metadata (IP, port, thời điểm...), không đọc được nội dung do đã mã hoá.
- Xác nhận thực nghiệm: cần bật Promiscuous Mode mới bắt được traffic unicast từ máy Attacker.

Lưu ý 
Windows Server 2022 không còn hỗ trợ cài Telnet Server nên dùng Ubuntu Server thay thế cho vai trò này; SSH vẫn dùng OpenSSH có sẵn trên Windows Server 2022. Cần bật Promiscuous Mode = Allow All trên các VM để Attacker bắt được traffic.