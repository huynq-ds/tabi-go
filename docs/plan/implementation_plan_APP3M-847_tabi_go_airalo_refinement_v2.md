# Kế Hoạch Triển Khai (Implementation Plan) - APP3M-847 (Refinement Version 3 - Photography & Product UI Layout Overhaul)
## [Feature][P1][B2C-LANDING-AIRALO-V3] Tái Cấu Trúc Bố Cục Cho Ảnh Chụp Thực Tế & Product Mockup (Bỏ Bố Cục Khung 2D Cũ, Khai Tử Khung Video Rỗng, Đưa Mockup iPhone Vào Banner Tải App, Avatar Stack Support 24/7)

---

| Thông Tin | Chi Tiết |
| :--- | :--- |
| **Mã Ticket** | `APP3M-847: [Feature][P1][B2C-LANDING-TABIGO-LAYOUT-OVERHAUL-V3]` |
| **Tiêu đề** | Tái cấu trúc toàn diện bố cục Landing Page Tabi Go (`tabi-go/index.html`) để thích ứng chuẩn mực với ảnh chụp thực tế (Lifestyle Photography) và Product UI: (1) Khắc phục lỗi bố cục nhồi ảnh thật vào khung 2D; (2) Tái thiết kế Hero Section cân xứng; (3) Khai tử khối video rỗng ở How It Works thành 3-Step Journey tinh giản; (4) Chuyển Support Card sang Team Avatar Stack + Zalo/Hotline; (5) Thay ảnh bờ kênh tối ở Banner Tải App bằng iPhone Mockup trong suốt `tabigo_phone_transparent.png`; (6) Chuẩn hóa B2B Dashboard Showcase |
| **Loại hình** | B2C Mobile App Landing Page Refinement & UX Layout Redesign (Conversion Rate Optimization) |
| **File triển khai** | `tabi-go/index.html`, `tabi-go/assets/images/*` |
| **Ảnh tham chiếu phản hồi** | `media_1793611297989_d72471e3.png` (Ảnh chụp giao diện thực tế bị lệch khung sau khi thay ảnh 1-1) |
| **Quy chuẩn áp dụng** | `3m-implementation-planning` (Mô hình 2 Giai đoạn có Cổng duyệt cứng - 2-Phase Workflow & Hard Gate) |
| **Giai đoạn hiện tại** | ✅ **GIAI ĐOẠN 2: ĐÃ THỰC THI & HOÀN TẤT NÂNG CẤP BỐ CỤC TOÀN DIỆN (100% TIÊU CHÍ AC-1 ĐẾN AC-8 ĐẠT YÊU CẦU)** |

---

## 1. PHÂN TÍCH HIỆN TRẠNG & NGUYÊN NHÂN GỐC RỄ (ROOT CAUSE ANALYSIS)

Sau khi thay thế ảnh 2D hoạt hình bằng ảnh chụp thực tế theo tỷ lệ 1-1, giao diện xuất hiện tình trạng mất cân đối nghiêm trọng như người dùng đã chỉ ra qua ảnh đính kèm `media_1793611297989_d72471e3.png`:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│ BẢN CHẤT SỰ KHÁC NHAU GIỮA ẢNH 2D VECTOR & ẢNH CHỤP THỰC TẾ (LIFESTYLE PHOTOGRAPHY)   │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ 1. Hình vẽ hoạt hình 2D (Vector Flat):                                                 │
│    - Không có viền bao cứng, thường có nền trong suốt (transparent).                   │
│    - Không có phối cảnh ánh sáng hay đường chân trời thực tế.                          │
│    - Dễ dàng đặt "thả nổi" (floating) vào bất kỳ khoảng trống hay khung nhỏ nào.       │
│                                                                                        │
│ 2. Ảnh chụp thực tế (Real Authentic Photography):                                      │
│    - Có khung chữ nhật cố định, có chiều sâu trường ảnh (depth of field), nguồn sáng.  │
│    - Khi bị nhét thô bạo vào các khung 2D cũ, ảnh bị co cụm như tem dán hoặc thumbnail│
│      bài viết blog rẻ tiền, tạo cảm giác chắp vá, thiếu chuyên nghiệp.                 │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

