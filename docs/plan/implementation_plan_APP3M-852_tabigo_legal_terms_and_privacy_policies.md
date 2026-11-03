# Kế Hoạch Triển Khai (Implementation Plan) - APP3M-852
## [Landing Page][Legal & Compliance] Chuẩn Hóa Điều Khoản Sử Dụng & Chính Sách Bảo Mật TabiGo

---

| Thông Tin | Chi Tiết |
| :--- | :--- |
| **Mã Ticket** | `APP3M-852: [UI/UX][Compliance] TabiGo Legal Policies Integration` |
| **Tiêu đề** | Tích hợp văn bản Điều khoản sử dụng (8 mục dịch vụ) và Chính sách bảo mật cho TabiGo, xử lý điều hướng Dialog vs New Page |
| **Dự án / Module** | `tabi-go` (Website Landing Page B2C & Compliance) |
| **Mức độ ưu tiên** | **HIGH / P1 (Tuân thủ pháp lý Bộ Công Thương & Bảo vệ người dùng)** |
| **Nhánh Git đề xuất** | `version-2` |
| **Trạng thái** | 📋 **GIAI ĐOẠN 1: LẬP KẾ HOẠCH & ĐỀ XUẤT KIẾN TRÚC (CHỜ DUYỆT - HARD GATE)** |

---

## 1. MỤC TIÊU & PHẠM VI (OBJECTIVES & SCOPE)

### 1.1. Mục tiêu
1. **Chuẩn hóa thương hiệu & thông tin liên hệ 100% theo TabiGo:**
   - Loại bỏ hoàn toàn các tên gọi cũ/nhầm lẫn (`eSIMTravel`, `eSIM Travels`, `esimtravels.vn`, `Esim Travel`).
   - Thống nhất duy nhất thương hiệu: **TabiGo** (nền tảng eSIM du lịch quốc tế).
   - Thống nhất số Hotline & Zalo duy nhất: **`0794.058.999`** (khớp đồng bộ với Header, Footer và Floating Button Zalo hiện hữu).
   - Thống nhất thời gian giao nhận: **100% kỹ thuật số, gửi mã QR qua email trong 5 - 10 phút (tối đa 30 phút)**, loại bỏ triệt để đoạn văn bản cũ ghi nhầm "1-3 ngày làm việc".
2. **Cấu trúc lại nội dung pháp lý theo chỉ đạo của Product Owner:**
   - **Nhóm 1 (Gộp chung mục 1 đến 8):** Trở thành bộ văn bản **"Điều khoản sử dụng & Chính sách dịch vụ TabiGo"** (Bao gồm: Giao hàng, Bảo hành, Vận chuyển/Giao nhận, Thanh toán, Tiếp nhận & Giải quyết khiếu nại, Đổi trả & Hoàn tiền, Kiểm hàng, Điều khoản và điều kiện chung).
   - **Nhóm 2 (Mục 9 riêng biệt):** Trở thành văn bản **"Chính sách bảo mật thông tin TabiGo"** (Bảo vệ dữ liệu cá nhân, Cookie, eKYC và nguyên tắc lưu trữ).
3. **Giải quyết bài toán trải nghiệm người dùng (UX Interaction):**
   - Lập phương án phân tích chuyên sâu: Khi khách hàng click vào link *"Điều khoản sử dụng"* hoặc *"Chính sách bảo mật"* ở footer thì nên **mở Dialog (Modal popup)** hay **chuyển sang Trang mới (Dedicated Page)**.

---

## 2. BỐI CẢNH & PHÂN TÍCH HIỆN TRẠNG DỮ LIỆU

### 2.1. Bảng đối chiếu & chuẩn hóa các mâu thuẫn dữ liệu từ văn bản gốc

