# Kế Hoạch Triển Khai (Implementation Plan) — Landing Page TabiGo (Phiên Bản Version 2)
## [Release][P1][B2C-LANDING-TABIGO-V2] Tổng Hợp Toàn Diện Quá Trình Nâng Cấp Giao Diện Ảnh Thực Tế, Tối Ưu Mobile Responsive, Bộ Văn Bản Pháp Lý Bộ Công Thương & Hồ Sơ Xét Duyệt Meta Facebook Login

---

| Thông Tin | Chi Tiết |
| :--- | :--- |
| **Dự án / Module** | `tabi-go` (Website Landing Page B2C & Compliance) |
| **Mã Phiên Bản** | **TABIGO LANDING PAGE VERSION 2 (V2-STABLE)** |
| **Nhánh Git triển khai** | **`main`** *(Đồng bộ trực tiếp toàn bộ code từ nhánh `version-2` bên GitHub)* |
| **Kho lưu trữ chính thức** | `git@gitlab.human-life.vn:3m-app/tabigo-landing.git` |
| **Trạng thái thực tế** | ✅ **HOÀN THÀNH 100% & ĐÃ BÀN GIAO TOÀN DIỆN LÊN PRODUCTION** |
| **Quy chuẩn kỹ thuật** | HTML5, CSS3, Vanilla JS, Vite 6 (Multi-Page App MPA), Responsive Mobile-First |
| **Đơn vị chủ quản** | Công ty TNHH Đầu tư và Phát triển Công nghệ 3M Intel |

---

## 1. MỤC TIÊU & BỐI CẢNH NÂNG CẤP VERSION 2 (OVERVIEW & OBJECTIVES)

Phiên bản **TabiGo Landing Page Version 2** là đợt nâng cấp toàn diện và quan trọng nhất kể từ khi khởi tạo dự án, nhằm giải quyết triệt để 4 nhóm bài toán lớn:

1. **Nâng cấp thẩm mỹ & Tái cấu trúc bố cục theo ảnh chụp thực tế (Lifestyle Photography):**
   - Loại bỏ hoàn toàn hình vẽ hoạt hình 2D, thay bằng ảnh chụp thực tế của du khách tại Tokyo, Rome, sân bay.
   - Khai tử các vùng đen / video rỗng gây hiểu nhầm; thiết kế lại Hero Section cân xứng, 3-Step Journey tinh giản và Hub hỗ trợ khách hàng người thật 24/7.
2. **Tối ưu trải nghiệm người dùng trên thiết bị di động (Mobile & Tablet Responsive):**
   - Thay thanh điều hướng tràn màn hình trên mobile bằng **Hamburger Menu & Off-canvas Drawer** trượt mượt mà.
   - Tối ưu hóa padding, typography, và bố cục lưới responsive trên mọi kích thước màn hình từ 375px đến 1440px.
3. **Chuẩn hóa hồ sơ pháp lý đăng ký Website Thương mại điện tử với Bộ Công Thương (MoIT Compliance):**
   - Xây dựng 2 trang tài liệu chuyên biệt: **`terms.html`** (gộp 8 chính sách vận hành) và **`privacy.html`** (chính sách bảo mật dữ liệu theo Nghị định 13/2023/NĐ-CP).
   - Tích hợp thanh mục lục bên cạnh (Sticky Table of Contents) cuộn tự động theo vị trí đọc (**ScrollSpy**).
   - 100% chuẩn hóa nhận diện thương hiệu TabiGo, Hotline/Zalo `0794.058.999`, thời gian giao eSIM qua email trong 5-10 phút.
4. **Đáp ứng điều kiện kiểm duyệt xét duyệt quyền Đăng nhập Facebook (Meta Developer App Review):**
   - Xây dựng trang chuyên biệt **`data-deletion.html`** (Hướng dẫn xóa dữ liệu người dùng Facebook theo Meta Platform Policy).
   - Xuất file biểu tượng ứng dụng App Icon chuẩn **1024 x 1024 px** (`tabigo_app_icon_1024.png`).
   - Cấu hình đóng gói Multi-Page App trong `vite.config.js` để triển khai đồng thời cả 4 trang trên Vercel/GitLab CI/CD.

---

## 2. CHI TIẾT CÁC HẠNG MỤC NÂNG CẤP TRONG VERSION 2

