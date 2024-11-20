# Phân tích Kiến Trúc và Ca Sử Dụng Hệ Thống Payroll

## 1. Phân tích Kiến Trúc

### Kiến trúc 3 lớp
- **Lớp giao diện người dùng (UI)**: Nơi người dùng tương tác, nhập liệu hoặc xem thông tin. Đây có thể là một ứng dụng web hoặc giao diện desktop.
- **Lớp logic ứng dụng (Application Layer)**: Xử lý các logic nghiệp vụ, như tính toán lương, tính thuế, bảo hiểm và xử lý các yêu cầu từ UI.
- **Lớp dữ liệu (Data Layer)**: Quản lý cơ sở dữ liệu, lưu trữ và truy xuất thông tin về nhân viên, bảng lương, thời gian làm việc, v.v.

**Giải thích lý do lựa chọn**:
- Phân chia hệ thống thành ba lớp giúp tổ chức mã nguồn rõ ràng, dễ bảo trì và mở rộng.
- Mỗi lớp có thể thay đổi mà không ảnh hưởng đến các lớp còn lại (tính tái sử dụng và linh hoạt).

### Biểu đồ package
![Biểu đồ](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bT1Od9sOdggWbAefu9FOcLgaP92DPU2GhHhRa5EVcLgQbXcQdciWW98A22nCZSrhmGimbNBXT3gM52GavcSM9APduTY1b13KNvEZdD-NWc8JYsA1Oc6PEQc9YSMfI0B8vlcabYIYDKf88canEBKM2J78CHgkHnIyrA0NW80003__mC0)

## Giải thích 
Biểu đồ này mô tả sự phân chia hệ thống thành các package (gói) khác nhau để tổ chức mã nguồn, bao gồm:
* **UI Layer (Giao diện người dùng) :** Đây là lớp giao diện, nơi người dùng tương tác với hệ thống. Các lớp như EmployeeView và PaymentView đại diện cho các trang hoặc biểu mẫu mà người dùng sử dụng để xem thông tin nhân viên hoặc thanh toán.
* **Application Layer (Lớp ứng dụng) :** Lớp này chứa các logic nghiệp vụ, xử lý các yêu cầu từ UI và giao tiếp với lớp dữ liệu. Các lớp như PayrollController và TimecardController xử lý các thao tác như tính toán lương, duy trì thông tin thời gian làm việc của nhân viên.
* **Data Layer (Lớp dữ liệu) :** Đây là lớp chịu trách nhiệm lưu trữ và truy xuất dữ liệu từ cơ sở dữ liệu. Các lớp như EmployeeDatabase và PaymentDatabase lưu trữ dữ liệu về nhân viên và thanh toán.


## 2. Cơ chế phân tích
Một số cơ chế cần giải quyết trong hệ thống Payroll:
*   **Quản lý dữ liệu nhân viên :**   Cần cơ chế để thêm, sửa, xóa và truy xuất thông tin nhân viên.
*   **Tính toán lương :**  Tính toán các yếu tố như tiền lương, thuế, bảo hiểm và các khoản khấu trừ khác.
*   **Quản lý thời gian làm việc :** Cần cơ chế để theo dõi và tính toán giờ làm việc của nhân viên.
  ## Giải thích lý do: Các cơ chế này đảm bảo hoạt động của hệ thống Payroll được thực hiện một cách tự động và chính xác, giúp hệ thống có thể mở rộng và dễ bảo trì

## 3. Phân tích ca sử dụng: Select Payment
**Lớp phân tích :**
*   **PayrollController :** Xử lý các yêu cầu liên quan đến lương.
*   **EmployeeDatabase :** Truy xuất thông tin nhân viên từ cơ sở dữ liệu.
*   **PaymentDatabase :** Truy xuất và lưu trữ thông tin thanh toán.

