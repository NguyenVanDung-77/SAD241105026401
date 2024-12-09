



## 1. Sơ đồ Lớp (Class Diagram)
![Sơ đồ](https://www.planttext.com/api/plantuml/png/X5HBJiCm5Dpd55wcYroWGgWgHQKRLD4YrYP-0gkE7TaEgWMSZ0L7uWhOYUtMjGLP9JD-Rzvduf-lxuNIMEgXOrNBi59eYuqKZEsCqj2XzmgDpneuIAp1im_G2wdhcMTlC6i7PkaTPbXIK97PuJSNqxv2Ux3WP-LLRhkU2GFW1Hf4kOxWXdXGQKdv2xh77QJ8LYYggU15VLFFveY8uPd1IN1FEsYn98bW0ADWiOgLJUnEeYSX3-x3uvC4kXE3L8u2SbdENcZCHhvKKfXBKb80_ox9Iq_jfjWU7rDWAVYWyZNwbSpzICycXO-X0JlXw81JK_XO-zHgr2-qDchceIFyRx0pbrsla2PcS3QgWMkgJN3MOqzinWjm1GmoS0rwQJQafiIAJLHkn8AeZGli56ytCUO8w5bn0QgZiQ7hP_ckopA1JMK2MlgLedTw_p9gdMM_-cYQGdFPaRomAhq1ckRwr71EXL-eGCNw2r69nme79jCkW1DtC_q2003__mC0)
Sơ đồ này mô tả các lớp chính trong hệ thống Payroll System và cách chúng tương tác với nhau:

- **PayrollSystem**:
  - Là lớp trung tâm quản lý hệ thống bảng lương.
  - Chứa các phương thức chính như GeneratePayrollReport, CalculateSalaries, và SavePaycheck.
  - Phụ thuộc vào các lớp khác như Employee, Timecard, TaxCalculation, và Bonus để hoàn tất quá trình xử lý lương.

- **Employee**:
  - Đại diện cho thông tin của nhân viên.
  - Chứa các thuộc tính cơ bản như EmployeeId, Name, và Position.
  - Phương thức CalculateSalary dùng để tính lương cơ bản.

- **Timecard**:
  - Quản lý giờ làm việc của nhân viên trong ngày.
  - Chứa thông tin như TimecardId, EmployeeId, và HoursWorked.
  - Phương thức CalculateTotalHours tính tổng số giờ làm việc từ nhiều bản chấm công.

- **Paycheck**:
  - Đại diện cho kết quả lương của một nhân viên sau khi tính toán.
  - Gồm các thuộc tính như Salary, Tax, và Bonus.

- **TaxCalculation và Bonus**:
  - **TaxCalculation**: Tính thuế dựa trên mức lương.
  - **Bonus**: Tính thưởng dựa trên chính sách công ty.

- **Repository**:
  - Lớp cơ sở thực hiện các thao tác lưu trữ (CRUD).
    - **EmployeeRepository**: Quản lý lưu trữ thông tin nhân viên.
    - **PaycheckRepository**: Lưu trữ thông tin phiếu lương.

## 2. Sơ đồ Tương Tác Hệ Thống Con (Sequence Diagram)
![Sơ đồ](https://www.planttext.com/api/plantuml/png/P99BReCm48RtFiKe-ro0HHM2QBkeMWHKPJjoHWgAiQazhiBPkkYHUeKQar18MCx_OEQJVxz_TexHik-KGCd6mhiZA_emQcNResRO53XOerGrEAPk0-YWgDQElEkL6OXAwerhGyiGRNcvjjLjHnBj8OfrTYFYEKCblK9kZPuiQRFsx8tsBahxjzUx9UMHvEbcXQ8KOhm8jWzXwmHA-lJa62utmHDfil6FegX6KrucOSXmFGbUMiSYBs5xQLWBofWU7WEs7ELnrWI4R-ghiwdlsNZhuCFO4nsYN6TpPMqOrUHO9jCcWIiIWi1dogNDVn3Fa7R6Qrxa0ffbBZABSX3cP9pUPujmVOLV15USWlJXGcR4E09aR_NCRyHjMUo2RNn2Vm000F__0m00
)

1. Người dùng (User) gửi yêu cầu tạo bảng lương.
2. **PayrollSystem**:
   - Gửi yêu cầu đến **EmployeeRepository** để lấy danh sách nhân viên.
   - Lấy dữ liệu chấm công từ **Timecard** cho từng nhân viên.
   - Tính thuế với **TaxCalculation** và thưởng với **Bonus**.
   - Lưu thông tin phiếu lương vào **PaycheckRepository**.
3. Sau khi hoàn tất, hệ thống trả về báo cáo lương cho người dùng.



## 3. Mối Quan Hệ Phụ Thuộc Giữa Các Hệ Thống Con
![Sơ dồ](https://www.planttext.com/api/plantuml/png/T99D2i8m48NtEKNelbUGghWKHBt0a0vQcf-IfD0Wdio5H_8ALgLjnZRPPRvvZtd3l1xFmdcmlbMIDI1gk23F3X2iaV8Kd4ULyHlZ_HCIdEC4iJkRH3lLI1CGzw3xlqBjgNBW2wKZDiPLtjX07C-LGW6sJ3aEd8gWM-joOtJhjY15Ay5NHly9eOjO1BuoOjVd5LSKTMg6WI-KQ2goE9xdgsaXQHHPp9l6-0k81fmt_8BEwsESD8fcOWNgydCvRm000F__0m00)
Sơ đồ này tổ chức các hệ thống con thành các nhóm chức năng và chỉ rõ mối quan hệ giữa chúng:

- **PayrollSystem**:
  - Hệ thống trung tâm xử lý bảng lương. Nó phụ thuộc vào các hệ thống con khác để hoàn thành công việc.
- **EmployeeManagement**:
  - Chứa các lớp **Employee** và **EmployeeRepository**.
  - Cung cấp thông tin nhân viên cần thiết cho việc tính lương.
- **TimecardManagement**:
  - Quản lý thông tin về giờ làm việc thông qua lớp **Timecard**.
- **TaxAndBonusCalculation**:
  - Xử lý các yếu tố về thuế và thưởng với các lớp **TaxCalculation** và **Bonus**.
- **PaycheckManagement**:
  - Lưu trữ và quản lý thông tin phiếu lương với các lớp **Paycheck** và **PaycheckRepository**.

Mối quan hệ:
- **PayrollSystem** phụ thuộc vào tất cả các hệ thống con vì mỗi hệ thống con đảm nhận một phần công việc.
- Sự phân chia rõ ràng giúp dễ bảo trì và mở rộng hệ thống.

