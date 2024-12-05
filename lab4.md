# Hệ thống Payroll System

## 1. Các lớp và thuộc tính/phương thức của chúng

![Sơ đồ Lớp](https://www.planttext.com/api/plantuml/png/T5DBJiCm4Dtd55wcYrm0eQf0aQW4KjKWiPuwezQgFvNj82B4oLXm9Aw0xTWEZjfLudblPjxyVhz_LiQ2jhtW5ULW3Dd2e1NdxM0i2l9P4T8G56Uk1iHdPYov8Vvp-nXjoy0umq2FI4__6Tje6naMFXw0qvw3LTfHNgStKp9GzahsvWKa7D0pxlspSWWXD38nggiN3dzNh0le0INg4Gm9wwJNaP9Cxv3mwgkAnIOqrYb1U9_MQYOFHUMRTMdVWy4MEEZ1sTUgttESAHtHsZA157JdAuw_Yyab2qdOhE7pj4VLQ_Ecz0bzG2Rjc5GZLRfxyc0TA2EOcvJJf0x4D6PMGPnJQGXJAKqIxSNYqo1sU5RQXY55yLEXnTYZ3fTpvzokjTBvr4nI9IR6fHw6VOaHW-WxeNffhqKDz6khCiKkxw5fbfbNvUtnrZJ12mvvxtBxWqDv00KshluAPUSEymy00F__0m00)

### Giải thích:
- **PayrollSystem**: Lớp trung tâm quản lý hệ thống bảng lương.
- **Employee**: Đại diện cho nhân viên.
- **Timecard**: Quản lý giờ làm việc của nhân viên.
- **Paycheck**: Kết quả cuối cùng sau tính toán lương.
- **TaxCalculation** và **Bonus**: Xử lý các yếu tố liên quan đến thuế và thưởng.

---

## 2. Đơn giản hóa sơ đồ chuỗi tương tác

![Sơ đồ Chuỗi Tương Tác](https://www.planttext.com/api/plantuml/png/T95B2i8m48RtEKMM5VG2BaHyx0Nr06CwQ32FaaobFPiBZ-GLZ6bJ6gdB_8_Xcydx-Lfx0aUrLWm4MSVF7XshWYI5hC0GFq3hh5B7rXFgpDdhIjaMCHDFKgC0L_xE43SKzpm9pHQKg1MGj2QpDjRKdh4l2r-iSWI-vAAlOMyKCvP7GYV1XVWLARrsG32LJjHTEht-fZFoCL1m2cc4rJXHYrkDqr4ei6URQAIxHIo3hbivIaDjpWcQERzyPyKHNIEqu_cMl4Gb7-Y6ueojqPJXnpy0003__mC0)

### Giải thích:
1. Người dùng (User) khởi tạo việc tính toán lương.
2. **PayrollSystem** lấy thông tin từ **Employee** và **Timecard**.
3. Tính thuế và thưởng thông qua **TaxCalculation** và **Bonus**.
4. Kết quả được ghi lại trong **Paycheck** và gửi đến người dùng.

---

## 3. Định nghĩa hành vi persistence-related

![Sơ đồ Persistence](https://www.planttext.com/api/plantuml/png/X5913e8m4Bpt5Jt2WGyO3yRemPD6Nr3fYjL22Lr86lLb7doINx0WLP2gFMrsPdTcDhrVRnEDhC0obIIMJ6kwXbnfWQemz4IeVPfL44260WqTqUNs0366jggKu0sXp3d3tnGE4lvGTYBZKxFWWU2slS52P4duef8BQVsjc2cKb1kZ4LAlsPOnOyY2lCkssthJFVq4i3iOVfBV3kPfBfK1y8exC82si7jSRv3N0RxS3kibZ_SG7x-5Ri0wSLCy_JVbGDS1Fbs7rReTfV4vYhxTVi0RNiYtwYCCcK36wt_u0000__y30000)

### Giải thích:
- **Repository**: Lớp cơ bản hỗ trợ lưu trữ, cập nhật, và tìm kiếm các thực thể.
- Các lớp con:
  - **PayrollSystemRepository**
  - **EmployeeRepository**
  - **PaycheckRepository**

---

## 4. Phân tích lớp và bản đồ cơ chế kiến trúc từ Use-Case

![Sơ đồ Kiến Trúc](https://www.planttext.com/api/plantuml/png/T56xRW8n4Epz5LicHPJ-YeWGoXGyyWCRtufOCLxYNPyu8RwCWa_Y5_1PSBeZOiiPp-pE-7myJKGnQjfuiqNxYsk2UIIXeAYE0-mDWFKe0XySDBBt50lOpG-6sjEI_XA9FZr31GsxEfC7Sp2ztpI92oJooMjd1uPpR3k_5SN6MUfDBNgRF2fT-R5lh_x2tKDbvefgnkdRqrWtvP3aeRAmzzf1bXaglbkRq_mFigGjYrEERUyhsD3m_cuyOrsmM_vMb3QtHQFoNzxkoglWMhOPu_dXuB8A5ebY-xhAsmjk9XJgxeil0000__y30000)

### Giải thích:
- Hệ thống chia thành 3 lớp:
  - **Presentation Layer**: Xử lý giao diện.
  - **Business Logic Layer**: Thực hiện logic nghiệp vụ.
  - **Data Access Layer**: Giao tiếp cơ sở dữ liệu.

---

## 5. Cải thiện mô tả quy trình sự kiện

### Use-Case: **Generate Payroll Report**
1. Người dùng yêu cầu tạo báo cáo bảng lương.
2. Hệ thống lấy danh sách nhân viên từ cơ sở dữ liệu.
3. Tính lương, thuế, và thưởng cho từng nhân viên.
4. Tổng hợp dữ liệu và xuất báo cáo.

---

## 6. Thống nhất các lớp và subsystem

![Sơ đồ Subsystem](https://www.planttext.com/api/plantuml/png/R8z12i8m44NtEKKkq0kuaAAu5smFC4u73Pqa9JC1WtYoBdeaho1r4OIwVVz__l_lUMb58MdsR2R04Mvapr1IPBxagnHHylPfh4K6aIfzUQKdFt4iHBysl1EE5NJmE09ZPb0NGyM76BAObwdLlJfsMlvLTyuJGXfM-sPXq-otsPtjXSIq58RrtWS00F__0m00)

### Giải thích:
- Các lớp chính nằm trong **PayrollSubsystem**.
- **UtilitySubsystem** hỗ trợ tính toán giờ làm việc.

