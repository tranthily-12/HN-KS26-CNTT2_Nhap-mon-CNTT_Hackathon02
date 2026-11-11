# BÀI LÀM – HACKATHON 02

- **Mã đề:** 09
- **Họ tên:** Trần Thị Lý
- **Lớp:** HN-KS26-CNTT2
- **Link repository:**
- **Hệ điều hành (Windows/macOS):** Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
# pwd
# ls -Force
# mv .\noi_quy_thanh_vien.txt .\docs\
# mkdir backup
# cp .\data\thue_cho_thang_9.xlsx .\backup\
# rm .\temp_909.tmp
# cd .\logs\
# ls -Force
# cd ..
# Get-ChildItem -Recurse -Force
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
Directory: C:\Users\fpt yen thanh\Downloads\starter-kit
    (2)\starter-kit\coworking-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   1:35 PM                backup
d-----        11/11/2026   1:34 PM                data
d-----        11/11/2026   1:35 PM                docs
d-----        11/11/2026   1:32 PM                evidence
d-----        11/11/2026   1:34 PM                logs
d-----        11/11/2026   1:31 PM                web
------         11/3/2026   7:08 AM             72 .env
-a----         11/3/2026   7:08 AM           2409 bai_lam.md


    Directory: C:\Users\fpt yen thanh\Downloads\starter-kit
    (2)\starter-kit\coworking-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM           6162 thue_cho_than
                                                  g_9.xlsx


    Directory: C:\Users\fpt yen thanh\Downloads\starter-kit
    (2)\starter-kit\coworking-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM           6162 thue_cho_than
                                                  g_9.xlsx


    Directory: C:\Users\fpt yen thanh\Downloads\starter-kit
    (2)\starter-kit\coworking-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM            146 noi_quy_thanh
                                                  _vien.txt


    Directory: C:\Users\fpt yen thanh\Downloads\starter-kit
    (2)\starter-kit\coworking-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM            991 member.log


    Directory: C:\Users\fpt yen thanh\Downloads\starter-kit
    (2)\starter-kit\coworking-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   1:31 PM                images
------         11/3/2026   7:08 AM            605 app.js
------         11/3/2026   7:08 AM            543 index.html
------         11/3/2026   7:08 AM            460 style.css


    Directory: C:\Users\fpt yen thanh\Downloads\starter-kit
    (2)\starter-kit\coworking-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
------         11/3/2026   7:08 AM           3069 logo-coworkhu
                                                  b.png
```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
# Get-Content .\logs\member.log | Select-String "status=500" > logs/loi_500.txt

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
2026-09-28 08:10:39 POST /api/dat-cho status=500
2026-09-28 08:12:50 POST /api/dat-cho status=500


```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
# Get-Content .\logs\member.log | Select-String "status=404"| Measure-Object

```

```text
Count    : 4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
# ni tong_hop.ps1
# Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
# .\tong_hop.ps1
```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO SU CO WEBSITE ===

2026-09-28 08:28:45 GET /images/phong-hop-3.jpg status=404
2026-09-28 08:41:40 GET /goi-cu status=404
2026-09-28 08:49:13 GET /images/phong-hop-3.jpg status=404
2026-09-28 08:59:46 GET /images/phong-hop-3.jpg status=404




Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 


```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | Network | logo.png | Mở web/index.html bằng VS Code, tại dòng 10 có đoạn src="image/logo.png";thay logo.png bằng logo-coworkhub.png |
| 2 | Console | Uncaught ReferenceError: hienThiBangThue is not defined | Mở web/app.js bằng VS Code, tại dòng 18, đổi hienThiBangThue thành hienThiGoiThue  |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** Tớ mở trình duyệt Chrome để kiểm tra web/index.html bằng DevTools(F12)
- **Expected:** Hiển thị bảng giá thuê đẩy đủ
- **Actual:** Không hiển thị bảng giá do lỗi ở tab Console 
- **Log:** Uncaught ReferenceError: hienThiBangThue is not defined

### Câu tìm kiếm Google

```text
site:stackoverflow.com "Uncaught ReferenceError: hienThiBangThue is not defined"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/thue_cho_thang_9.xlsx`, không cần ghi vào đây.