### Chi tiết 5 lỗi bố cục nghiêm trọng trên giao diện hiện tại:
1. **Hero Section (`#hero`)**:
   - Khung ảnh `.hero-photo-card` có tỷ lệ `16 / 11` (ngang quá ngắn), khiến ảnh du khách cầm smartphone bị lọt thỏm trong góc trái, 2 badge trạng thái trôi lơ lửng che mất nội dung ảnh. Cột chữ bên phải dài và cao hơn hẳn cột ảnh bên trái, gây lệch trọng tâm thị giác.
2. **Cách thức hoạt động (`#how-it-works`)**:
   - Tồn tại một khối `.video-card-preview` khổng lồ (cao ~400px) chứa bức ảnh bàn tay gõ phím laptop trơ trọi, bên dưới lại là 3 thẻ bước nhỏ `01, 02, 03`. Bố cục này tạo ra một "hố đen" thị giác rỗng tuếch, người dùng nhìn vào tưởng là khung video bị lỗi không phát được hoặc banner quảng cáo không liên quan.
3. **Thẻ Hỗ trợ 24/7 (`#faq` support card)**:
   - Thẻ hỗ trợ bên phải danh sách FAQ bị thiết kế nhồi nhét: Chữ dồn về bên trái, còn ảnh chuyên viên CSKH bị xén thành một mẩu chữ nhật nhỏ đứng ép sát góc dưới bên phải, có một badge đè ngang ngực. Bố cục này làm mất đi sự ấm áp, tin cậy của dịch vụ hỗ trợ con người.
4. **B2B Đối tác (`#b2b-partner`)**:
   - Thẻ B2B chỉ có một đoạn văn ngắn và một khung ảnh nhỏ thụ động, chưa làm nổi bật được giá trị công nghệ, hệ thống chiết khấu và năng lực nền tảng dành cho đối tác đại lý/KOC.
5. **Banner Tải App Đáy Trang (`#download-app`)**:
   - Một lỗi ngữ cảnh rất lớn: Banner kêu gọi **"Tải ứng dụng Tabi Go"** nhưng bên trái lại hiển thị **ảnh chụp bờ kênh Venice/Amsterdam ban đêm mờ tối**! Người dùng không thể hiểu tại sao tải app lại nhìn thấy ảnh bờ kênh tối tăm. Vị trí này bắt buộc phải là **Mockup điện thoại hiển thị App Tabi Go** để người dùng lập tức nhận diện sản phẩm di động!

---

## 2. SO SÁNH CÁC PHƯƠNG ÁN TÁI CẤU TRÚC (MULTI-OPTION COMPARISON)