### 2.1. Tái Cấu Trúc Giao Diện Trang Chủ (`index.html`)

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│ KIẾN TRÚC GIAO DIỆN CHUẨN AIRALO & LIFESTYLE PHOTOGRAPHY TRÊN VERSION 2                │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ [Header]        Logo TabiGo sắc nét | Language Selector | Nút "Khám phá eSIM"         │
│ [Mobile Drawer] Hamburger Menu trượt êm, tích hợp công cụ tiền tệ VND & liên kết pháp lý│
│ [Hero Slider]   Ảnh du khách thực tế chuẩn 4:3 (Tokyo, Rome) cân đối với nội dung text │
│ [Quick Jump]    3 Thẻ điều hướng cuộn nhanh (Cách thức hoạt động, Điểm đến, B2B)       │
│ [How It Works]  3 Bước hành trình trực quan (01 Chọn gói, 02 Quét QR, 03 Kết nối ngay)  │
│ [App Banner]    Mockup smartphone phong cách Lifestyle tại sân bay kèm QR code quét tải│
│ [Support Hub]   Avatar Stack chuyên viên hỗ trợ 24/7 kèm nút gọi Hotline/Chat Zalo     │
│ [Footer]        Huy hiệu Bộ Công Thương, hotline 0794.058.999 và 5 liên kết điều khoản │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

1. **Header & Navigation:**
   - Phóng to logo TabiGo cân xứng, hiển thị sắc nét trên màn hình Retina.
   - Trên desktop: Giữ hàng navigation rõ ràng, thoáng đãng.
   - Trên mobile: Tự động ẩn hàng nav dài, hiển thị nút Hamburger và mở menu trượt (Off-canvas Drawer) chuyên nghiệp.
2. **Hero Section:**
   - Slide 0: Nữ du khách trải nghiệm mạng SoftBank 5G tại Tokyo giữa mùa hoa anh đào ngập tràn ánh nắng ấm áp (tỷ lệ 4:3 chuẩn).
   - Slide 1: Đôi bạn trẻ du lịch selfie tại Rome (Vodafone 5G), truyền tải trọn vẹn thông điệp chia sẻ và tặng 100.000đ Tabi Xu.
   - Đồng bộ chiều cao (`44px`) và bo góc (`12px`) giữa nút CTA chính cam và 2 nút tải ứng dụng Store đen, triệt tiêu lỗi nút to nút nhỏ.
3. **Quy trình kết nối 3 bước (How It Works):**
   - Xóa bỏ khối video rỗng cũ; tinh giản thành 3 bước kết nối rõ ràng: Bước 1 (Chọn điểm đến & gói data), Bước 2 (Quét mã QR nhận qua email), Bước 3 (Bật Data Roaming kết nối ngay khi hạ cánh).
   - Phụ đề được co gọn trên 1 dòng duy nhất trên màn hình lớn theo đúng yêu cầu thiết kế.
4. **Trung tâm hỗ trợ khách hàng (Support Hub):**
   - Đội ngũ Avatar Stack người thật kèm chấm xanh trực tuyến 24/7/365.
   - Kết nối trực tiếp Hotline & Zalo CSKH chính thức: `0794.058.999`.

---

### 2.2. Bộ Văn Bản Pháp Lý & Tuân Thủ Bộ Công Thương (`terms.html` & `privacy.html`)

1. **Trang Điều Khoản Dịch Vụ (`terms.html`):**
   Gộp chung 8 quy định vận hành chính thức từ văn bản nghiệp vụ của dự án:
   * **Mục 1:** Chính sách giao hàng (100% kỹ thuật số qua email trong 5–10 phút, tối đa 30 phút).
   * **Mục 2:** Chính sách bảo hành kết nối.
   * **Mục 3:** Thông tin vận chuyển, giao nhận (Không giao vật lý, quét mã QR trước khi cất cánh).
   * **Mục 4:** Chính sách thanh toán (VNPAY, OnePay, Apple Pay, Google Pay, Tabi Xu, SSL 256-bit).
   * **Mục 5:** Tiếp nhận và giải quyết khiếu nại (Hotline `0794.058.999`, Technopark Tower).
   * **Mục 6:** Chính sách đổi trả và hoàn tiền (Hoàn tiền 100% nếu lỗi mạng từ nhà cung cấp).
   * **Mục 7:** Chính sách kiểm tra đơn hàng.
   * **Mục 8:** Điều khoản và điều kiện chung (Tuân thủ pháp luật Việt Nam).
