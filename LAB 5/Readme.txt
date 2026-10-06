Họ tên: Võ Huỳnh Phúc Huy
MSSV: 1150080055
Lớp: 11_ĐH_THMT
Link video: https://youtu.be/b-rYdhOIzow
Môi trường: VMware Workstation, pfSense CE 2.7.2.

Mạng
Thiết bị	    Mạng	                IP
pfSense       WAN	Bridged	DHCP      (192.168.0.107)
pfSense       LAN	VMnet1 (Host-only) 10.0.0.1/8
Domain        Controller	VMnet1	   10.0.0.2/8
LAN-Test      (Ubuntu)	VMnet1	     10.0.0.3/8
Máy thật	    VMnet1	               10.0.0.100/8
VMnet1:       subnet                 10.0.0.0/255.0.0.0, tắt DHCP.

Đã làm
Tải ISO, kiểm tra SHA-256, giải nén.
Tạo VM pfSense (2 GB RAM, 2 vCPU, 20 GB, 3 card mạng) và cài đặt.
Đặt IP LAN 10.0.0.1/8, chạy Setup Wizard, WAN có IP.
Tắt 2 rule Default allow, Reset States, tạo rule nền tảng.
Tình huống 1: tạo 3 rule (Block ICMP, Pass DNS 53, Pass Web_Ports).