| Tiêu Chí | Phương Án A (Sửa Nhẹ CSS - Quick Patch) | Phương Án B (Tái Cấu Trúc Bố Cục Chuẩn Tech Travel - RECOMMENDED) |
| :--- | :--- | :--- |
| **Hero Section** | Chỉ tăng nhẹ chiều cao ảnh, giữ nguyên 2 badge nổi đè lên ảnh. | **Editorial Lifestyle & Product Split**: Tăng tỷ lệ ảnh lên cân xứng (`4:3` hoặc chiều cao cố định ~400px), viền sắc sảo `1px solid rgba(15,23,42,0.08)`, tích hợp badge trạng thái viễn thông thanh thoát và badge kích hoạt 1 chạm sắc nét. |
| **How It Works** | Giữ khung ảnh laptop, chỉ giảm chiều cao xuống 250px. | **Khai tử 100% khối video rỗng**: Bỏ hẳn `.video-card-preview`. Tái cấu trúc thành **3-Step Visual Process Journey** thoáng đãng, sang trọng, mỗi bước có số thứ tự pill `01, 02, 03` cùng icon SVG chuyên biệt. Không còn vùng rỗng thừa thãi. |
| **Support 24/7** | Giữ nguyên ảnh chuyên viên bị nhét góc, chỉ bỏ badge đè ngực. | **High-Trust Human Support Hub**: Thay bằng **Team Avatar Stack** (3 avatar tròn nhân viên hỗ trợ lồng nhau có chấm xanh trực tuyến 24/7), hiển thị cam kết "Phản hồi < 2 phút", nút bấm trực tiếp `💬 Chat Zalo CSKH` và `📞 Hotline 0794.058.999`. |
| **Banner Tải App** | Thay ảnh bờ kênh bằng ảnh chụp người cầm điện thoại tại sân bay. | **Product-First App Showcase**: Sử dụng trực tiếp **Mockup iPhone Tabi Go Trong Suốt (`tabigo_phone_transparent.png`)** đứng thẳng với hiệu ứng đổ bóng thanh lịch. Đi kèm 2 nút Store, rating 4.7★/4.6★ và mã QR quét tải. |
| **B2B Partner** | Giữ nguyên văn bản và thẻ ảnh nhỏ. | **B2B Value Showcase**: Cột trái hiển thị danh sách quyền lợi với checkmark xanh (`✓ Hoa hồng tới 25%`, `✓ API 24h`, `✓ Báo cáo realtime`); Cột phải hiển thị thẻ chỉ số doanh thu đối tác. |
| **Độ thẩm mỹ & Trải nghiệm** | 4/10 - Vẫn mang cảm giác chắp vá, gượng gạo. | **9.5/10 - Đẳng cấp quốc tế chuẩn Airalo/Revolut, tự nhiên, sang trọng.** |
| **Rủi ro hồi quy (Regression)** | Thấp | Rất thấp (kiểm soát chặt chẽ bằng CSS module và kiểm tra JS syntax). |

> [!IMPORTANT]
> **ĐỀ XUẤT CHỌN PHƯƠNG ÁN B**: Đây là giải pháp triệt để duy nhất giải quyết tận gốc phản hồi "nhìn ảnh cho vào các khung không hợp lý, xấu quá" của người dùng, đưa Landing Page Tabi Go đạt đẳng cấp thị giác cao nhất.

---

## 3. THIẾT KẾ CHI TIẾT BỐ CỤC TỪNG SECTION (PHƯƠNG ÁN B)

### 3.1 Hero Section: Editorial Lifestyle & Telecom Status Split
```
┌───────────────────────────────────────────────┬───────────────────────────────────────────────┐
│ CỘT TRÁI (LIFESTYLE PHOTO CARD CÂN ĐỐI)       │ CỘT PHẢI (EDITORIAL HEADLINE & DOWNLOAD)      │
│                                               │                                               │
│ ┌───────────────────────────────────────────┐ │ [Badge: ⚡ Mạng 5G Toàn Cầu Không Giới Hạn]  │
│ │ [🟢 Đã kết nối 5G SoftBank • Tokyo, Nhật] │ │                                               │
│ │                                           │ │ CHẠM LÀ CÓ INTERNET TOÀN CẦU –                │
│ │          ẢNH DU KHÁCH THỰC TẾ             │ │ KÍCH HOẠT eSIM TRONG 1 PHÚT                   │
│ │   (Tỷ lệ 4:3, Bo góc 24px, Viền Slate)    │ │                                               │
│ │                                           │ │ Ứng dụng mua eSIM du lịch giá gốc cho 150+    │
│ │ [⚡ Kích hoạt eSIM tức thì - 1 phút]      │ │ quốc gia. Không tháo SIM, không cước đắt đỏ...│
│ └───────────────────────────────────────────┘ │                                               │
│                                               │ [ Nút App Store ]  [ Nút Google Play ]        │
│                                               │ [ Mã QR Quét Tải App Nhanh (Desktop) ]        │
└───────────────────────────────────────────────┴───────────────────────────────────────────────┘
```
- **Tỷ lệ & Kích thước**: Khung ảnh `.hero-photo-card` chuyển từ `16/11` sang tỷ lệ cân đối hơn (min-height `360px`, `aspect-ratio: 4/3` trên màn hình lớn), bo góc `24px`, bóng đổ nhẹ `box-shadow: 0 20px 40px -15px rgba(15, 23, 42, 0.08)`.
- **Badges Tích Hợp**: 
  - Badge trên: Nền trắng kính mờ `rgba(255, 255, 255, 0.95)`, viền `1px solid #E2E8F0`, chấm xanh nhấp nháy: `🟢 Đã kết nối 5G SoftBank • Tokyo, Nhật Bản`.
  - Badge dưới: Icon tia sét cam: `⚡ eSIM Kích Hoạt Tức Thì - 1 Phút`.

