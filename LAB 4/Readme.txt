LAB 4 - KHAO SAT VA DANH GIA BAO MAT MANG BANG NMAP
=====================================================

Ho ten: Vo Huynh Phuc Huy
MSSV: 1150080055
File bao cao: 11_DH_THMT-1150080055-VoHuynhPhucHuy.docx

MUC TIEU BAI LAB
-----------------
Dung Nmap tren Kali Linux de kiem ke host, cong, dich vu va rui ro co ban
cua mang Host-only ca nhan (192.168.220.0/24), gom: phat hien host dang
song, so sanh cac ky thuat quet TCP/UDP, nhan dien dich vu/he dieu hanh,
kiem tra 1 lo hong SMB bang NSE, xuat bang chung, va chung minh hieu qua
1 bien phap phong thu (before/after hardening).

MOI TRUONG THUC TE (khac tai lieu goc, da duoc giang vien cho phep)
---------------------------------------------------------------------
- Ao hoa      : VMware Workstation Pro 26H1 (thay VirtualBox)
- Mang        : Host-only VMware VMnet1, dai 192.168.220.0/24
                (thay 192.168.56.0/24 cua VirtualBox)
- "May that"  : dong vai tro boi may ao Win10 (192.168.220.129),
                co cai san Nmap 7.991 + Npcap + Zenmap
- Kali Linux  : may quet chinh, IP 192.168.220.131, Nmap 7.99 (co san)
- Metasploitable 2 (2.0.0): may dich, IP 192.168.220.130, chi noi Host-only
- Snapshot "Before-LAB4" da tao cho Kali va Metasploitable2 truoc khi lam

DA LAM DUOC
------------
[x] Cai Nmap + Npcap + Zenmap tren may dong vai tro "may that" (Win10)
[x] Kiem tra IP Host-only cua Kali va Metasploitable2
[x] Kiem tra ket noi (ping) giua cac may truoc khi quet
[x] Nhiem vu 1 - Host discovery (-sn): phat hien 5 host trong /24
[x] TCP Connect scan (-sT) va SYN scan (-sS): 23 open / 977 closed / 0 filtered
[x] FIN / Xmas / NULL scan: ca 3 deu ra open|filtered cho 23 cong da biet mo
[x] ACK scan (-sA): toan bo 1000 cong unfiltered (khong co firewall chan)
[x] UDP scan (20 cong pho bien): 2 open, 3 open|filtered, 15 closed
[x] Version detection (-sV): liet ke day du 23 dich vu + phien ban
[x] OS detection / Aggressive scan (-A): xac dinh Linux 2.6.9 - 2.6.33
[x] NSE smb-vuln-ms17-010: chay tren Metasploitable2 va Win10
[x] Xuat ket qua -oA (.nmap/.xml/.gnmap) va lay ra ngoai may that
[x] Da tra loi day du 10 cau hoi phan tich (muc 10) dua tren du lieu that
[x] Da bat dau tinh huong hardening: quet "Before" cong 21 (vsftpd 2.3.4, open)