| Hạng mục đối chiếu | Hiện trạng trong file thô | Chuẩn hóa chính thức cho TabiGo | Lý do kỹ thuật & pháp lý |
| :--- | :--- | :--- | :--- |
| **Thương hiệu** | Ghi lẫn lộn `eSIMTravel`, `eSIM Travels`, `esimtravels.vn`, `Esim Travel`. | Thống nhất 100% là **TabiGo** (Website: `tabigo.vn`). | Đúng nhận diện thương hiệu sản phẩm đang xây dựng. |
| **Thời gian giao eSIM** | Một số chỗ ghi "1–3 ngày làm việc", chỗ khác ghi "5–10 phút". | **Giao tức thì qua Email trong 5–10 phút (chậm nhất 30 phút)**. | eSIM là sản phẩm số 100%, không giao vật lý, không có thời gian vận chuyển 1-3 ngày. |
| **Hotline hỗ trợ** | Lẫn lộn giữa 2 số `0794 058 999` và `0356 628 532`. | Thống nhất duy nhất: **Hotline & Zalo: `0794.058.999`**. | Đồng bộ tuyệt đối với Hotline hiển thị ở Header & Footer hiện tại. |
| **Email liên hệ** | `congty3mintel@gmail.com`. | **`support@tabigo.vn`** (kèm email dự phòng pháp nhân `congty3mintel@gmail.com`). | Chuyên nghiệp hóa kênh liên lạc người dùng. |
| **Đơn vị vận hành** | Đơn vị chủ quản: Công ty TNHH Đầu tư và Phát triển ZEYFI / 3M Intel. | **"Nền tảng TabiGo được phát triển và vận hành bởi 3M Intel / ZEYFI"**. | Thỏa mãn đầy đủ yêu cầu đăng ký hồ sơ với Cục TMĐT - Bộ Công Thương. |
| **Quy định hủy & hoàn tiền** | Đoạn thanh toán ghi hủy trong 24h trước khi kích hoạt; đoạn điều khoản ghi không hủy sau khi nhận QR. | **Làm rõ rành mạch:**<br>1. *Trước khi phát hành QR:* Hủy 100% miễn phí.<br>2. *Sau khi QR đã gửi vào email:* Không hoàn hủy ngang do tính bảo mật mã số.<br>3. *Hoàn tiền 100%:* Khi lỗi kỹ thuật từ hệ sinh thái TabiGo/nhà mạng mà không khắc phục được. | Tránh tranh chấp khiếu nại của khách hàng, minh bạch điều kiện. |

---

## 3. PHÂN TÍCH & MA TRẬN ĐA PHƯƠNG ÁN (DIALOG VS NEW PAGE VS HYBRID)

Người dùng yêu cầu: *"click vào nó sang trang mới hay mở dialog gì thì m lên kế hoạch xử lý nha"*. Dưới đây là phân tích kỹ thuật và UX chuyên sâu của 3 phương án:

```
┌────────────────────────────────────────────────────────────────────────┐
│ MA TRẬN ĐÁNH GIÁ CÁC PHƯƠNG ÁN ĐIỀU HƯỚNG PHÁP LÝ                       │
├────────────────────────────────────────────────────────────────────────┤
│ OPTION A: In-Page Modal Dialog (Mở Popup tại chỗ)                      │
│ OPTION B: Dedicated Independent Pages (Mở trang tĩnh độc lập)          │
│ OPTION C (KHUYÊN DÙNG): Hybrid Architecture (Trang riêng + Tab mới)   │
└────────────────────────────────────────────────────────────────────────┘
```

### 3.1. Phân tích chi tiết từng phương án

#### Phương Án A: In-Page Modal Dialog (Mở Popup toàn màn hình tại chỗ)
- **Cơ chế:** Khi click vào *"Điều khoản sử dụng"* hoặc *"Chính sách bảo mật"*, trang web không chuyển hướng mà mở một Dialog lớn (Modal popup với backdrop mờ), bên trong có Sidebar chuyển đổi 2 Tab: Tab 1 (8 mục Điều khoản) & Tab 2 (Chính sách bảo mật).
- **Ưu điểm:**
  - Khách hàng không bị rời khỏi trang đích, giữ nguyên ngữ cảnh và giỏ hàng/thanh tìm kiếm.
  - Tốc độ mở siêu nhanh (0s), cảm giác hiện đại giống ứng dụng di động.
- **Nhược điểm lớn:**
  - **Không đạt tiêu chuẩn kiểm duyệt của Bộ Công Thương:** Huy hiệu *"Đã đăng ký Bộ Công Thương"* ở footer yêu cầu các liên kết chính sách trên website TMĐT phải là các URL cố định, công khai để hệ thống crawler và chuyên viên thẩm định có thể truy cập trực tiếp bằng hyperlink (ví dụ: `tabigo.vn/terms.html`, `tabigo.vn/privacy.html`). Dialog thuần JS không có URL tĩnh độc lập sẽ bị đánh rớt hồ sơ TMĐT.
  - Nội dung 8 chính sách rất dài (hơn 4.000 từ). Đọc một văn bản pháp lý đồ sộ trong một khung cuộn modal trên mobile gây gò bó, khó chia sẻ link cụ thể.

