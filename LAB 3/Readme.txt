# LAB3 – Nhận diện và ứng phó các mối đe dọa an toàn thông tin

**Họ tên:** Võ Huỳnh Phúc Huy
**MSSV:** 1150080055
**Lớp:** ĐH_THMT
**Lab:** LAB3 – Identifying and Responding to Information Security Threats

## Môi trường

Dùng **Windows 10 Home** (build 19045) . VMware Workstation Pro 26H1, máy ảo `Win10`, mạng mặc định **Host-only**, chỉ chuyển NAT tạm thời khi cần Internet (tải công cụ, TH5).

Công cụ: Python 3.14.7, Wireshark 4.6.8 + Npcap, Sysmon 15.22, Autoruns 14.3, Process Explorer 17.14, Microsoft Defender (tích hợp sẵn).

## Kết quả các tình huống

| TH | Nội dung | Kết quả |
|---|---|---|
| Baseline | Defender + Firewall đang bật | PASS |
| TH1 | Risk register 5 tài sản, phân loại 5 tình huống | PASS |
| TH2 | EICAR bị Defender phát hiện và cách ly | PASS |
| TH3 | Đăng nhập đúng/sai (4624/4648/4625), đổi mật khẩu vô hiệu credential cũ | PASS |
| TH4 | Phát hiện persistence (`LAB3_Run_Demo`, `LAB3_Persistence_Demo`) và listener 8080 qua Sysmon/Autoruns/Process Explorer | PASS |
| TH5 | So sánh HTTP (đọc được nội dung) và HTTPS (chỉ thấy metadata) qua Wireshark | PASS |
| TH6 | `local_load_test.py` (DoS cục bộ), phân tích `ddos_sample.csv`, `mailbomb_sample.csv` | PASS |
| TH7 | Nhận diện 5 chỉ dấu phishing, phân loại 6 case Social Engineering | PASS |

Toàn bộ 7/7 tình huống đã hoàn thành.

## Bằng chứng

Toàn bộ log, ảnh chụp và `evidence_sha256.csv` nằm trong `C:\LAB3\Evidence` trên máy ảo.