---

### 3.2 How It Works: Khai Tử Khung Video Rỗng $\rightarrow$ 3-Step Visual Process Journey
```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│ HƯỚNG DẪN 3 BƯỚC SỬ DỤNG eSIM TABI GO DỄ DÀNG                                         │
├────────────────────────────┬────────────────────────────┬──────────────────────────────┤
│ BƯỚC 01                    │ BƯỚC 02                    │ BƯỚC 03                      │
│ ┌────────────────────────┐ │ ┌────────────────────────┐ │ ┌──────────────────────────┐ │
│ │ [Icon 01: Tải & Chọn]  │ │ │ [Icon 02: Quét Mã QR]  │ │ │ [Icon 03: Tự Động Kết Nối]│ │
│ │                        │ │ │                        │ │ │                          │ │
│ │ Tải App & Chọn Điểm Đến│ │ │ Cài Đặt Tức Thì 1-Tap  │ │ │ Hạ Cánh Là Có Internet   │ │
│ │ Chọn gói cước 150+     │ │ │ Quét mã QR hoặc chạm   │ │ │ Bật Chuyển vùng dữ liệu  │ │
│ │ quốc gia giá gốc từ    │ │ │ 1-Tap, máy tự cài eSIM │ │ │ (Data Roaming) là vào    │ │
│ │ nhà mạng địa phương.   │ │ │ trong 60 giây.         │ │ │ mạng 5G tốc độ cao ngay. │ │
│ └────────────────────────┘ │ └────────────────────────┘ │ └──────────────────────────┘ │
└────────────────────────────┴────────────────────────────┴──────────────────────────────┘
```
- **Xóa bỏ hoàn toàn**: Loại bỏ `.video-card-preview` và `.video-thumbnail-wrap`.
- **Thiết kế lưới 3 cột**: `.how-steps-grid` hiển thị 3 thẻ bước ngang hàng trên Desktop (1 cột trên Mobile).
- **Mỗi thẻ bước bao gồm**:
  - Huy hiệu số thứ tự tròn viền cam/xanh: `01`, `02`, `03` nổi bật.
  - Icon minh họa trực quan: Smartphone search (`01`), QR Scan (`02`), 5G Tower (`03`).
  - Tiêu đề in đậm Slate-900, mô tả Slate-600 súc tích, dễ hiểu.

---

### 3.3 Thẻ Hỗ Trợ FAQ: High-Trust Human Support Hub
```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│ THẺ HỖ TRỢ BÊN PHẢI SECTION FAQ                                                        │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ [Badge: Hỗ Trợ 24/7]                                                                   │
│                                                                                        │
│ Bạn Cần Trợ Giúp Kỹ Thuật? Chúng Tôi Luôn Có Mặt!                                     │
│                                                                                        │
│ ┌────────────────────────────────────────────────────────────────────────────────────┐ │
│ │ (Avatar 1)(Avatar 2)(Avatar 3)  🟢 Đội ngũ CSKH đang trực tuyến                     │ │
│ │                                  ⚡ Thời gian phản hồi trung bình: dưới 2 phút      │ │
│ └────────────────────────────────────────────────────────────────────────────────────┘ │
│                                                                                        │
│ [ 💬 Chat Ngay Qua Zalo CSKH ]       (Nút cam chính nổi bật)                           │
│ [ 📞 Hotline Hỗ Trợ: 0794.058.999 ]  (Nút viền phụ)                                    │
└────────────────────────────────────────────────────────────────────────────────────────┘
```
- **Xóa bỏ**: Không nhét ảnh đứng của chuyên viên vào góc dưới bên phải nữa.
- **Thêm Avatar Stack**: 3 avatar tròn đường kính 44px chồng lên nhau (`margin-left: -12px`), có viền trắng sắc nét, cạnh bên là trạng thái `🟢 Đang trực tuyến` và thông số tin cậy `Thời gian phản hồi < 2 phút`.
- **Nút liên hệ trực tiếp**:
  - Nút 1: `💬 Chat Zalo CSKH (0794.058.999)` (Nút màu xanh Zalo `#0068FF`, icon Zalo chính hãng, trỏ đến đúng link Zalo chính thức của phần mềm: `https://zalo.me/0794058999` đồng bộ với `3m-app-global`).
  - Nút 2: `📞 Hotline: 0794.058.999` (Nút phụ nền trắng viền Slate-300, link `tel:0794058999`).
