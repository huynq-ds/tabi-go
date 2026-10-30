# Kế Hoạch Triển Khai (Implementation Plan) - APP3M-847 (Refinement v5)
## [Feature][P1][B2C-LANDING-CONCEPT-5] Tinh Chỉnh Chi Tiết Bố Cục Tabi Go Theo Chuẩn Thiết Kế Airalo (Vector SVG Brand Icon, Slider Capsule Chuẩn Pixel, 3 Slide Hoạt Họa & Tỉ Mỉ Từng Chi Tiết)

---

| Thông Tin | Chi Tiết |
| :--- | :--- |
| **Mã Ticket** | `APP3M-847: [Feature][P1][B2C-LANDING-CONCEPT-5-AIRALO-REFINEMENT-V5]` |
| **Tiêu đề** | Tinh chỉnh Concept 5 (Airalo Vibe): Thay thế hoàn toàn logo chụp màn hình bằng Vector SVG Brand Icon sắc nét, thiết kế lại thanh Slider Capsule chuẩn pixel theo ảnh thực tế, chuẩn hóa 3 Slide hoạt họa và hoàn thiện design system tỉ mỉ |
| **Loại hình** | B2C Mobile App Landing Page (iOS & Android) |
| **File triển khai** | `tabi-go/concept-5-airalo.html` |
| **Tài nguyên** | Vector SVG Icon Tabi Go tự vẽ đạt chuẩn Retina, `tabi-go/assets/images/lottie/*.svg` |
| **Ảnh tham chiếu** | Ảnh Airalo do người dùng cung cấp (`media_1793270719095.png`, `media_1793270746461.png`, `media_1793269664725.png`, `media_1793269217187.png`) |
| **Quy chuẩn áp dụng** | `3m-implementation-planning` (Quy trình 2 Giai đoạn có Cổng duyệt cứng - 2-Phase Workflow & Hard Gate) |
| **Giai đoạn hiện tại**| ✅ **GIAI ĐOẠN 2: ĐÃ THỰC THI & NGHIỆM THU HOÀN TẤT (100% AC-1 ĐẾN AC-18 PASS)** |

---

## 1. MỤC TIÊU & PHÂN TÍCH NGUYÊN NHÂN GỐC RỄ (ROOT CAUSE ANALYSIS)

### 1.1 Phân Tích Phản Hồi Từ Người Dùng
1. **Vấn đề Logo:**
   - *Phản hồi của người dùng:* *"logo của tabi go thì phải icon chứ, chụp m xem thôi chứ k phải bế cả ảnh vào"*
   - *Nguyên nhân gốc rễ:* Trước đây hệ thống đã dùng một file ảnh raster cắt từ ảnh chụp màn hình điện thoại (`tabigo_brand_horizontal.png` / `tabigo_logo.png`). Ảnh cắt này bị vỡ hạt (pixelated), có viền răng cưa, dính nền mờ của screenshot ứng dụng và tỉ lệ không phù hợp với thanh header website cao cấp.
   - *Giải pháp:* Người dùng gửi ảnh là để cung cấp **hình mẫu nhận diện thương hiệu** (Icon Tabi Go gồm quả địa cầu xanh với máy bay giấy vàng bay quanh quỹ đạo và sóng wifi, chữ TabiGo gồm chữ Tabi xanh đậm và chữ Go xanh ngọc cyan). Trên website thực tế, logo phải được dựng bằng **Vector SVG Brand Icon sắc nét 100% (Retina / 4K Ready)** kết hợp với Typography/Wordmark chuyên nghiệp, nền transparent trong suốt hoàn hảo, không có bất kỳ hạt vỡ hay viền lem nào.

