# LAB3 – Nhận diện và ứng phó các mối đe dọa an toàn thông tin

**Họ tên:** Võ Huỳnh Phúc Huy
**MSSV:** 1150080055
**Lớp:** ĐH_THMT
**Tên lab:** LAB3 – Identifying and Responding to Information Security Threats
**Năm học:** 2026–2027

## Phiên bản môi trường thực hành (khác tài liệu gốc)

> **Lưu ý quan trọng:** môi trường thực tế dùng **Windows 10** thay vì Windows 11 25H2 như tài liệu yêu cầu, theo **sự cho phép của giảng viên** do giới hạn ISO/phần cứng sẵn có.

| Thành phần | Phiên bản dùng thực tế | Ghi chú |
|---|---|---|
| Ảo hóa | VMware Workstation Pro 26H1 | Máy ảo `Win10`, mạng Host-only là mặc định; tạm chuyển NAT khi cần tải công cụ hoặc thực hiện TH5 |
| Máy ảo | Windows 10 Home, build **19045** | Khác Windows 11 25H2 build 26200.9445 — đã được giảng viên cho phép thay thế |
| Endpoint protection | Microsoft Defender Antivirus tích hợp Windows 10 | Real-time protection và Tamper Protection luôn bật |
| Shell | Windows PowerShell 5.1 | Mở bằng Run as administrator cho các bước cần quyền quản trị |
| Wireshark | 4.6.8 Stable + Npcap | Cài từ file cài đặt tải trực tiếp (không dùng winget vì Windows 10 không có sẵn) |
| Python | 3.14.7 | Cài từ trình cài đặt chính thức python.org |
| Gói dữ liệu bài lab | `LAB3_Threats_Assets.zip` do giảng viên cung cấp | SHA-256 thực tế: `ea93627111fd093996d6e0460b3baee8182ccaa8293475b273c7d491af0f5337` (khác số `96236f95...` in trong tài liệu PDF — xem mục "Lỗi gặp phải" bên dưới) |

## Cách dùng môi trường

1. Mở VMware Workstation Pro, chọn tab máy ảo **Win10**.
2. Đăng nhập tài khoản cục bộ đã tạo sẵn trên máy ảo.
3. Toàn bộ dữ liệu, log, bằng chứng của bài lab nằm trong `C:\LAB3` trên máy ảo:
   - `C:\LAB3\Evidence` — file log, baseline, kết quả các lệnh PowerShell.
   - `C:\LAB3\Downloads` — file cài đặt, gói dữ liệu gốc.
   - `C:\LAB3\lab3_assets` — dữ liệu mẫu offline (CSV, script, template phishing) do giảng viên cung cấp.
4. Mạng máy ảo mặc định **Host-only** (cô lập, không có Internet); chỉ chuyển sang **NAT** tạm thời khi cần tải công cụ hoặc khi TH5 cần tạo traffic HTTPS ra ngoài.

## Các tình huống đã thực hiện

| Tình huống | Trạng thái | Ghi chú |
|---|---|---|
| Baseline hệ thống | **PASS** | `RealTimeProtectionEnabled = True`, firewall 3 profile đều Enabled |
| TH1 – Xác định tài sản/lỗ hổng/mối đe dọa/rủi ro | **PASS** | Risk register 5 dòng; 5 tình huống phân loại đúng 5 nhóm |
| TH2 – Mã độc (EICAR) | **PASS** | Defender phát hiện và cách ly (Quarantined) file EICAR, có trong Protection history |
| TH3 – Tấn công mật khẩu | **PASS** | Có 4624/4648 cho đăng nhập hợp lệ, 2×4625 cho lần sai; sau khi đổi mật khẩu, mật khẩu cũ không còn dùng được |