#### Phương Án B: Dedicated Pages (Mở trang web riêng biệt cùng tab)
- **Cơ chế:** Tạo 2 file HTML riêng: `dieu-khoan-su-dung.html` và `chinh-sach-bao-mat.html`. Khi click, trình duyệt chuyển hướng từ `index.html` sang trang chính sách.
- **Ưu điểm:**
  - Chuẩn 100% hồ sơ Bộ Công Thương và chuẩn SEO Google.
  - Giao diện trang tài liệu chuyên nghiệp: có Mục lục bên trái (Sticky Table of Contents) giúp click nhảy nhanh đến từng mục (Giao hàng, Bảo hành, Đổi trả...).
- **Nhược điểm:**
  - Khách hàng đang xem dở trang chủ mua eSIM bị chuyển hướng mất trang, phải bấm nút Back của trình duyệt để quay lại.

#### Phương Án C (ĐỀ XUẤT TỐI ƯU NHẤT - HYBRID ARCHITECTURE): Trang Riêng Mở Tab Mới (`target="_blank"`)
- **Cơ chế:**
  1. Tạo 2 trang HTML chuẩn mực, cùng chung Design System với Landing Page (Font *Plus Jakarta Sans*, bảng màu *Warm Almond Cream* `#F5EFE6`, Header & Footer thu gọn đồng bộ):
     - `terms.html`: **Điều khoản sử dụng & Các chính sách dịch vụ TabiGo** (Gồm 8 mục: 1. Giao hàng, 2. Bảo hành, 3. Vận chuyển giao nhận, 4. Thanh toán, 5. Khiếu nại, 6. Đổi trả hoàn tiền, 7. Kiểm hàng, 8. Điều khoản chung). Có thanh điều hướng mục lục Sticky bên cạnh.
     - `privacy.html`: **Chính sách bảo mật thông tin TabiGo** (Toàn bộ nội dung Mục 9 về bảo vệ dữ liệu cá nhân, Cookie, eKYC).
  2. Tại Footer của `index.html`:
     - Gắn link trực tiếp: `<a href="terms.html" target="_blank" rel="noopener">Điều khoản sử dụng</a>`
     - Gắn link trực tiếp: `<a href="privacy.html" target="_blank" rel="noopener">Chính sách bảo mật</a>`
  3. *(Tùy chọn mở rộng)* Hỗ trợ mở Modal Preview nhanh nếu người dùng click trên Mobile Drawer, kèm nút *"Mở toàn trang trong tab mới"*.
- **Vì sao Phương án C là lựa chọn số 1:**
  - ✅ **Bảo toàn chuyển đổi bán hàng:** Khi người dùng mở xem điều khoản, tab trang chủ `index.html` vẫn giữ nguyên 100%, không mất trạng thái đang chọn eSIM hay tìm kiếm quốc gia.
  - ✅ **Chuẩn chỉ 100% Pháp lý Bộ Công Thương & Nghị định 52/2013/NĐ-CP về TMĐT:** Chuyên viên Bộ Công Thương có URL tĩnh trực tiếp để thẩm định và cấp tích xanh.
  - ✅ **Trải nghiệm đọc xuất sắc:** Không gian rộng rãi, có mục lục nhảy nhanh từng chính sách, hỗ trợ in ấn (Print CSS) và hiển thị hoàn hảo trên cả Desktop lẫn Smartphone.
  - ✅ **Giữ cho file `index.html` gọn gàng:** Không bị phình to thêm hàng chục KB text pháp lý, tối ưu Core Web Vitals (LCP/FID).

### 3.2. Bảng so sánh 3 phương án