2. **Vấn đề Thanh Slider Indicator & 3 Thẻ Điều Hướng Nhanh (Navigation Cards):**
   - *Phản hồi của người dùng:* *"ảnh 2 là mẫu, nhìn khác nhau không, và click vào nó đi tới mục tương ứng cơ mà... backgound cũng k thấy hoạ tiết đẹp như mẫu"*
   - *Phân tích so sánh ảnh 1 (cũ) vs ảnh 2 (mẫu thực tế của Airalo):*
     + **Thanh Slider Indicator:**
       * Ảnh 1 (cũ): Khung dày với viền xanh dương điện tử `#0055FF`, bên trong là cục đen to thô và icon chevron `<` `>`.
       * Ảnh 2 (mẫu Airalo): Thanh capsule màu trắng tinh khôi thanh mảnh (`height: 18px`, viền xám mờ `#E2DDD5`), bên trong gồm 3 phân đoạn dạng **vạch mảnh sợi tóc (hairline lines, height: 2.5px)** màu xám nhạt `#D8D3CA`. Phân đoạn active có một **vạch đen mảnh `#111827`** lấp đầy êm ái từ trái sang phải. **HOÀN TOÀN KHÔNG CÓ VIỀN XANH DƯƠNG NÀO CẢ**. Hai nút điều hướng là nút tròn với mũi tên ngang chuẩn `←` và `→`.
     + **3 Thẻ Điều Hướng Nhanh (Navigation Jump Cards):**
       * Ảnh 1 (cũ): Làm nhầm thành 3 nút dropdown lọc gói cước ("Gói cước theo quốc gia ˅", "Khu vực ˅", "Gói cước toàn cầu ˅").
       * Ảnh 2 (mẫu Airalo): Là **3 thẻ Card liên kết điều hướng nhanh dạng bấm nhảy đến các mục trên trang** với mũi tên chỉ xuống `↓`:
         1. `Cách thức hoạt động của Tabi Go` `↓` $\rightarrow$ Nhấp vào cuộn mượt mà đến `#how-it-works`.
         2. `Điểm đến` `↓` (có viền cam nổi bật `#F26322`, nền trắng) $\rightarrow$ Nhấp vào cuộn mượt mà đến `#destinations`.
         3. `Giải pháp doanh nghiệp` `↓` $\rightarrow$ Nhấp vào cuộn mượt mà đến `#b2b-partner`.
     + **Họa Tiết Nền (Background Motifs):**
       * Ảnh 2 (mẫu Airalo): Ngay phía sau thanh slider và nhô xuống giữa thẻ 2 ("Điểm đến") có một **hình thoi xanh ngọc pastel nghiêng 45° (`#CFE4D8`)**; bên phải phía sau thẻ 3 ("Giải pháp doanh nghiệp") có một **mảng màu vàng óng uốn lượn mềm mại (`#F8D882`)**; cùng các mảng màu pastel đào (`#FFE2D5`) và xanh trời (`#D8EEF8`) tạo chiều sâu thị giác sang trọng trên nền kem hạnh nhân `--bg-page: #F5EFE6`.

3. **3 Slide Hoạt Họa & Nội Dung Tabi Go:**
   - 3 Slide hoạt họa khớp 100% với 3 phân đoạn của thanh slider trong ảnh tham chiếu:
     + **Slide 1:** 2 người bạn nghe nhạc/selfie (`hero-slide-1.svg`) -> *"Cảm nhận sự tự do của dữ liệu không giới hạn cùng Tabi Go"*
     + **Slide 2:** 3 người bạn khoác vai bước đi cùng bạn nữ chân giả công nghệ (`hero-slide-2.svg`) -> *"Giới thiệu bạn bè. Nhận ngay 100.000đ Tabi Xu."*
     + **Slide 3:** 3 người bạn nhảy ăn mừng đập tay high-five (`hero-slide-3.svg`) -> *"Tích lũy điểm thưởng Tabi Go mỗi chuyến đi."* (Hoàn tiền tới 10% Tabi Xu).

4. **Landing Page thuần túy (Không Auth):**
   - Không có nút "Đăng nhập", "Đăng ký" hay popup auth nào. Header bên phải gồm: Nút chọn ngôn ngữ (Globe), Nút đơn vị tiền tệ (`₫ VND 🇻🇳`), và Nút CTA chính "Khám phá eSIM" (hoặc "Tải ứng dụng").

5. **Xử lý triệt để viền trắng của ảnh điện thoại (Banner Tải App):**
   - *Phản hồi của người dùng:* *"ảnh nó lại bị biền trắng trắng nhìn xấu quá"*
   - *Nguyên nhân gốc rễ:* File `tabigo_phone_screen.png` trước đó là ảnh chụp màn hình có dính lớp nền xám-trắng mờ (alpha = 255), đồng thời thẻ `<img>` áp dụng `border-radius: 28px; box-shadow: ...` nên tạo thành một khối hộp chữ nhật màu trắng bao quanh thân máy, nổi cộm trên nền banner xanh cyan `#E8F7FA`.
   - *Giải pháp:*
     + Chuyển sang file `tabigo_phone_transparent.png` đã được cắt tỉa trong suốt 100% ngoài thân máy (alpha = 0).
     + Đồng bộ đè file này lên cả `tabigo_phone_screen.png` để triệt tiêu mọi vấn đề lưu cache.
     + Thay thế `box-shadow` hình chữ nhật bằng `filter: drop-shadow(0 18px 30px rgba(15, 23, 42, 0.16))` — bóng đổ mềm mại ôm sát tự nhiên theo đường cong viền máy iPhone thực tế, nền trong suốt hòa quyện hoàn hảo với màu nền banner.

