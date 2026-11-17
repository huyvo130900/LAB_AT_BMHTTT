Họ tên: Võ Huỳnh Phúc Huy
MSSV: 1150080055
Lớp: 11_ĐH_THMT
Link video: Huy Võ Huỳnh Phúc - YouTube

1. Nội dung báo cáo

| Mục | Nội dung | Số ảnh |
|---|---|---|
| 2 | Kết nối SQL Server | 1 |
| 3 | Bài 2.1 — Mật mã DES | 4 |
| 4 | Bài 2.2 — Mật mã TripleDES (3DES) | 4 |

Tổng cộng **9 ảnh chụp màn hình** minh chứng kết quả chạy thật.

---

## 2. Kết nối SQL Server

Tạo cơ sở dữ liệu `LAB2_MaHoaHienDai` gồm hai bảng `dbo.app_users` và `dbo.crypto_history`,
tạo tài khoản `lab2_user`, cấp quyền đọc/ghi, rồi kiểm tra bằng form `frm_KetNoiSQL`.

| Tham số | Giá trị |
|---|---|
| Server | `127.0.0.1` |
| Port | `1433` |
| Database | `LAB2_MaHoaHienDai` |
| User | `lab2_user` |

**Kết quả:** `Kết nối thành công: Microsoft SQL Server 15.00.2000 - database LAB2_MaHoaHienDai`

> **Khác tài liệu:** hướng dẫn giả định SQL Server Express ở cổng `14333` và instance
> `localhost\SQLEXPRESS`. Máy thực hiện cài bản **Developer Edition dạng instance mặc định**,
> nên dùng `localhost` (không có `\SQLEXPRESS`) và cổng **`1433`**.

---

## 3. Bài 2.1 — Mật mã DES

**Thuật toán**

- Mã khối: khối 8 byte (64 bit), khóa 8 byte (thực dùng 56 bit).
- Chế độ **CBC** + **IV ngẫu nhiên 8 byte** + đệm **PKCS5**.
- Bản mã = `Base64( IV ‖ dữ liệu đã mã hóa )`; giải mã tự tách 8 byte đầu làm IV.
- IV sinh mới mỗi lần → **mã hóa cùng một câu hai lần ra hai bản mã khác nhau**, đây là kết quả đúng.

**Dữ liệu thử**

| Mục | Giá trị |
|---|---|
| Plaintext | `Xin chào Lab 2 - Mã hóa hiện đại!` |
| Key | `12345678` |
| Yêu cầu | `Decrypt(Encrypt(x)) = x` |

**Kết quả** — Hình 2 đến Hình 5: mã hóa, giải mã khôi phục đúng bản rõ,
Save File ra `des_ciphertext.txt`, Open File nạp lại bản mã.

---

## 4. Bài 2.2 — Mật mã TripleDES (3DES)

**Thuật toán**

- Chạy DES ba lần: mã hóa K1 → giải mã K2 → mã hóa K3.
- Khóa **24 byte** = K1 ‖ K2 ‖ K3, mỗi phần 8 byte; phải gõ đúng 24 ký tự **không dấu**.
- Khối vẫn 8 byte, vẫn CBC + IV 8 byte + đệm PKCS5 như DES. Chậm gấp ba lần DES.
- NIST đã ngừng khuyến nghị 3DES từ 2023 — chỉ dùng để học.

**Dữ liệu thử**

| Mục | Giá trị |
|---|---|
| Plaintext | `Xin chào Lab 2 - Mã hóa hiện đại!` |
| Key | `123456789012345678901234` |

**Kết quả** — Hình 6 đến Hình 9: Encrypt, Decrypt khôi phục đúng,
Save File ra `tripledes_ciphertext.txt`, Open File nạp lại bản mã.