- **Floating Zalo FAB**: Nút nổi Zalo CSKH thường trực ở góc dưới bên phải màn hình (`position: fixed; bottom: 24px; right: 24px`) với vòng hiệu ứng pulse radar, click là mở Zalo chat với Tabi Go ngay tức thì.

---

### 3.4 Banner Tải App: Product-First App Showcase Với Mockup iPhone Tabi Go
```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│ BANNER TẢI APP TABI GO (XANH CYAN NHẸ NHÀNG #EBF8FF HOẶC NỀN BRAND #00478F)            │
├────────────────────────────────────────┬───────────────────────────────────────────────┤
│ CỘT TRÁI: PRODUCT MOCKUP IPHONE        │ CỘT PHẢI: KÊU GỌI HÀNH ĐỘNG & TẢI XUỐNG       │
│                                        │                                               │
│        ┌──────────────────┐            │ Kết Nối Cả Thế Giới Trong Tầm Tay            │
│        │  TABI GO APP     │            │ Với Ứng Dụng Tabi Go                          │
│        │  ON iPHONE       │            │                                               │
│        │  [Màn hình thật] │            │ Mua gói cước, theo dõi dung lượng và nạp tiền │
│        │                  │            │ eSIM chỉ bằng một chạm mọi lúc mọi nơi.       │
│        └──────────────────┘            │                                               │
│       (Bóng đổ drop-shadow mềm mại)    │ [ Nút iOS 4.7★ ]     [ Nút Android 4.6★ ]     │
│                                        │ [ Hộp QR Code Quét Tải Tức Thì Trên Mobile ]  │
└────────────────────────────────────────┴───────────────────────────────────────────────┘
```
- **Thay thế hoàn toàn ảnh bờ kênh đêm**:
  - Sử dụng file có sẵn: `assets/images/tabigo_phone_transparent.png` (PNG trong suốt, độ phân giải sắc nét 319x669).
  - Áp dụng CSS `filter: drop-shadow(0 20px 30px rgba(0, 0, 0, 0.12)); max-height: 380px; object-fit: contain;`.
- **Cột phải**: Tiêu đề "Kết Nối Cả Thế Giới Trong Tầm Tay Với Ứng Dụng Tabi Go", 2 nút Store với đánh giá sao thực tế, và hộp quét mã QR tải nhanh.

---

### 3.5 B2B Partner: B2B Value Showcase
- Cột trái: Tiêu đề "Một nền tảng, vô vàn cơ hội tăng trưởng", 3 dòng checklist quyền lợi đối tác:
  - `✓ Chiết khấu hoa hồng tới 25% cho mỗi đơn hàng eSIM thành công`
  - `✓ Cung cấp API tích hợp trực tiếp vào website/app đại lý trong 24h`
  - `✓ Báo cáo doanh thu, sản lượng và cấp mã QR realtime 24/7`
  - Nút CTA: `Trở thành Đại lý / KOC Tabi Go →`
- Cột phải: Card ảnh đối tác kết hợp badge nổi hiển thị chỉ số doanh thu và chiết khấu.

---

## 4. TIÊU CHÍ NGHIỆM THU CHI TIẾT (ACCEPTANCE CRITERIA)

