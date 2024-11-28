# Phân tích Ca sử dụng "Payroll"

## 1. Xác định các lớp phân tích
- **PayrollSystem**: Lớp quản lý hệ thống bảng lương, thực hiện các thao tác liên quan đến tính toán lương.
- **Employee**: Lớp đại diện cho nhân viên, chứa các thông tin như tên, ID, lương cơ bản, số giờ làm việc.
- **Timecard**: Lớp quản lý thời gian làm việc của nhân viên, ghi lại số giờ làm việc mỗi ngày.
- **Paycheck**: Lớp đại diện cho bảng lương của nhân viên, chứa thông tin chi tiết về lương, các khoản khấu trừ và thu nhập cuối cùng.
- **TaxCalculation**: Lớp tính toán thuế, dựa trên mức thu nhập của nhân viên.
- **Bonus**: Lớp quản lý các khoản thưởng cho nhân viên.

## 2. Nhiệm vụ từng lớp phân tích
- **PayrollSystem**: Tính toán lương của nhân viên, quản lý quá trình thanh toán và phát lương cho nhân viên.
- **Employee**: Cung cấp thông tin về nhân viên (tên, ID, mức lương cơ bản).
- **Timecard**: Ghi nhận thời gian làm việc của nhân viên và cung cấp dữ liệu cho quá trình tính toán lương.
- **Paycheck**: Xuất thông tin về bảng lương của nhân viên sau khi tính toán, bao gồm lương cơ bản, khấu trừ và thưởng.
- **TaxCalculation**: Tính toán các khoản thuế cần khấu trừ từ lương của nhân viên.
- **Bonus**: Quản lý và tính toán các khoản thưởng cho nhân viên.

## 3. Xác định thuộc tính và quan hệ giữa các lớp
- **PayrollSystem**: Thuộc tính `employeeList`, `paycheckList`, `taxCalculator`, `bonusList`. Quan hệ: liên kết với lớp Employee, Paycheck, TaxCalculation, và Bonus.
- **Employee**: Thuộc tính `name`, `employeeID`, `baseSalary`. Quan hệ: liên kết với lớp Timecard và Paycheck.
- **Timecard**: Thuộc tính `hoursWorked`, `employeeID`. Quan hệ: liên kết với lớp Employee.
- **Paycheck**: Thuộc tính `salary`, `tax`, `bonus`, `netSalary`. Quan hệ: liên kết với lớp Employee, TaxCalculation, và Bonus.
- **TaxCalculation**: Thuộc tính `taxRate`, `income`. Quan hệ: liên kết với lớp Paycheck.
- **Bonus**: Thuộc tính `bonusAmount`. Quan hệ: liên kết với lớp Paycheck.

## 4. Biểu đồ
![Biểu đồ lớp Payroll](https://www.planttext.com/api/plantuml/png/T5DBJiCm4Dtd55x2eXUmK5MWI5HYKP5AhAVEgBNgJsLF417YP2mu4bSWJkoqRaqMbZn-yzwRJtw_VnQUm56hLIKKUC_Mq3chLDrvGiq-AnO-r4TbEyGNwOcpSDuznT1yH1oX4tiKXpF4EeOYWk3Z4PHe5P1rd6rELsdD2DbQq_epXeTmJmBE2lG-shkvvUpTogRwggBlv2TPDg2HivgSDBkyYDMICsaeIeB76XIuZhF6jbk5Oto7b1YNI22L3vAHRXBTI8q2N9D4zxPr_isw0pOvNL6xrtWE2O4vWYVcrBp4x0iU-uxcWQ5_USWWbSipw80moLptCvzFij5BllPfEPaqmkgBc8YvsFEKwXj6crW7t_VQjeR-OHdWEK--gBFPV5g1mbEgi_1qiOZNW46xclPho8bphwOnbPbERoF90atJ_sf_0000__y30000)

## 5. Giải thích sơ đồ lớp
- **PayrollSystem** chịu trách nhiệm quản lý tất cả các yếu tố liên quan đến bảng lương của nhân viên, bao gồm nhân viên, bảng lương, thuế và thưởng.
- **Employee** chứa thông tin cơ bản của nhân viên và có quan hệ với lớp `Timecard` để ghi nhận số giờ làm việc của họ.
- **Timecard** ghi nhận số giờ làm việc của nhân viên, cung cấp dữ liệu cho lớp `PayrollSystem`.
- **Paycheck** là kết quả cuối cùng sau khi tính toán lương, thuế và thưởng. Nó được tạo ra từ dữ liệu trong lớp `Employee`, `TaxCalculation`, và `Bonus`.
- **TaxCalculation** tính toán thuế dựa trên thu nhập của nhân viên.
- **Bonus** tính toán các khoản thưởng.

---

# Phân tích Ca sử dụng "Generate Employee Reports"

## 1. Xác định các lớp phân tích
- **ReportGenerator**: Lớp tạo báo cáo về nhân viên.
- **Employee**: Lớp chứa thông tin của nhân viên.
- **PayrollSystem**: Lớp quản lý bảng lương và thông tin về lương của nhân viên.
- **Report**: Lớp đại diện cho báo cáo đã tạo ra, có thể là bảng lương hoặc các loại báo cáo khác.

## 2. Nhiệm vụ từng lớp phân tích
- **ReportGenerator**: Tạo các báo cáo cho hệ thống (báo cáo bảng lương, thông tin nhân viên, v.v.).
- **Employee**: Cung cấp thông tin cần thiết cho báo cáo (tên, ID, v.v.).
- **PayrollSystem**: Cung cấp thông tin về bảng lương của nhân viên.
- **Report**: Lưu trữ các dữ liệu báo cáo đã tạo ra.

## 3. Xác định thuộc tính và quan hệ giữa các lớp
- **ReportGenerator**: Thuộc tính `employeeList`, `payrollSystem`. Quan hệ: Liên kết với lớp Employee và PayrollSystem.
- **Employee**: Thuộc tính `name`, `employeeID`. Quan hệ: Liên kết với lớp ReportGenerator và PayrollSystem.
- **PayrollSystem**: Thuộc tính `employeeList`, `paycheckList`. Quan hệ: Liên kết với lớp ReportGenerator.
- **Report**: Thuộc tính `reportContent`, `reportDate`. Quan hệ: Liên kết với lớp ReportGenerator.

## 4. Biểu đồ
![Biểu đồ lớp Generate Employee Reports](https://www.planttext.com/api/plantuml/png/b59B2i8m4Dtt55dgeXS8KWfMH71Hx0b2EzHWcfHa58fuCXSUoIlOcAGOKSGi1kRtthoPtA-tt23JUEn4KWjc3Db1hpIkGO9cg3Gv9yG-w7gX1e0jDqY9jOkL3sMkecU3La9KWq7eA2bVNLVHEb1m5BCvzMJ99V7a0JAmIjO19HLgBjjuZar12PSOW35q5e2C2sF1VTi47atqbwvw3_NXfQBqeIpMvGc-otD-eDPFRwaaWiHOfKiL8oObriOy5lgaU6E1ty-LfjcqnO_9-2xnJdusUq4vo6RyCGy0003__mC0)

## 5. Giải thích sơ đồ lớp
- **ReportGenerator** sử dụng dữ liệu từ lớp `Employee` và `PayrollSystem` để tạo báo cáo.
- **Employee** cung cấp thông tin nhân viên cần thiết cho báo cáo.
- **PayrollSystem** cung cấp thông tin bảng lương và các dữ liệu liên quan để tạo báo cáo chi tiết hơn.
- **Report** chứa nội dung báo cáo đã tạo và ngày báo cáo.

