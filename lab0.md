# Quản Lý Bán Sách Đơn Giản

## Mô Tả Dự Án

Hệ thống **Quản lý bán sách đơn giản** giúp quản lý thông tin sách, đơn hàng và khách hàng trong cửa hàng sách. Các tính năng chính của hệ thống bao gồm:

- Quản lý sách: Lưu trữ thông tin về sách (tên, tác giả, giá, số lượng tồn kho).
- Quản lý đơn hàng: Quản lý các đơn hàng của khách hàng (sách đã mua, số lượng, ngày đặt hàng).
- Quản lý khách hàng: Lưu trữ thông tin của khách hàng (tên, email, số điện thoại).

Dự án này sử dụng **ASP.NET Core MVC**, **Entity Framework Core**, và **SQL Server** để lưu trữ dữ liệu. Nó cung cấp giao diện người dùng để thêm, sửa, xóa sách và đơn hàng, đồng thời hiển thị các thông tin thống kê về bán hàng.

## Sơ đồ lớp 
![Sơ đồ lớp](https://www.planttext.com/api/plantuml/png/T94x3i8m38RtdCBg14X5i3Bn75XuY5uWIas9o0Cbxe0G9sFWI5o1DhHLKM6pFzd-_pzvFPvJJznHhXKJYdiFSslFS6C0CKX3i4v3wSb9aq4YIM4Rp78wMHT8Ya9ghc3dfC1c_q1Md8iE84DQ8d6fVAy_gVRPdLMoMvUYw-gMPUcerIvoJrQZQw5zpWr9kWQmv8I9rFWvMNQrV01hSxI_3DHd_sRVSFqLVQMBB6smErdJQ3KkEtBXWQDn174CqMWu74HL-688bVAiSV9xwAAuGC-cQDBYrzu0003__mC0)

## Cấu Trúc Hệ Thống

### **Các Lớp trong Hệ thống**

1. **Book**: Đại diện cho một cuốn sách.
2. **Order**: Đại diện cho một đơn hàng của khách hàng.
3. **Customer**: Đại diện cho một khách hàng mua sách.

### **Sơ Đồ Lớp**

Dưới đây là sơ đồ lớp của hệ thống quản lý bán sách đơn giản, mô tả các lớp và mối quan hệ giữa chúng:

```planttext
@startuml
class Book {
  - int Id
  - string Title
  - string Author
  - decimal Price
  - int Stock
  + getDetails(): string
}

class Order {
  - int Id
  - int BookId
  - int CustomerId
  - int Quantity
  - DateTime OrderDate
  + getOrderInfo(): string
}

class Customer {
  - int Id
  - string Name
  - string Email
  - string Phone
  + getCustomerInfo(): string
}

Book "1" -- "0..*" Order : sells
Customer "1" -- "0..*" Order : places
@enduml

