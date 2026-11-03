Họ tên: Võ Huỳnh Phúc Huy
MSSV: 1150080055
Lớp: 11_ĐH_THMT
Link video: Huy Võ Huỳnh Phúc - YouTube

LAB 10 — Remote DNS Cache Poisoning — Tóm tắt
Môi trường: VMware. ATTACKER = Ubuntu + python3-dnspython (thay Kali, vì bài cấm sniff). Kế thừa LAB 9.

Máy & truy cập (SSH qua card NAT)
Máy	IP lab	SSH	Vai trò
pfSense	DNSLAB 10.9.0.1 + ATTACKNET 10.10.0.1	WebGUI 192.168.56.254	firewall
DNS-SERVER (web-proxy)	10.9.0.10	192.168.250.51	BIND9 baseline / vuln_resolver (attack)
VICTIM	10.9.0.100	192.168.250.50	client
ATTACKER	10.10.0.200	192.168.250.52	evil_dns + kaminsky
DMZ-WEB (AUTH-DNS)	172.16.6.20 / .10	192.168.250.53	auth_dns_relay
Card guest: ens192 = mạng lab, ens160 = NAT (SSH). User vohuynhphuchuy.
Domain: www.example.lab10.test → baseline 172.16.6.10, sau poison → 10.10.0.200.