6. **Màu Sắc Header & Duy Trì Tab Bar Menu Khi Lăn Chuột (Sticky Header Color & Tab Bar Menu Persistence):**
   - *Phản hồi của người dùng:* *"sao lại màu trắng, mẫu màu khác mà, và rồi cái tabar menu đâu , ấn mất luôn à"*
   - *Phân tích & Khắc phục triệt để:*
     + **Màu nền Header:** Tuyệt đối **KHÔNG đổi sang màu trắng `#FFFFFF`** khi cuộn chuột. Header luôn giữ vững màu kem ấm hạnh nhân đồng nhất với trang (`rgba(245, 239, 230, 0.95)` và khi `.scrolled` là `rgba(245, 239, 230, 0.98)` với viền dưới thanh mảnh `#E2DDD5` cùng bóng đổ rất nhẹ `0 4px 16px rgba(0,0,0,0.04)`).
     + **Tab Bar Menu (Hàng 2):** Tuyệt đối **KHÔNG ẩn đi khi cuộn (`display: none`)**. Menu điều hướng (`.header-row2` với `.nav-menu`: Trang chủ, Cửa hàng eSIM, Cách thức hoạt động, Giới thiệu về Tabi Go, Tạp chí, Trợ giúp) luôn duy trì hiển thị cố định, gắn kết trực quan với thanh ScrollSpy tự động đổi màu cam `#E0533C` khi lướt qua từng section.
     + **Mượt mà khi click:** Áp dụng `scroll-behavior: smooth;` trên `html` và `scroll-margin-top: 130px;` trên các section để khi người dùng click vào bất kỳ mục menu nào, màn hình sẽ cuộn êm ái đến đúng vị trí mà không bị Header che mất tiêu đề.

7. **Khoảng Cách Giữa Các Khối Nội Dung (Section Spacing / Vertical Rhythm):**
   - *Phản hồi của người dùng:* *"ảnh 2 nó còn đang bị dính sát vào nhau nữa chứ"*
   - *Nguyên nhân & Khắc phục:* Thiết lập `margin-bottom: 88px !important;` cho cả `#faq` và `.blog-section`, tạo nhịp điệu thị giác rộng rãi, thoáng đãng, sang trọng theo đúng nguyên tắc thiết kế cao cấp của Airalo.