![Biểu đồ](https://www.planttext.com/api/plantuml/png/V51B2W8n3Dtt5Bc05-X21go2En4yG6QCED3FcAQBdis5H_8AJa46RDLD0Y_lvJtUy_xeeY1BSbRX887X58bL6R1Qmm4p1sitmKlPn1gET4iKfPmSUG53WgEDgg4M_TPDDcGYWu8zHjAm8nck2mvxVmdiKCRWLKt-6K0I-yyNtztV4Mlp9VcCguhptxDMjfQbE0rcZ9F5t7JKaJ_FJRy0003__mC0)

## Mô tả các bước :
* **User (Người dùng)** yêu cầu xem thông tin thanh toán từ PayrollController (Điều khiển thanh toán).
* **PayrollController** gửi yêu cầu lấy thông tin nhân viên từ EmployeeDatabase (Cơ sở dữ liệu nhân viên).
* **EmployeeDatabase** trả về thông tin của nhân viên cho PayrollController.
* **PayrollController** tiếp tục gửi yêu cầu lấy dữ liệu thanh toán từ PaymentDatabase (Cơ sở dữ liệu thanh toán).
* **PaymentDatabase** trả về dữ liệu thanh toán cho PayrollController.
* Cuối cùng **PayrollController** hiển thị thông tin thanh toán cho User.
  
## Giải thích
* Ca sử dụng "Select Payment" cho phép người dùng xem thông tin thanh toán của mình. Hệ thống truy xuất thông tin từ cơ sở dữ liệu của nhân viên và thanh toán, rồi hiển thị lại cho người dùng. Đây là một ca sử dụng cơ bản trong hệ thống payroll, nơi người dùng chỉ đơn giản là xem các thông tin đã được tính toán trước.

## 4. Phân tích ca sử dụng: Maintain Timecard
**Lớp phân tích :**
*   **TimecardController :** Xử lý các yêu cầu liên quan đến thời gian làm việc.
*   **EmployeeDatabase :** Lưu trữ thông tin nhân viên.
*   **TimecardDatabase :** Lưu trữ và quản lý thông tin về giờ làm việc của nhân viên.

![Biểu đồ](https://www.planttext.com/api/plantuml/png/T91B3i8m34JtEKKkm0MwG4Ly9BOK3k0cBaJaWnmNnDbOS2IkG1E95XMwiQp9U5uqhyUpZ0p4hRC250UIXuWaqf2pkTmRXmf8BuDd2jOY5R9gQsUuVv9RtmHom2PuyUjFAMjtiU6Ek0A66Y8MSeEiJhsU8yJODSNV8RVaHyV_mHzr05TmnU7hIHTZqnItsnj3BX_b73r1JUKLSg7EFjmiwkCNC7SNOwggHA-xrjy0003__mC0)

## Mô tả các bước : 
* **User (Người dùng)** nhập thông tin thời gian làm việc (Timecard) và gửi tới TimecardController (Điều khiển bảng công).
* **TimecardController** gửi yêu cầu lấy thông tin nhân viên từ EmployeeDatabase (Cơ sở dữ liệu nhân viên).
* **EmployeeDatabase** trả về thông tin nhân viên cho TimecardController.
* **TimecardController** lưu trữ thông tin thời gian làm việc vào TimecardDatabase (Cơ sở dữ liệu bảng công).
* **TimecardDatabase**  xác nhận dữ liệu đã được lưu cho TimecardController.
* cuối cùng **TimecardController** gửi thông báo xác nhận việc lưu thông tin thời gian làm việc đến User.

# Giải thích 
* Ca sử dụng "Maintain Timecard" cho phép người dùng nhập và duy trì thông tin thời gian làm việc của mình. Hệ thống sẽ lưu trữ thông tin này vào cơ sở dữ liệu để theo dõi thời gian làm việc của nhân viên. Đây là một phần quan trọng trong việc tính toán lương cho nhân viên trong hệ thống payroll.
 

## 5. Hợp nhất kết quả phân tích

![Biểu đồ](https://www.planttext.com/api/plantuml/png/Z9DDJiCm48NtFiNiMFK2MQ2Y1YGMIAY10qoTALZufzXZKCx6WYDn1UpGDi594Aiuu_VcFNsIlpu-ru7HSpHQe6JduJ6GFnwRBZ0P8IwW8KsIuHuxGvOX1WA9WKGMm-eoNtYdzSPPpb_o5MpfDL8OF3KnAXt4H9hzr-QWNKTK8-CkBQxWXbW-d-TmQ_VE6sJbh2Z5YmKuUljxnNpwiM8PVcwUvgBG_9rPEgUH6Lm5jGe7ZTs4KI9-Xygc7miFof14tqwXdsx61PguCue7qvZRLFzlzBFCv_9deSy7dwP3S8DlD5JluPMYfTnqtYjlUbE_frr8_G5_9L-iUzVKFeq2UtOXP5Hhicrw4jy0003__mC0)

Biểu đồ tổng hợp này mô tả sự kết hợp của hai ca sử dụng "Select Payment" và "Maintain Timecard". Điều này thể hiện rằng hệ thống Payroll cần phải xử lý nhiều tác vụ đồng thời:

* Khi người dùng yêu cầu xem thông tin thanh toán (Select Payment), hệ thống sẽ truy xuất thông tin từ cơ sở dữ liệu nhân viên và thanh toán, sau đó hiển thị lại cho người dùng.
* Đồng thời, khi người dùng duy trì bảng công (Maintain Timecard), thông tin về thời gian làm việc sẽ được lưu vào cơ sở dữ liệu và hệ thống xác nhận lại với người dùng.

