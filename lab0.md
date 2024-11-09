# Quản Lý Kho sách

Đây là sơ đồ của lớp Quản Lí Kho Sách với lớp cha và các lớp con , lớp `Sach` là lớp Cha , và các lớp con ( `SachThamKhao` , `SachGiaoKhoa` , `SachDienTu` )

## Sơ đồ lớp 
![Sơ đồ lớp](https://www.planttext.com/api/plantuml/png/Z97DQW8n4CVlUOevreClK7eGNMfXHP0DudL8qyr0TYBkvDJwCDAtg9GUV1AVm5VeRbUf1eITus_8_oDpsl-CQi6DnCeh8V4M5l7uzSamEtn3xW8KXvrnIXcFTGq56WVl2jefP4DSWhRSqbk6PahO8MA1ELQhY396xjZKYdQ1IqtyC7WylrBRQnVjiCeTXiHjHkoMqVIMQMA4fWKcCXDSluJ-AXbPrZ7Ho9ee6NBvJDvsYpSVK22dDdqCvdznr-BlFvy-XiERpWc-T4Xm5qgfaUNNzdg_0000__y30000)


## Sơ đồ ca sử dụng
![Sơ đồ ca sử dụng](https://www.planttext.com/api/plantuml/png/R96zQiCm481tFSMHtQzG0kxcr50ikX-kY0JHsTZoaBalKCYOAIrTIhDriYWPLFeUUeA-GYKxSHBeUFVTptVIhptCMuEDwVIA6MLM0egV7Nm_Uxk15A7mTW-tthxH4XAuxtp_Ih1mNv392WgtAoLZM9ggERA8i0q1qc9z9BbqB_IWt3j5b4iCWI36kbQKs8gOgGiiPQIpNFf-Nu-ZuSxRhPfDXPaIcZV8AuhROtMcl7tI49B0Wp55hNCzLpgsJBEv-z1XYEyFUbnmBasn3Xg6ougMND7KaWusWvG1BjrdU8V0J-riF1IIv6Owup9tPSnEfm_eGkuQ_AF2s5pGO_YYFm000F__0m00)


## Sơ đồ gói
![Sơ đồ gói](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bT9PabEgaBmiOKAHoOyt3rPmVtmvam5NON0qeUx5kSf-1pUg-2TaQyGV7XXSWONLq5YSdPYUgg2Kc1fOfvF9L0cE34vGqcXcai12AATy_DAYl9pSbABOY42mQb5PPd9gL2URtvAQauiLoqN5x9A1LrTEuHA1Ik5u8UxrogaFDozD2-T2o4ELWKn0KqDbqDgNWhGAm00003__mC0)




## Mô tả các lớp

### Lớp `Sach` ( Lớp cha )
- **Thuộc tính** : `TenSach` , `TacGia` , `NamXuatBan`
- **Phương thức** : `GetThongTin()`

### Lớp `SachThamKhao` ( Lớp con của `Sach` )
- **Thuộc tính** : `LinhVuc`
- **Phương thức** : `GetThongTin()`

### Lớp `SachGiaoKhoa` ( Lớp con của `Sach` )
- **Thuộc tính** : `CapHoc`
- **Phương thức** : `GetThongTin()`

### Lớp `SachDienTu` ( Lớp con của `Sach` )
- **Thuộc tính** : `DinhDangFile` , `KichThuocFile`
- **Phương thức** : `GetThongTin()`