| Tiêu chí | Option A: In-Page Modal | Option B: Trang Riêng (Cùng Tab) | Option C: Trang Riêng (Tab Mới - Đề Xuất) |
| :--- | :---: | :---: | :---: |
| **Chuẩn pháp lý Bộ Công Thương** | ❌ Kém (Không có URL tĩnh) | ✅ Hoàn hảo | ✅ **Hoàn hảo 100%** |
| **Không làm mất ngữ cảnh mua eSIM** | ✅ Tốt | ❌ Bị gián đoạn (chuyển trang) | ✅ **Tuyệt đối (Mở tab mới song song)** |
| **Trải nghiệm đọc văn bản 4000+ từ** | ⚠️ Gò bó trong popup | ✅ Thoải mái, có mục lục | ✅ **Tối ưu với Sticky TOC** |
| **Tác động đến kích thước index.html** | ⚠️ Tăng thêm ~35KB DOM | ✅ Không ảnh hưởng | ✅ **Hoàn toàn sạch sẽ** |
| **Khả năng chia sẻ link trực tiếp** | ❌ Không thể | ✅ Rất tốt | ✅ **Rất tốt (`terms.html#hoan-tien`)** |

---

## 4. CHI TIẾT NỘI DUNG VĂN BẢN ĐÃ CHUẨN HÓA CHO TABIGO

### 4.1. File 1: `terms.html` - Điều Khoản Sử Dụng & Chính Sách Dịch Vụ TabiGo
*Tập hợp 8 mục chính sách được phân chia rõ ràng với Anchor ID để người dùng click mục lục cuộn đến ngay lập tức:*

1. **Phần 1: Chính sách giao hàng eSIM (`#giao-hang`)**
   - Cam kết 100% eSIM kỹ thuật số cho 150+ quốc gia và vùng lãnh thổ.
   - Hình thức: Gửi mã QR và tài liệu hướng dẫn kích hoạt từng bước qua Email của khách hàng.
   - Thời gian giao hàng: Tức thì ngay sau thanh toán, thông thường trong 5 - 10 phút, chậm nhất 30 phút.
   - Lưu ý kiểm tra thư mục: Hộp thư đến $\rightarrow$ Spam/Junk $\rightarrow$ Quảng cáo.
   - Hotline hỗ trợ kỹ thuật: **`0794.058.999`**, Email: **`support@tabigo.vn`**.

2. **Phần 2: Chính sách bảo hành kết nối (`#bao-hanh`)**
   - Đối tượng & Điều kiện: Áp dụng cho mọi khách hàng mua gói cước eSIM TabiGo chính thức còn trong thời hạn sử dụng.
   - Phạm vi: Bảo hành kết nối, hỗ trợ thiết lập APN, cấu hình mạng chuyển vùng quốc tế, khắc phục lỗi kỹ thuật từ nhà mạng đối tác.
   - Quy trình bảo hành 4 bước: Tiếp nhận $\rightarrow$ Xác minh lỗi $\rightarrow$ Hướng dẫn kỹ thuật/Cấp lại mã eSIM thay thế $\rightarrow$ Hoàn tất xử lý trong vòng 24h.

3. **Phần 3: Thông tin vận chuyển, giao nhận (`#van-chuyen`)**
   - Khẳng định: eSIM TabiGo là sản phẩm số, không áp dụng giao nhận bưu chính vật lý.
   - Lưu trữ mã QR: Được gửi qua email đồng thời hiển thị trong lịch sử đơn hàng trên ứng dụng/website TabiGo.
   - Hướng dẫn cài đặt trước chuyến đi: Có thể quét cài đặt trước 1 - 2 ngày ở nhà mà không lo hao hụt dung lượng (gói cước chỉ bắt đầu tính ngày khi kết nối trạm sóng tại nước sở tại).

4. **Phần 4: Chính sách thanh toán an toàn (`#thanh-toan`)**
   - Phương thức chấp nhận: Cổng VNPAY (VietQR, Mobile Banking, Thẻ nội địa), OnePay (Thẻ Visa, Mastercard, JCB, Amex), Apple Pay, Google Pay, Ví Tabi Xu.
   - Quy định thanh toán trước 100% để hệ thống cấp phát mã QR tự động.
   - Tiêu chuẩn bảo mật mã hóa SSL 256-bit, không lưu trữ thông tin thẻ ngân hàng trên server TabiGo.
   - Hóa đơn điện tử gửi tự động qua email đặt hàng.