2. **Trang Chính Sách Bảo Mật Thông Tin (`privacy.html`):**
   * Bảo vệ quyền riêng tư theo tiêu chuẩn quốc tế và Nghị định 13/2023/NĐ-CP.
   * Quy định về thông tin chủ động cung cấp, dữ liệu kỹ thuật, eKYC quốc tế theo luật viễn thông bản địa.
   * Cam kết không thu thập dữ liệu cá nhân nhạy cảm và chính sách Cookie minh bạch.
3. **Trải nghiệm tra cứu (UX):**
   * Cả 2 trang mở trong tab mới (`target="_blank"`) từ Footer để không làm gián đoạn luồng mua hàng của khách trên trang chủ.
   * Tích hợp thanh mục lục bên cạnh (Sticky Sidebar Table of Contents) tự động đánh dấu mục đang đọc (**ScrollSpy**).

---

### 2.3. Xét Duyệt Facebook Login Cho Ứng Dụng Tabigo (`data-deletion.html` & App Icon)

1. **Trang Hướng Dẫn Xóa Dữ Liệu Người Dùng Facebook (`data-deletion.html`):**
   * Đáp ứng trực tiếp yêu cầu bắt buộc của Meta (Facebook Platform Policy) khi xin quyền `Sign in with Facebook`.
   * Cung cấp 2 cách rõ ràng:
     * **Cách 1 (Tự động):** Hướng dẫn người dùng vào Cài đặt Facebook $\rightarrow$ Ứng dụng và trang web $\rightarrow$ Gỡ quyền ứng dụng Tabigo.
     * **Cách 2 (Thủ công):** Gửi email tới `privacy@tabigo.vn` để hệ thống xóa vĩnh viễn tài khoản, liên kết Facebook UID và lịch sử giao dịch trong vòng 24 - 48h (có cấp mã xác nhận Confirmation Code).
2. **Cập nhật chính sách dữ liệu Facebook trong `privacy.html`:**
   * Nêu rõ thông tin thu thập qua Facebook Login: Họ tên, Email, Facebook UID, Avatar.
   * Cam kết không thu thập bạn bè hay tin nhắn riêng tư; không chia sẻ cho bên thứ ba.
3. **Biểu tượng ứng dụng Meta (App Icon 1024 x 1024 px):**
   * Xuất file ảnh chuẩn Retina: `assets/images/tabigo_app_icon_1024.png` kích thước chính xác 1024x1024 px nền xanh thương hiệu sắc nét.

---

### 2.4. Đóng Gói Kỹ Thuật & Cấu Hình Multi-Page App (Vite & Vercel)

* **Vấn đề đã khắc phục:** Vite mặc định chỉ đóng gói 1 file `index.html`, dẫn tới việc các file `terms.html`, `privacy.html`, `data-deletion.html` bị lỗi `404 NOT_FOUND` khi deploy lên Vercel.
* **Giải pháp trong `vite.config.js`:**
  Khai báo toàn bộ 4 điểm vào (entry points):
  ```javascript
  input: {
    main: resolve(__dirname, 'index.html'),
    terms: resolve(__dirname, 'terms.html'),
    privacy: resolve(__dirname, 'privacy.html'),
    dataDeletion: resolve(__dirname, 'data-deletion.html'),
  }
  ```
* **Kết quả build:** Cả 4 trang HTML được xuất hoàn hảo vào thư mục `dist/`, hoạt động mượt mà 100% trên cả Vercel và môi trường tĩnh.

---

## 3. DANH SÁCH CÁC TẬP TIN HOÀN THIỆN TRONG VERSION 2