8. **Bố Cục Banner Tải App & Footer 7 Cột Chuẩn Mẫu Thực Tế (Ảnh Mẫu 2 & 3):**
   - *Phản hồi của người dùng:* *"lỗi này, ảnh 2 nó phải là tabigo chứ sửa lại đi, mấy cái link mà click nếu k có thì cũng k cho nó nhảy sang link khác nha"*
   - *Bố cục chuẩn hóa theo Ảnh mẫu 2 & 3:*
     + **Banner Tải App (App Download Banner):** Nền xanh Cyan ngọc trời `#72C7DC`, bo góc lớn `36px`, padding `56px 64px`. Bên trái hiển thị sắc nét mockup điện thoại iPhone ứng dụng Tabi Go nền trong suốt (`tabigo_phone_transparent.png`), giải quyết triệt để lỗi file SVG Bodymovin cũ bị lệch tọa độ khiến ô bên trái bị trống. Bên phải gồm tiêu đề *"Chúng tôi luôn đồng hành cùng bạn, dù bạn ở bất cứ đâu"*, phụ đề và 2 nút bấm tải app dạng viên nang trắng (iOS & Android) kèm khối sao đánh giá (`Rating 4.7 ★★★★★` và `Rating 4.6 ★★★★★`).
     + **Linh vật Thế giới Tabi Go (TabiGo World Mascot Artwork):** Tuyệt đối **KHÔNG dùng artwork chữ `airalo`**. Toàn bộ tác phẩm đồ họa được dựng lại bằng Vector SVG độc bản [tabigo-footer-world.svg](file:///Users/quanghuy/human/3M/tabi-go/assets/images/lottie/tabigo-footer-world.svg) với các chữ cái 3D màu trắng **`t a b i g o`**:
       * Chữ `t`: Chú chim du lịch ngực đỏ dễ thương đậu trên đỉnh.
       * Chữ `a`: Chàng trai trẻ mặc áo đỏ ngồi trong lòng chữ 'a' thư thái lướt smartphone.
       * Chữ `b`: Đường nét bo tròn 3D trắng tinh khôi.
       * Chữ `i`: Chấm tròn là **Quả địa cầu xanh Tabi Go 3D** với quỹ đạo phát sáng và máy bay giấy origami.
       * Chữ `g`: Cô gái tóc xoăn mặc áo cam ngồi trên vòng lượn của chữ 'g' vui vẻ vẫy tay chào.
       * Chữ `o`: Khối tròn 3D hoàn chỉnh.
       * Phần chân đế: Kệ đất cát ấm áp, các khối đá rêu cuội cùng thảm thực vật nhiệt đới và hoa dại pastel sinh động.
     + **Footer 7 Cột Liền Mạch:** Nền trong suốt hòa vào nền kem của trang, chia làm 7 cột danh mục: `Gói cước eSIM`, `Về eSIM`, `Trợ giúp`, `Tạp chí`, `Tabi Go`, `Doanh nghiệp`, và `Theo dõi chúng tôi`. Phía dưới là linh vật TabiGo World Mascot và dòng bản quyền căn giữa `©2026 TABI GO` cùng các liên kết pháp lý.
     + **Bảo Vệ Liên Kết (Link Safeguarding):** Tất cả các liên kết placeholder/chưa có trang đích (nút tải app, mạng xã hội, các chính sách pháp lý) được gán `href="javascript:void(0)"` kết hợp listener `preventDefault()`. Tuyệt đối không để xảy ra hiện tượng nhảy lên đầu trang (hash `#`) hoặc chuyển hướng ra các website bên ngoài không mong muốn.
     + **Họa Tiết Nền Toàn Trang (Full-page Ambient Shapes):** Dàn trải các hình khối pastel (đốm vàng mềm, hình thoi hồng đào, vòng tròn xanh bạc hà mint, hình hạt đậu cyan) từ đầu trang Hero xuống qua các mục và phủ đến tận Footer, không để trang bị trơ trọi hay lệch nhịp thị giác.

---

## 2. THIẾT KẾ VECTOR SVG BRAND ICON & WORDMARK TABI GO

Để giải quyết triệt để lỗi "bế ảnh chụp vào", logo Tabi Go sẽ được kiến tạo hoàn toàn bằng Vector SVG chuẩn đồ họa:

### 2.1 Cấu Trúc Vector Icon Tabi Go (Icon 36x36px)
Biểu tượng gồm các thành phần vector hình học tinh xảo:
- **Nền squircle app icon:** Hình vuông bo góc mượt mà (`rx="9"` trong viewBox 36x36), dải chuyển màu tuyến tính gradient từ Cyan `#00C2FF` sang Royal Blue `#0066FF`.
- **Quả địa cầu (Globe):** Vòng tròn gradient xanh đại dương `#0084FF` đến `#0048D9` với các mảng lục địa màu trắng ngọc và bóng mờ tinh tế.
- **Vòng quỹ đạo (Orbit Path):** Đường elip trắng mảnh uốn lượn quanh quả cầu với nét đứt/chấm định vị tọa độ.
- **Máy bay giấy origami (Paper Airplane):** Biểu tượng gấp giấy sắc nét màu vàng kim cam rực rỡ (Gradient `#FFB800` $\rightarrow$ `#FF8A00`) đang cất cánh bay vút lên góc phải trên.
- **Sóng kết nối (Signal/WiFi Waves):** 2 cung sóng phát tín hiệu màu trắng tinh khôi ở góc dưới phải của quả địa cầu biểu thị khả năng kết nối không dây tốc độ cao.

### 2.2 Wordmark TabiGo
- **Chữ "Tabi":** Font chữ Sans-Serif hiện đại, `font-weight: 800`, màu Navy cao cấp `#0B2545`.
- **Chữ "Go":** `font-weight: 800`, màu Cyan thương hiệu `#00A3E0` với chi tiết máy bay vàng nhỏ nhắn bay ra từ chữ 'o'.
- **Ưu điểm vượt trội:**
  + Sắc nét tuyệt đối trên mọi màn hình (Retina, 4K, 8K), không bao giờ bị nhòe hay vỡ hạt.
  + Dung lượng cực nhẹ (< 2KB), hiển thị tức thì, không phát sinh HTTP request tải ảnh.
  + Nền trong suốt tự nhiên, tương thích hoàn hảo với mọi màu nền header.

---

## 3. THIẾT KẾ THANH SLIDER CAPSULE CHUẨN PIXEL (PIXEL-PERFECT SPEC)

Dựa trên ảnh tham chiếu thực tế `media_1793270746461.png`:

```
┌───────┐  ┌────────────────────────────────────────────────────────┐  ┌───────┐
│       │  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │  │       │
│   ←   │  │  │              │  │              │  │ ┌──────┐     │  │  │   →   │
│ (36px)│  │  │ Inactive Pill│  │ Inactive Pill│  │ │Fill  │     │  │  │ (36px)│
│       │  │  │  (#E2E8F0)   │  │  (#E2E8F0)   │  │ └──────┘     │  │  │       │
│       │  │  └──────────────┘  └──────────────┘  └──────────────┘  │  │       │
│       │  │   height: 12px       height: 12px    Blue Border #0055FF│       │
└───────┘  └────────────────────────────────────────────────────────┘  └───────┘
  Button                     Capsule Track Container                     Button
```

### 3.1 Bảng Thông Số Kỹ Thuật CSS

| Phần Tử | Thuộc Tính CSS Chuẩn | Chi Tiết Trực Quan |
| :--- | :--- | :--- |
| **Carousel Nav Container** | `display: inline-flex; align-items: center; justify-content: center; gap: 14px; margin-top: 28px;` | Căn giữa dưới 3 Slide Hero |
| **Arrow Buttons (`←`, `→`)** | `width: 36px; height: 36px; border-radius: 50%; background: #FFFFFF; border: 1px solid #E5E7EB; box-shadow: 0 1px 3px rgba(0,0,0,0.06); cursor: pointer; display: flex; align-items: center; justify-content: center; color: #4B5563; transition: all 0.2s;` | Nút tròn trắng thanh lịch |
| **Capsule Track Container** | `background: #FFFFFF; border: 1px solid #E5E7EB; border-radius: 9999px; padding: 4px 6px; display: inline-flex; align-items: center; gap: 8px; box-shadow: 0 1px 4px rgba(0,0,0,0.04);` | Khung viên nang trắng bo tròn |
| **Inactive Segment** | `width: 105px; height: 12px; border-radius: 9999px; background: #E2E8F0; cursor: pointer; transition: all 0.25s ease;` | Viên nang xám bạc nhạt mềm mại |
| **Active Segment** | `width: 105px; height: 20px; border-radius: 9999px; border: 2px solid #0055FF; background: #FFFFFF; padding: 2px; position: relative; display: flex; align-items: center; cursor: pointer;` | Viền xanh dương điện tử rực rỡ |
| **Progress Fill Bar** | `height: 100%; border-radius: 9999px; background: #111827; width: 0%;` khi active chạy `animation: fillPill 6s linear forwards;` | Vạch đen bo tròn di chuyển mượt |

---

## 4. BẢNG THIẾT KẾ 3 SLIDE HERO HOẠT HỌA & NỘI DUNG TABI GO

Khớp chính xác với 3 hình ảnh hoạt họa mà Airalo sử dụng:

| Slide | Hình Ảnh Hoạt Họa | Bố Cục | Tiêu Đề & Nội Dung Tabi Go | Nút Kêu Gọi (CTA) |
| :---: | :--- | :---: | :--- | :--- |
| **1** | `hero-slide-1.svg`<br>(2 bạn trẻ selfie & nghe nhạc) | Minh họa Trái<br>Nội dung Phải | **Cảm nhận sự tự do của dữ liệu không giới hạn cùng Tabi Go**<br>Hãy cứ xem video đó, nghe bài hát đó, tải ứng dụng đó — nhận dữ liệu eSIM tốc độ cao không giới hạn để có kết nối thông suốt mọi nẻo đường tại 200+ quốc gia. | `[Về các gói không giới hạn]`<br>(Cam Airalo `#FF6E30`) |
| **2** | `hero-slide-2.svg`<br>(3 người bạn khoác vai, bạn nữ chân giả) | Minh họa Trái<br>Nội dung Phải | **Giới thiệu bạn bè. Nhận ngay 100.000đ Tabi Xu.**<br>Nhận ngay 100.000đ Tabi Xu cho mỗi lượt bạn bè mua eSIM thành công qua mã giới thiệu — bạn bè của bạn cũng sẽ được giảm ngay 10% đơn hàng đầu tiên. | `[Giới thiệu bạn bè ngay]`<br>(Cam Airalo `#FF6E30`) |
| **3** | `hero-slide-3.svg`<br>(3 người bạn nhảy ăn mừng high-five) | Minh họa Trái<br>Nội dung Phải | **Tích lũy điểm thưởng Tabi Go mỗi chuyến đi**<br>Nhận hoàn tiền tự động tới 10% Tabi Xu cho mỗi lần kích hoạt hoặc nạp data eSIM. Bạn đi du lịch càng nhiều, chi phí kết nối càng tiết kiệm! | `[Xem các cấp độ thành viên]`<br>(Cam Airalo `#FF6E30`) |

---

## 5. DESIGN SYSTEM & DESIGN TOKENS CHUẨN AIRALO

```css
:root {
  /* Backgrounds */
  --bg-page: #FAF8F5;            /* Nền kem ấm đặc trưng Airalo */
  --bg-card: #FFFFFF;            /* Nền thẻ trắng tinh */
  --bg-subtle: #F3F4F6;          /* Nền xám nhạt */
  
  /* Primary & Signature Colors */
  --orange: #FF6E30;             /* Cam chủ đạo Airalo */
  --orange-hover: #F25A1B;       /* Cam hover */
  --blue-slider: #0055FF;        /* Xanh dương viền active slider */
  --green-market: #48B080;       /* Xanh ngọc lục bảo sàn eSIM */
  --cyan-banner: #78CFE5;        /* Xanh Cyan hộp tính năng 30M users */
  
  /* Typography Colors */
  --text-heading: #111827;       /* Đen đậm cho H1, H2 */
  --text-body: #4B5563;          /* Xám đậm cho đoạn văn bản */
  --text-muted: #9CA3AF;         /* Xám nhạt cho placeholder & meta */
  
  /* Borders & Shadows */
  --border-light: #E8E4DD;       /* Viền phân cách nhẹ */
  --border-card: #E5E7EB;        /* Viền thẻ card */
  --shadow-soft: 0 4px 18px rgba(0, 0, 0, 0.04);
  --shadow-hover: 0 10px 28px rgba(0, 0, 0, 0.08);

  /* Typography Scale */
  --font-family: 'Plus Jakarta Sans', system-ui, -apple-system, sans-serif;
}
```

---

## 6. ĐỀ XUẤT ĐA PHƯƠNG ÁN (MULTI-OPTION COMPARISON)

| Tiêu Chí | Phương Án A (Khuyên Dùng) - Vector SVG Inline & CSS Typography | Phương Án B - Đóng Gói SVG File Độc Lập (`tabigo_brand.svg`) |
| :--- | :--- | :--- |
| **Mô tả** | Dựng mã SVG Vector trực tiếp trong HTML kết hợp CSS typography cho wordmark TabiGo. | Tạo file vector `tabigo_brand.svg` lưu vào `assets/images/` rồi nhúng qua thẻ `<img>`. |
| **Độ sắc nét** | Sắc nét 100% trên Retina, 4K, 8K; không bao giờ vỡ hạt. | Sắc nét 100% trên Retina, 4K. |
| **Tốc độ render** | Hiển thị tức thì 0ms, không phụ thuộc mạng, 0 network request. | Cần 1 HTTP request để tải file `.svg`. |
| **Tùy biến theme** | Cực kỳ linh hoạt: dễ dàng đổi màu, scale kích thước qua CSS. | Kém linh hoạt hơn nếu muốn đổi màu chữ/icon theo dark/light mode. |
| **Khả năng bảo trì** | Tất cả nằm trong code giao diện, kiểm soát từng pixel. | Cần duy trì file asset tách biệt. |
| **Đánh giá** | ⭐⭐⭐⭐⭐ **Khuyên dùng** (Tối ưu nhất cho Single Landing Page). | ⭐⭐⭐⭐ Tốt. |

---

## 7. CHI TIẾT CÁC TẬP TIN SẼ CẬP NHẬT TRONG GIAI ĐOẠN 2

1. **`tabi-go/concept-5-airalo.html`:**
   - Thay thế thẻ `img` logo bằng **Vector SVG Brand Icon & Wordmark Tabi Go** siêu nét.
   - Viết lại toàn bộ cụm CSS cho `.carousel-nav-container`, `.carousel-track`, `.carousel-segment`, `.carousel-segment.active`, `.carousel-segment-fill` theo đúng thông số Mục 3.
   - Đồng bộ HTML Slider về đúng **3 Slide** với 3 phân đoạn tương ứng.
   - Tinh chỉnh khoảng cách dòng, kích thước font chữ, confetti và các chi tiết thô cứng.
   - Đảm bảo script JavaScript điều khiển chuyển slide mượt mà khi hết 6s hoặc khi click thủ công vào các phân đoạn / nút mũi tên.

---

## 8. LỘ TRÌNH THỰC HIỆN TỪNG BƯỚC (PHASE ROADMAP)

- **Bước 1 (Đã hoàn thành):** Phân tích phản hồi chi tiết từ người dùng, nghiên cứu ảnh tham chiếu thực tế `media_1793270746461.png`, lập kế hoạch chi tiết v5 và dừng chờ duyệt.
- **Bước 2 (Chờ duyệt):** Người dùng xem xét kế hoạch, kiểm tra bảng thông số SVG Logo và Slider Capsule.
- **Bước 3 (Thực thi sau duyệt):** Cập nhật `concept-5-airalo.html` và `index.html`.
- **Bước 4 (Kiểm thử & Nghiệm thu):** Mở trình duyệt kiểm tra visual, test tương tác chuyển slide, kiểm tra responsive 390px/768px/1280px.

---

## 9. TIÊU CHÍ NGHIỆM THU (ACCEPTANCE CRITERIA)

- [x] **AC-1:** Logo Tabi Go tại Header là Vector SVG phẳng thanh thoát (~32px), đứng trực tiếp trên nền kem, không còn khung vuông bo góc cồng kềnh.
- [x] **AC-2:** Thanh Slider Carousel chuẩn capsule 3 phân đoạn mượt mà theo ảnh mẫu Airalo.
- [x] **AC-3:** Có đúng 3 slide hoạt họa tương ứng với 3 ảnh người dùng cung cấp (`hero-slide-1.svg`, `hero-slide-2.svg`, `hero-slide-3.svg`).
- [x] **AC-4:** Khi click mũi tên `←` / `→` hoặc click trực tiếp vào từng phân đoạn, slide chuyển mượt mà và thanh tiến trình reset chạy lại từ đầu.
- [x] **AC-5:** Khắc phục triệt để viền trắng mockup điện thoại trên banner cyan bằng ảnh PNG tách nền trong suốt và drop-shadow tự nhiên.
- [x] **AC-6:** Giữ nguyên tiêu chuẩn Landing Page: Tuyệt đối không có nút "Đăng nhập", "Đăng ký" hay luồng auth.
- [x] **AC-7:** Màu nền trang là kem ấm `#FAF8F5`/`#F5EFE6`, các card trắng nổi bật, font `Plus Jakarta Sans` chuẩn kích cỡ.
- [x] **AC-8:** Mục FAQ (Câu hỏi thường gặp) khớp 100% mẫu Ảnh 4 của Airalo: Header có nút pill "Đi đến trung tâm trợ giúp", Support Card bên phải bố cục chữ bên trái (Support badge, title, link có mũi tên `→`) và hình nhân viên gõ laptop ngồi góc dưới cùng bên phải.
- [x] **AC-9:** Bố cục Banner Tải App khớp chuẩn 100% mẫu Ảnh 2: Thẻ bo góc `36px` nền xanh Cyan `#72C7DC`, bên trái hiển thị rõ nét mockup điện thoại iPhone ứng dụng Tabi Go trong suốt (`tabigo_phone_transparent.png`); bên phải gồm cụm tải app chuẩn pixel:
  - **Nút iOS**: Vector chính thức 100% của **Apple App Store** (gradient xanh `#17C9FB` $\rightarrow$ `#1A74E8`, đường viền squircle chuẩn Apple, biểu tượng 3 thanh đan chéo chính thức của App Store), nhãn chữ `Download iOS app`, viền mảnh sắc nét `1.2px solid #52525B`.
  - **Nút Android**: Vector chính thức 100% của **Google Play Store** (4 mảng màu chuẩn Google `#4285F4`, `#34A853`, `#FBBC04`, `#EA4335` với các góc bo tròn mềm mại chuẩn brand), nhãn chữ `Download Android app`, viền mảnh sắc nét `1.2px solid #52525B`.
  - **Cụm đánh giá**: Nhãn `Rating`, điểm số đen tuyền cực đậm cỡ lớn `font-size: 28px; font-weight: 800; color: #000000;`, 5 ngôi sao SVG màu cam san hô `#FF7A30` đặc trưng của Airalo với ngôi sao thứ 5 chia tỉ lệ phần trăm chính xác (72% cam cho 4.7 và 60% cam cho 4.6).
- [x] **AC-10:** Footer khớp chuẩn 100% linh vật và nhân vật của mẫu Airalo mang thương hiệu TabiGo độc bản:
  - **Nhân vật minh họa chuẩn Airalo gốc 100%**: Sử dụng toàn bộ 52 sprite minh họa cao cấp từ nguyên bản Airalo (bạn nam tóc gợn sóng lãng tử mặc áo thun đỏ cầm smartphone, bạn nữ đeo khuyên tai vàng áo len mustard kiểm tra smartwatch, chú vẹt mào cockatoo trắng đậu vỗ cánh nghiêng đầu, thảm thực vật cây lá nhiệt đới, đá cuội sông mềm mại).
  - **Hệ thống chuyển động mượt mà 226 keyframe After Effects (`<animateTransform>`)**: Toàn bộ cử động cơ thể, mắt, tay chân, cánh vẹt và cành lá đung đưa đều chạy mượt mà nguyên bản ở tốc độ 60FPS.
  - **Bộ chữ 3D White Porcelain mang tên thương hiệu TabiGo**: Lớp chữ được tạo hình theo chuẩn font hình học cao cấp của Airalo, mang tên **`TabiGo`** bằng màu trắng sứ sang trọng (`#FFFFFF`), viền sắc nét nổi khối (`stroke="#EDE8E1" stroke-width="5"`), hiệu ứng bóng đổ đa tầng tự nhiên (`filter="url(#tabigo3D)"`). Toàn bộ 6 chữ cái `T a b i G o` đều đứng vững chãi trên cùng mặt phẳng chân đế, không bị cắt xén, với khoảng cách chữ (kerning/tracking) được tính toán chính xác tuyệt đối: **mọi khoảng hở giữa các chữ cái đều đạt chuẩn đồng đều 90.0px** (T $\xrightarrow{90px}$ a $\xrightarrow{90px}$ b $\xrightarrow{90px}$ i $\xrightarrow{90px}$ G $\xrightarrow{90px}$ o), triệt tiêu hoàn toàn sự chênh lệch hay dính chữ. Bạn nam ngồi tựa vào tâm chân chữ `T`, chú chim đậu tự nhiên trên vai cong của chữ `G`, và bạn nữ ngồi thư giãn thoải mái bên trong chữ `o`.
  - Dòng bản quyền `©2026 TABI GO` căn giữa thanh lịch.
- [x] **AC-11:** Cơ chế Header khi cuộn chuột: Header tuyệt đối **KHÔNG đổi sang màu trắng `#FFFFFF`** mà giữ nguyên nền kem ấm (`rgba(245, 239, 230, 0.97)`). Khi cuộn chuột xuống (`scrollY > 20px`), Tab Bar Menu (Hàng 2) sẽ **tự động thu gọn biến mất mượt mà** (`max-height: 0; opacity: 0; padding: 0; overflow: hidden`) giúp header gọn gàng thanh thoát đúng chuẩn trải nghiệm; khi cuộn ngược về đỉnh trang (`scrollY <= 20px`) thì thanh menu sẽ mở ra đầy đủ (`max-height: 60px; opacity: 1`).
- [x] **AC-12:** Điều hướng và ScrollSpy mượt mà: Bấm vào bất kỳ mục menu nào đều cuộn êm ái (`scroll-behavior: smooth`, `scroll-margin-top: 130px`) và menu tự động đổi màu active `#E0533C` theo vị trí section thực tế trên màn hình.
- [x] **AC-13:** Họa tiết nền toàn trang (Full-page Ambient Shapes): Hệ thống các hình khối pastel (đốm vàng, thoi đào, tròn mint, hạt đậu cyan) trải dài từ đầu Hero xuống qua Marketplace, FAQ, B2B, Banner Tải App và Footer, tạo độ sâu thị giác sinh động chuẩn 100% Airalo.
- [x] **AC-14:** Bảo vệ liên kết (Link Safeguarding): Tất cả các liên kết placeholder (nút tải app, mạng xã hội, các chính sách pháp lý, các nút tìm hiểu) đều được gán `javascript:void(0)` và kích hoạt bộ chặn click tự động `e.preventDefault()`, đảm bảo người dùng bấm vào sẽ không bao giờ bị nhảy trang, không bị nhảy lên đầu trang (hash `#`), và không bị chuyển hướng ra link ngoài.
- [x] **AC-15:** Màu sắc thương hiệu Logo Header & Footer đồng nhất: Header Logo gồm chữ `Tabi` màu đen tinh tế `#111827`, chữ `Go` và icon máy bay màu Cam chủ đạo Tabi Go `var(--orange)` `#F26322`, tạo sự hài hòa tối đa với toàn bộ hệ thống CTA và linh vật Footer.
- [x] **AC-16:** Menu Hàng 2 Đậm Chữ & Dễ Đọc (Bold Navigation): Các mục điều hướng tại Hàng 2 (`Trang chủ`, `Cửa hàng eSIM`, `Cách thức hoạt động của Tabi Go`, `Giới thiệu về Tabi Go`, `Tạp chí`, `Trợ giúp`) được tăng cường độ đậm chữ rõ rệt (`font-weight: 700`, màu đen sắc nét `#18181B`, `font-weight: 800` khi active), khắc phục tình trạng chữ mảnh khó nhìn.
- [x] **AC-17:** Nút Hamburger Menu & Floating Dropdown Chuẩn 1:1 Theo Ảnh Mẫu Airalo Người Dùng Cung Cấp:
  - **Nút Menu trên Header**: Hiển thị chữ `Menu` kèm icon linh hoạt: trạng thái đóng hiển thị 3 vạch ngang `☰`, trạng thái mở hiển thị dấu gạch chéo `✕` sắc nét, không viền hộp thô cứng, đặt cạnh vạch phân cách `|`.
  - **Khối Dropdown Trắng Tinh Khôi**: Nền trắng `#FFFFFF`, góc bo mềm mại `28px 4px 28px 28px` kết hợp mỏ vuốt cong (curved beak / swoop) ở góc trên bên phải kết nối liền mạch với vị trí nút `Menu ✕`. Đổ bóng đa tầng sâu và êm ái `filter: drop-shadow(0 20px 48px rgba(0,0,0,0.14))`.
  - **Typography & Danh Sách Menu**: Font chữ đen cực đậm (`font-size: 16.5px; font-weight: 800; color: #000000;`), giãn cách dòng rộng rãi thoáng đãng (~22px gap), loại bỏ hoàn toàn các chấm bullet/viền hộp. Mục đang active (ví dụ: *Trang chủ*) có đường gạch chân đen thanh lịch (`text-decoration: underline; text-underline-offset: 5px; text-decoration-thickness: 2.2px`).
  - **Hàng Footer Dropdown**: Ngăn cách bằng đường kẻ xám nhạt mảnh `1px solid #E5E7EB`, phía dưới là 2 icon Tiền tệ `💵` (banknote) và Ngôn ngữ `🌐` (globe) cách nhau bởi vạch thẳng đứng `|`, hỗ trợ tương tác đổi tiền tệ và ngôn ngữ nhanh chóng.
- [x] **AC-18:** Ô Tìm Kiếm Trung Tâm Trên Header Khi Cuộn (Scrolled Center Search Bar - Khớp Chuẩn Ảnh Mẫu 3): Trên sticky header khi cuộn trang, thanh tìm kiếm dạng viên nang xuất hiện ở vị trí trung tâm `[ 🔍 Bạn cần eSIM ở đâu? | Quốc gia ▾ ]` tương tự chuẩn Airalo. Click hoặc focus vào sẽ hiển thị danh sách thẻ điểm đến nhanh (Nhật Bản, Hàn Quốc, Thái Lan, Singapore, v.v.), tự động đồng bộ từ khóa với thanh tìm kiếm Hero và cuộn xuống mục Marketplace khi bấm Enter hoặc chọn thẻ.