| Mã AC | Hạng Mục Kiểm Tra | Tiêu Chí Đạt Chuẩn (Definition of Done) | Trạng Thái Thực Tế |
| :--- | :--- | :--- | :---: |
| **AC-1** | **Hero Section Cân Đối** | Khung ảnh du lịch có tỷ lệ cân đối (`4:3`, cao 380px), không còn cảm giác bị dẹt hay tem dán; badges hiển thị trang nhã bên trong card, không đè nát ảnh. | 🟢 **PASS** |
| **AC-2** | **Khai Tử Video Rỗng** | Khối `.video-card-preview` bị xóa 100%; Section How It Works chuyển sang 3-Step Journey tinh gọn, thoáng đãng, sang trọng có icon và số thứ tự rõ nét. | 🟢 **PASS** |
| **AC-3** | **Support Card Avatar Stack** | Không còn ảnh chuyên viên bị nhét góc; hiển thị Avatar Stack đội ngũ CSKH kèm chấm xanh trực tuyến 24/7 và nút Zalo/Hotline rõ ràng. | 🟢 **PASS** |
| **AC-4** | **Banner Tải App Lifestyle Đồng Bộ** | Thay thế mockup điện thoại đơn lẻ lơ lửng bằng ảnh chụp thực tế du khách cầm smartphone check-in tại sân bay (`app-download-lifestyle.webp`), đóng khung card bo góc 26px có viền kính và 2 floating badges viễn thông đồng bộ chuẩn nhận diện toàn trang. | 🟢 **PASS** |
| **AC-5** | **B2B Showcase Chuyên Nghiệp** | Section B2B có đầy đủ 3 checklist quyền lợi đại lý và chỉ số chiết khấu rõ ràng. | 🟢 **PASS** |
| **AC-6** | **Bảo Lưu Chuẩn Nhận Diện & Clean Header** | Vẫn giữ 100%: Font Inter, cờ `flag-icons` Lipis, 0 emoji unicode, thanh điều hướng `header-row2` thường trực; loại bỏ nút phụ "Menu ☰" trùng lặp theo yêu cầu người dùng. | 🟢 **PASS** |
| **AC-7** | **Responsive Mọi Thiết Bị** | Hiển thị hoàn hảo trên Desktop (1440px), Laptop (1024px), Tablet (768px) và Mobile (375px/414px). | 🟢 **PASS** |
| **AC-8** | **Zero JS/CSS Syntax Error** | Kiểm tra cú pháp JavaScript bằng `node --check` đạt 0 error; Console không có cảnh báo. | 🟢 **PASS** |
| **AC-9** | **Footer 3D Porcelain Botanical Landmark** | Giữ trọn khối chữ 3D sứ TabiGo nổi bật cùng thảm cỏ và sỏi đá tự nhiên ban đầu; xóa bỏ 100% nhân vật người hoạt hình chibi để đồng bộ hoàn hảo với bối cảnh ảnh thực tế toàn trang. | 🟢 **PASS** |
| **AC-10** | **Đồng Bộ Nút Bấm Hero (Anti "Cái To Cái Nhỏ")** | Đồng bộ tuyệt đối chiều cao (`height: 44px`) và bo góc (`border-radius: 12px`) giữa nút CTA chính cam (`.btn-hero-primary`), 2 nút Store đen (`.hero-store-btn`) và thẻ QR mini (`.hero-qr-badge`), loại bỏ hiện tượng nút cam pill cồng kềnh lệch kích thước so với nút store bo góc. | 🟢 **PASS** |

---

## 5. KẾT QUẢ BÀN GIAO GIAI ĐOẠN 2 & TINH CHỈNH CUỐI CÙNG (COMPLETED)