| Đường Dẫn Tập Tin | Vai Trò & Chức Năng |
| :--- | :--- |
| [`tabi-go/index.html`](file:///Users/quanghuy/human/3M/tabi-go/index.html) | Landing Page chính thức TabiGo Version 2 (Lifestyle Photography & Mobile Drawer) |
| [`tabi-go/terms.html`](file:///Users/quanghuy/human/3M/tabi-go/terms.html) | Trang Điều khoản dịch vụ & 8 chính sách vận hành (Chuẩn Bộ Công Thương) |
| [`tabi-go/privacy.html`](file:///Users/quanghuy/human/3M/tabi-go/privacy.html) | Trang Chính sách bảo mật thông tin (Chuẩn NĐ 13/2023/NĐ-CP & Facebook Login) |
| [`tabi-go/data-deletion.html`](file:///Users/quanghuy/human/3M/tabi-go/data-deletion.html) | Trang Hướng dẫn xóa dữ liệu người dùng Facebook (Meta Platform Policy) |
| [`tabi-go/vite.config.js`](file:///Users/quanghuy/human/3M/tabi-go/vite.config.js) | Cấu hình Vite Multi-Page Application (MPA) đóng gói cả 4 trang HTML |
| [`tabi-go/package.json`](file:///Users/quanghuy/human/3M/tabi-go/package.json) | Script build sản phẩm (`npm run build`) |
| [`tabi-go/assets/images/tabigo_app_icon_1024.png`](file:///Users/quanghuy/human/3M/tabi-go/assets/images/tabigo_app_icon_1024.png) | File ảnh App Icon 1024x1024 px nộp xét duyệt Meta Developer |
| [`tabi-go/.gitignore`](file:///Users/quanghuy/human/3M/tabi-go/.gitignore) | Loại bỏ `node_modules`, `dist` khỏi kho mã nguồn |

---

## 4. BẢNG TIÊU CHÍ NGHIỆM THU CHI TIẾT (DEFINITION OF DONE)

| Mã AC | Tiêu Chí Nghiệm Thu | Kết Quả Thực Tế | Trạng Thái |
| :--- | :--- | :--- | :---: |
| **AC-01** | **Hero Section Cân Đối 4:3** | Khung ảnh du khách Tokyo/Rome đạt chuẩn 4:3, ngập tràn ánh nắng ấm áp, hòa sắc 100% với nền Warm Almond Cream `#F5EFE6`. | 🟢 **PASS** |
| **AC-02** | **Khai Tử Video Rỗng** | Section How It Works chuyển thành 3 bước tinh gọn, phụ đề 1 dòng, không còn vùng đen gây hiểu nhầm. | 🟢 **PASS** |
| **AC-03** | **Support Hub Avatar Stack** | 3 Avatar chuyên viên hỗ trợ người thật lồng nhau kèm chấm xanh online 24/7 và kết nối Hotline/Zalo `0794.058.999`. | 🟢 **PASS** |
| **AC-04** | **Đồng Bộ Nút Bấm Hero** | Đồng bộ tuyệt đối chiều cao `44px` và bo góc `12px` giữa nút CTA chính cam và 2 nút Store đen. | 🟢 **PASS** |
| **AC-05** | **Mobile Navigation Drawer** | Thay thế thanh menu tràn bằng nút Hamburger và Off-canvas Drawer trượt mượt mà kèm công cụ tiền tệ. | 🟢 **PASS** |
| **AC-06** | **Trang Điều Khoản Dịch Vụ** | Đầy đủ 8 chính sách vận hành TabiGo, thanh mục lục dính cạnh ScrollSpy, giao diện sang trọng. | 🟢 **PASS** |
| **AC-07** | **Trang Chính Sách Bảo Mật** | Tuân thủ Nghị định 13/2023/NĐ-CP, bổ sung điều khoản xử lý dữ liệu Facebook Login. | 🟢 **PASS** |
| **AC-08** | **Trang Hướng Dẫn Xóa Dữ Liệu** | `data-deletion.html` hướng dẫn 2 cách gỡ quyền Facebook và xóa tài khoản TabiGo, chuẩn Meta Review. | 🟢 **PASS** |
| **AC-09** | **App Icon 1024x1024 px** | Xuất file PNG sắc nét, vuông vắn 1024x1024 px phục vụ nộp hồ sơ xét duyệt Meta. | 🟢 **PASS** |
| **AC-10** | **Vite Multi-Page Build** | Lệnh `npm run build` xuất đầy đủ 4 trang HTML vào `dist/`, không còn lỗi 404 khi deploy. | 🟢 **PASS** |
| **AC-11** | **Zero Syntax Error** | Kiểm tra cú pháp JavaScript & HTML toàn diện đạt 0 lỗi. | 🟢 **PASS** |
| **AC-12** | **Đồng Bộ Nhánh `main` GitLab** | Toàn bộ mã nguồn Version 2 được hợp nhất và đưa lên nhánh `main` chính thức của GitLab. | 🟢 **PASS** |

---

## 5. KẾT LUẬN & TRẠNG THÁI BÀN GIAO

Toàn bộ các tính năng, giao diện và tài liệu của **TabiGo Landing Page Version 2** đã được hoàn thiện xuất sắc và hợp nhất thành công vào nhánh **`main`** của kho lưu trữ GitLab:
`git@gitlab.human-life.vn:3m-app/tabigo-landing.git`

Hệ thống đã sẵn sàng cho việc nghiệm thu, đăng ký thẩm định với Bộ Công Thương và gửi xét duyệt ứng dụng trên Meta Developer Console.
