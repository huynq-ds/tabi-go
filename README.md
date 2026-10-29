# Tabi Go Multi-Concept Landing Pages (APP3M-847)

Dự án xây dựng 5 giao diện Landing Page độc bản hoàn toàn khác biệt cho Ứng dụng **Tabi Go eSIM** (Hệ sinh thái Công nghệ 3M), lấy cảm hứng từ 5 nền tảng eSIM hàng đầu thế giới: **Trifa, Firsty, Saily, BetterRoaming, và Airalo**.

---

## 📂 Danh Sách Các File Trong Dự Án

| File | Concept | Phong Cách | Tham Chiếu | Điểm Nhấn Tương Tác |
| :--- | :--- | :--- | :--- | :--- |
| [`index.html`](./index.html) | **Portal Hub** | Master Showcase Switcher & A/B Matrix | Tổng hợp 5 Concept | So sánh ma trận 5 phong cách |
| [`concept-1-trifa.html`](./concept-1-trifa.html) | **Concept 1: Trifa Vibe** | Japan Friendly & Travel Onboarding | [trifa.co](https://trifa.co) | Dropdown check máy, Postcard Destinations Grid, Voucher TABIGO10 |
| [`concept-2-firsty.html`](./concept-2-firsty.html) | **Concept 2: Firsty Vibe** | 3D Cyber Glow & Floating Bento Grid | [firsty.app](https://firsty.app) | Quả địa cầu CSS, HUD Radar User-Agent Scanner, Live Bento Specs |
| [`concept-3-saily.html`](./concept-3-saily.html) | **Concept 3: Saily Vibe** | High-Trust Security & Instant Search Hero | [saily.com](https://saily.com) | Ô Search Hero tức thì + Popup giá, Marquee nhà mạng, Bảng 3 cột |
| [`concept-4-betterroaming.html`](./concept-4-betterroaming.html) | **Concept 4: BetterRoaming** | Apple Minimalist & Savings Calculator | [betterroaming.com](https://betterroaming.com) | Bộ tính tiết kiệm Roaming animated counter, Editorial Tabs 01/02/03 |
| [`concept-5-airalo.html`](./concept-5-airalo.html) | **Concept 5: Airalo Vibe** | E-Commerce Destination Marketplace | [airalo.com](https://airalo.com) | Thanh tìm kiếm điểm đến, Sàn 3 Tab (Quốc gia / Khu vực / Toàn cầu) |

---

## 🚀 Hướng Dẫn Chạy & Xem Trực Tiếp

### Cách 1: Mở Trực Tiếp Trên Trình Duyệt (Không cần cài đặt)
Chỉ cần nhấp đúp hoặc chạy lệnh sau từ terminal:
```bash
open tabigo-multi-landing/index.html
```

### Cách 2: Chạy Bằng Local Server
```bash
cd tabigo-multi-landing
npx serve -l 3334 .
# hoặc nếu dùng vite:
npm run dev
```
Sau đó truy cập: `http://localhost:3334/`

---

## 🎯 Kiểm Tra Tiêu Chí Nghiệm Thu (Quality Checklist)

- [x] **AC-1:** Mở từng file HTML trực tiếp hoặc qua local server chạy ngay lập tức.
- [x] **AC-2:** 5 concept hiển thị hoàn toàn khác nhau về màu nền, hero visual, cấu trúc section.
- [x] **AC-3:** Responsive đầy đủ trên Mobile (390px), Tablet (768px), Desktop (1440px).
- [x] **AC-4:** Menu Mobile trượt mở/đóng mượt, click link tự đóng drawer và cuộn tới section.
- [x] **AC-5:** FAQ Accordion mở/đóng mượt, icon mũi tên xoay 180° không giật layout.
- [x] **AC-6:** Nút sao chép mã `TABIGO10` copy clipboard và hiện toast thông báo.
- [x] **AC-7 (Concept 2):** HUD Scanner tự nhận diện User-Agent và xuất kết quả thiết bị thật.
- [x] **AC-8 (Concept 3):** Gõ tên nước vào ô Search Hero hiện ngay popup giá gói cước mock.
- [x] **AC-9 (Concept 4):** Bộ tính tiết kiệm Roaming animate số tiền nhảy mượt trong 600ms.
- [x] **AC-10 (Concept 5):** 3 Tab phân vùng (Quốc gia / Khu vực / Toàn cầu) chuyển đổi mượt mà.
- [x] **AC-11:** DevTools Console sạch sẽ, zero syntax error.
- [x] **AC-12:** Hỗ trợ `@media (prefers-reduced-motion: reduce)` tôn trọng người dùng.
- [x] **AC-13:** `index.html` Portal Hub hiển thị đầy đủ 5 card và bảng so sánh A/B.