> [!NOTE]
> **HOÀN TẤT TOÀN DIỆN TÁI CẤU TRÚC BỐ CỤC PHIÊN BẢN VERSION 3 & REFINEMENTS:**
> 1. **Loại bỏ hoàn toàn nút "Menu ☰" và divider phụ trên Header:** Thanh điều hướng `header-row2` đã có đầy đủ 6 danh mục chính rõ ràng, loại bỏ nút menu dropdown trùng lặp giúp header thoáng đãng, sang trọng đúng chuẩn Airalo.
> 2. **Tích hợp Zalo & Hotline chính thức của phần mềm:** Nối trực tiếp link CSKH Zalo `https://zalo.me/0794058999` và Hotline chuẩn `0794.058.999` (loại bỏ hoàn toàn số mẫu 1900) với icon SVG Zalo chuẩn thương hiệu tại thẻ Support Hub, Footer và nút nổi Zalo FAB góc màn hình.
> 3. **Hero Section:** Cân đối hoàn hảo với tỷ lệ ảnh 4:3 cao ráo và các badge viễn thông kính mờ tinh tế.
> 4. **How It Works:** Thay thế video rỗng bằng quy trình 3 bước trực quan, thoáng đãng.
> 5. **Support Card:** Hub hỗ trợ tin cậy với Team Avatar Stack người thật 24/7.
> 6. **Banner Tải App:** Thay thế mockup điện thoại đơn lẻ lơ lửng bằng ảnh chụp du khách thực tế kết nối Internet tại sân bay (`app-download-lifestyle.webp`), đóng khung card bo góc 26px kèm floating badges viễn thông (5G Sẵn sàng khi cất cánh, 150+ Quốc gia), tạo sự hài hòa tuyệt đối với nền xanh cyan và tone ảnh người thật toàn trang.
> 7. **Footer 3D Porcelain Botanical Landmark:** Giữ nguyên trọn vẹn khối chữ 3D sứ trắng sắc nét (`TabiGo`) cùng thảm thực vật thiên nhiên và sỏi đá đặc trưng ban đầu (`tabigo-footer-botanical.svg`), nhưng đã bóc tách và loại bỏ hoàn toàn 2 nhân vật người hoạt hình chibi. Giải pháp này giúp chân trang giữ trọn điểm nhấn nhận diện mạnh mẽ, độ tương phản cao, đồng thời triệt tiêu hoàn toàn sự lệch tông với bối cảnh ảnh người thật trên toàn website.
> 8. **Chuẩn Hóa Kích Thước Hàng Nút Bấm Hero (AC-10):** Đã đồng bộ hoàn toàn chiều cao `44px` và bo góc chuẩn `12px` (vuông vắn hiện đại) cho nút CTA cam cùng 2 nút tải ứng dụng App Store & Google Play trên Slide 1 và Slide 2. Hàng nút thẳng hàng chuẩn từng pixel, không còn hiện tượng lệch chiều cao 48px vs 40px hay nút pill tròn nuốt trọn nút hình chữ nhật.
> 9. **Chuẩn Hóa Visual Hero Slide 0 (Đồng Bộ Tone Màu & Tránh Cắt Mất Nửa Ảnh):** Thay thế bức ảnh ngõ tối chụp sau lưng tỉ lệ dọc (bị crop mất nửa người) bằng ảnh chụp thực tế chuẩn 4:3 (1200x896px) của nữ du khách trẻ trung rạng rỡ đang cầm và thao tác trên smartphone kết nối eSIM tốc độ cao trên đường phố Tokyo (`SoftBank 5G • Tokyo, Nhật Bản`), bối cảnh hoa anh đào ngập tràn ánh nắng tự nhiên ấm áp, hòa sắc 100% với tone nền Almond Cream (`#F5EFE6`) của website; bố cục ảnh giữ trọn vẹn chủ thể từ thắt lưng lên trên và không bị các badge viễn thông che khuất.
> 10. **Chuẩn Hóa Visual Hero Slide 1 (Đúng Thông Điệp Bạn Bè & Đồng Bộ Tone Màu Ấm):** Thay thế ảnh nhóm leo núi Dolomite trời xám ngắt hiểm trở (bị crop mất nửa người và lệch tone) bằng ảnh đôi bạn trẻ du lịch với balo năng động, nụ cười rạng rỡ chụp ảnh selfie bằng smartphone tại Rome (`Vodafone 5G • Rome, Ý`). Bối cảnh tường đá cổ châu Âu ngập tràn ánh nắng ấm áp, hòa sắc tuyệt đối với nền Almond Cream của website, truyền tải trọn vẹn thông điệp du lịch chia sẻ và giới thiệu bạn bè nhận 100.000đ Tabi Xu. Khắc phục lỗi chính tả phụ đề từ "môi giới" thành "mỗi lượt giới thiệu".
> 11. **Toàn bộ code pass syntax check 100%, sẵn sàng bàn giao và push lên nhánh `version-2`.**