5. **Phần 5: Chính sách tiếp nhận và giải quyết khiếu nại (`#khieu-nai`)**
   - Nguyên tắc: Minh bạch, công bằng, bảo vệ quyền lợi chính đáng của du khách.
   - Các kênh tiếp nhận: Hotline/Zalo **`0794.058.999`**, Email: **`support@tabigo.vn`**, Trực tiếp tại Trụ sở Technopark Tower, Gia Lâm, Hà Nội.
   - Thời hạn xử lý: Phản hồi trong 2 giờ, giải quyết triệt để tối đa trong 5 ngày làm việc.

6. **Phần 6: Chính sách đổi trả và hoàn tiền (`#hoan-tien`)**
   - **Được hoàn tiền 100%:** Khi mã eSIM bị lỗi kỹ thuật hệ thống hoặc lỗi trạm phát sóng nhà mạng đối tác mà đội ngũ TabiGo không thể khắc phục được trong thời gian du lịch của khách.
   - **Trường hợp từ chối hoàn tiền:** Khách hàng tự ý xóa cấu hình eSIM đã cài đặt; thiết bị của khách hàng là máy khóa mạng (lock) hoặc không có phần cứng hỗ trợ eSIM do khách không kiểm tra danh sách tương thích trước khi đặt; điểm đến xảy ra sự cố bất khả kháng (thiên tai, chiến tranh).
   - Thời gian xử lý hoàn tiền: Chuyển khoản lại trong 3 - 7 ngày làm việc theo phương thức thanh toán ban đầu.

7. **Phần 7: Chính sách kiểm hàng (`#kiem-hang`)**
   - Hướng dẫn kiểm tra ngay khi nhận email: Kiểm tra tên gói cước, dung lượng GB, số ngày sử dụng, quốc gia áp dụng.
   - Thao tác quét thử kiểm tra nhận diện SIM ảo trên điện thoại trước chuyến bay.

8. **Phần 8: Điều khoản & Điều kiện chung (`#dieu-khoan-chung`)**
   - Định nghĩa dịch vụ, giá cước niêm yết minh bạch (đã bao gồm thuế phí).
   - Quyền sở hữu trí tuệ thương hiệu TabiGo, tính khả dụng của dịch vụ mạng quốc tế.
   - Luật áp dụng: Pháp luật Nước Cộng Hòa Xã Hội Chủ Nghĩa Việt Nam.

---

### 4.2. File 2: `privacy.html` - Chính Sách Bảo Mật Thông Tin TabiGo
*Bao gồm toàn bộ Mục 9 đã được chuyển đổi thương hiệu hoàn toàn sang TabiGo:*

1. **Nguyên tắc bảo vệ dữ liệu:** Thu thập đúng mục đích, giảm thiểu dữ liệu, thời hạn lưu trữ rõ ràng và tôn trọng quyền riêng tư của cá nhân.
2. **Thông tin thu thập:** Họ tên, email nhận eSIM, số điện thoại liên hệ, lịch sử đơn hàng.
3. **Dữ liệu eKYC (nếu có):** Đối với một số quốc gia quy định pháp luật bắt buộc định danh sim (như Singapore, Thái Lan, Nhật Bản theo luật viễn thông bản địa), TabiGo chỉ thu thập và chuyển tiếp bảo mật trực tiếp sang cổng xác thực được cấp phép.
4. **Cam kết không thu thập dữ liệu nhạy cảm:** Không thu thập số an sinh, niềm tin chính trị, tôn giáo, y tế.
5. **Chính sách Cookie & Tracking:** Sử dụng cookie phiên và cục bộ để duy trì phiên giỏ hàng và cá nhân hóa tiền tệ (VND/USD).
6. **Cam kết không thương mại hóa dữ liệu:** Tuyệt đối không bán, cho thuê thông tin người dùng cho bất kỳ bên thứ ba nào vì mục đích quảng cáo rác.
7. **Quyền của chủ thể dữ liệu:** Quyền tra cứu, yêu cầu chỉnh sửa, yêu cầu hủy bỏ thông tin cá nhân qua email `support@tabigo.vn`.

---

## 5. THIẾT KẾ GIAO DIỆN & TRẢI NGHIỆM ĐỒNG BỘ (DESIGN SPECIFICATION)

Cả 2 trang tài liệu pháp lý mới (`terms.html` và `privacy.html`) sẽ thừa hưởng nguyên vẹn ngôn ngữ thiết kế sang trọng, hiện đại của Landing Page:
- **Tone màu chủ đạo:** Nền Warm Almond Cream (`#F5EFE6`), Card nền trắng bo góc mềm mại (`#FFFFFF`, `border-radius: 20px`), viền mờ cao cấp (`border: 1px solid #EAE3D6`).
- **Typography:** Font chữ chuẩn *Plus Jakarta Sans* & *Inter*, cấp bậc tiêu đề rõ ràng (H1, H2, H3, H4) với số thứ tự đánh dấu nổi bật.
- **Header:** Phiên bản tối giản (Logo TabiGo sắc nét góc trái, nút quay về Trang chủ và nút CTA *"Khám phá eSIM"*).
- **Mục lục điều hướng (Sticky Sidebar TOC):** 
  - Nằm ở cột bên trái trên màn hình Desktop/Laptop, tự động highlight mục đang đọc khi người dùng cuộn chuột (ScrollSpy).
  - Trên Mobile: Hiển thị dưới dạng Dropdown menu trượt mượt giúp chọn nhanh phần muốn đọc.
- **Footer:** Giữ nguyên footer đồng bộ, hiển thị bản quyền `©2026 TABI GO` và dấu chứng nhận Bộ Công Thương.

---

## 6. DANH SÁCH CÁC TẬP TIN SẼ TẠO MỚI & THAY ĐỔI

1. **`tabi-go/terms.html` [TẠO MỚI]:** Trang Điều khoản sử dụng & 8 chính sách dịch vụ TabiGo.
2. **`tabi-go/privacy.html` [TẠO MỚI]:** Trang Chính sách bảo mật thông tin TabiGo.
3. **`tabi-go/index.html` [SỬA ĐỔI]:**
   - Cập nhật liên kết footer:
     - Đổi `href="javascript:void(0)"` thành `href="terms.html"` (`target="_blank"`).
     - Đổi link chính sách bảo mật thành `href="privacy.html"` (`target="_blank"`).
   - Cập nhật cả trong Mobile Drawer menu để người dùng điện thoại cũng truy cập dễ dàng.

---

## 7. LỘ TRÌNH TRIỂN KHAI (ROADMAP)

- **Bước 1 (Đã hoàn thành):** Khảo sát dữ liệu thô, lọc bỏ triệt để các tham chiếu cũ `eSIMTravel`, chuẩn hóa hotline `0794.058.999` và lập Kế hoạch triển khai (Implementation Plan).
- **🛑 CỔNG DUYỆT CỨNG (HARD GATE):** Trình bày phương án điều hướng cho Người dùng phê duyệt.
- **Bước 2 (Sau khi duyệt):** Xây dựng `terms.html` và `privacy.html` với cấu trúc responsive, sticky navigation và chuẩn nhận diện TabiGo.
- **Bước 3:** Cập nhật liên kết trong `index.html` (cả Desktop footer và Mobile drawer).
- **Bước 4:** Kiểm tra hiển thị đa thiết bị (Desktop 1280px, Tablet 768px, Mobile 390px) bằng Chrome Headless.
- **Bước 5:** Báo cáo Người dùng nghiệm thu trước khi commit & push lên `version-2`.

---

## 8. 🛑 CỔNG DUYỆT CỨNG (HARD APPROVAL GATE)

> [!IMPORTANT]
> **AI đang dừng lại tại Cổng duyệt cứng theo quy định.**
> Tuyệt đối không tự ý viết code khi chưa có phản hồi từ Người dùng.
> 
> **Câu hỏi cần duyệt từ Bạn:**
> 1. Bạn có duyệt **Phương Án C (Tạo 2 trang riêng `terms.html` và `privacy.html`, click mở tab mới `target="_blank"`)** để vừa chuẩn 100% hồ sơ Bộ Công Thương vừa không làm mất trang mua eSIM của khách không?
> 2. Các thông tin chuẩn hóa: Tên thương hiệu **TabiGo**, Hotline/Zalo **`0794.058.999`**, Email **`support@tabigo.vn`**, thời gian giao eSIM **5-10 phút qua email** đã hoàn toàn chuẩn ý bạn chưa?
>
> *(Chỉ cần bạn gõ `approve` hoặc cho ý kiến điều chỉnh, mình sẽ tiến hành tạo các trang ngay!)*

