---
name: website-3d-design
description: Chuyên gia thiết kế, tối ưu hóa và phát triển website 3D tương tác sử dụng Three.js và Glassmorphism UI. Hướng dẫn phân tích UI/UX, nâng cấp cảnh quan 3D, tối ưu hóa hiệu suất 60 FPS và kiểm thử trình duyệt.
---

# Skill: website-3d-design

Skill này cung cấp quy trình chuẩn hóa và kiến thức chuyên sâu để phát triển, nâng cấp và kiểm thử các website 3D tương tác (Interactive 3D WebGL Diorama) với trọng tâm là thẩm mỹ Indie Game cao cấp, ánh sáng điện ảnh, giao diện Glassmorphism và hiệu suất 60 FPS mượt mà.

---

## 1. PHÂN TÍCH UI/UX (UI/UX Analysis & Heuristics)

Khi nhận yêu cầu đánh giá hoặc nâng cấp giao diện của website 3D:

### 1.1. Nguyên tắc "3D As The Hero" (Tôn vinh không gian 3D)
* Không gian 3D là nhân vật chính. Giao diện (HUD) chỉ đóng vai trò thứ cấp hỗ trợ người dùng khám phá.
* **Quy tắc vùng an toàn (Safe Zone Padding):** Chiều cao của thanh điều khiển bên dưới (Bottom Dock) không được vượt quá **15% chiều cao màn hình** để tránh che khuất móng đảo hoặc các mô hình phía trước.
* **Trọng tâm bố cục (Golden Ratio Viewport):** Điểm nhìn `targetLook` của máy quay 3D cần được đặt lệch nhẹ lên phía trên tâm hình học để cân bằng khoảng trống bị thanh Dock chiếm dụng ở đáy màn hình.

### 1.2. Phân luồng điều khiển (Segmented Navigation)
* Không hiển thị dàn trải quá 12 nút bấm cùng một lúc trên màn hình.
* Gom nhóm các chức năng thành các tab phân luồng logic:
  * **Tab Phương tiện (Vehicles):** Đi bộ, Xe đạp, Ván trượt, Siêu xe, Tự lái quanh đường, Chuông còi.
  * **Tab Góc nhìn (Camera Views):** Toàn cảnh diorama, Cận cảnh nhân vật, Đường phố, Cổng sao, Tiệm Cafe, Quầy chợ.
  * **Tab Biểu cảm (Actions & Clips):** Các cử chỉ diễn hoạt của nhân vật (chào, nhảy múa, gõ code, ngủ...).
* Cố định các nút cốt lõi (Core Actions) như `🎬 Phim ngắn`, `🛑 Dừng lái`, `🔄 Tự xoay`, `🎵 Nhạc` trên thanh điều hướng chính.

### 1.3. Hệ thống Design Tokens (Glassmorphism & Colors)
* **Background Glass:** `rgba(13, 9, 32, 0.76)` kết hợp `backdrop-filter: blur(16px)`.
* **Border:** `1px solid rgba(139, 92, 246, 0.32)` với viền hover phát quang `rgba(192, 132, 252, 0.6)`.
* **Màu sắc chủ đạo:**
  * Primary Accent: Tím neon `#8b5cf6` và hồng pastel `#ff7ebb`.
  * Secondary Accent: Xanh ngọc lam `#38bdf8` và vàng hổ phách `#fbbf24`.
* **Typography:** Ưu tiên font hệ thống hiện đại `-apple-system, "Segoe UI", Roboto`, áp dụng `-webkit-font-smoothing: antialiased` và `letter-spacing: 0.15px`.
* **Phím tắt điều khiển (Keyboard Badges):** Hiển thị dạng thẻ `<kbd>` nổi sang trọng, cho phép người dùng thu gọn/mở rộng tự do.

---

## 2. CẢI TIẾN & PHÁT TRIỂN MÔ HÌNH 3D (3D World & Environment)

### 2.1. Thiết lập Bầu trời & Ánh sáng Điện ảnh (Cinematic Lighting Hierarchy)
1. **Vòm trời đa tầng (Celestial Sky Dome):**
   * Sử dụng hình cầu nghịch đảo `SphereGeometry(220, 24, 16)` với vật liệu `MeshBasicMaterial({ side: THREE.BackSide, depthWrite: false })`.
   * Gán chất liệu gradient canvas chuyển sắc từ tím vũ trụ huyền bí (`#080415`) qua tím twilight (`#1a0e38`) đến xanh đêm chân trời (`#142042`).
2. **Hệ thống 3 nguồn sáng chủ đạo:**
   * **Key Light (Ánh trăng):** `THREE.DirectionalLight` sắc tím lavender (`0xa5b4fc`), cường độ ~`1.05`, đổ bóng mềm qua `THREE.PCFShadowMap`.
   * **Ambient / Fill Light:** `THREE.HemisphereLight` với sắc trời tím mộng mơ (`0x8b7cff`) và phản xạ đất tím ấm (`0x241444`) để vùng tối vẫn có độ sâu màu sắc phong phú.
   * **Rim Light (Ánh sáng viền đối nghịch):** `THREE.DirectionalLight` ngọc lam (`0x2dd4bf`) từ góc chéo sau tạo viền sáng bắt mắt trên mái nhà, tán cây và nhân vật.
3. **Ánh sáng ấm áp nội thất & đường phố:**
   * Cửa sổ nhà, đèn lồng và đèn đường phát sáng vàng hổ phách ấm cúng (`0xffd166`, `0xffb84d`).
   * Tự động đồng bộ: Ban ngày tắt đèn, ban đêm bật đèn rực rỡ.

### 2.2. Kiểm soát Hào quang & Tránh cháy sáng (No Overexposure)
* Không dùng sprite phát sáng kích thước quá lớn (> 10) với chế độ AdditiveBlending trên các vật thể sáng.
* Tại cổng không gian (Stargate), sử dụng lốc xoáy năng lượng 2 lớp xoay ngược chiều nhau với độ mờ `opacity: 0.55 - 0.65`, hào quang halo nhỏ hơn `5.0`.

### 2.3. Bố cục & Lối đi kết nối (Interconnected Flow)
* Kết nối các công trình rời rạc bằng các tuyến đường dạo đá cuội tự nhiên (`Cobblestone Walkways`).
* Bổ sung các chi tiết trang trí sinh thái: Cụm nấm coctail phát quang, hoa sen bập bềnh, lá súng, thuyền gỗ nhỏ và bờ đá phủ rêu xanh.

---

## 3. TỐI ƯU HÓA HIỆU SUẤT 60 FPS (Performance Engineering)

Để website hoạt động mượt mà trên cả laptop văn phòng và điện thoại:
1. **Bộ nhớ đệm hình học & vật liệu (Caching System):**
   * Tái sử dụng `BoxGeometry`, `CylinderGeometry`, `SphereGeometry` qua bảng băm `_geoCache`.
   * Tái sử dụng `MeshStandardMaterial` và `MeshBasicMaterial` qua bảng băm `_matCache` và `_glwCache`.
2. **Đổ bóng có chọn lọc (Selective Shadow Casting):**
   * Chỉ bật `castShadow = true` cho các công trình lớn (Biệt thự, Tháp, Thân xe). Không bật đổ bóng cho hàng rào, cánh hoa hoặc đá nhỏ.
3. **Tối ưu hóa hạt phân tử (GPU-Friendly Particles):**
   * Tạo hạt bằng `BufferGeometry` và `Points`, di chuyển và xoay toàn bộ cụm `Points` trên GPU trong vòng lặp RAF thay vì cập nhật lại buffer `position` mỗi frame.
4. **Điều chỉnh độ phân giải thích ứng (Dynamic DPR Scaling):**
   * Theo dõi thời gian render frame `dt`. Nếu `dt > 28ms` (dưới 35 FPS), tự động hạ tỉ lệ `devicePixelRatio` từ `1.5` xuống `1.0` để duy trì tốc độ khung hình.

---

## 4. QUY TRÌNH KIỂM THỬ TRÌNH DUYỆT (Testing & Verification Procedure)

Mọi thay đổi phải tuân thủ nghiêm ngặt 3 bước xác thực:

### Bước 1: Kiểm tra cú pháp JavaScript
Trích xuất mã `<script>` từ file HTML và chạy kiểm tra cú pháp độc lập:
```powershell
node --check "<scratch_path>/script_check.js"
```

### Bước 2: Kiểm tra liên kết DOM ID & Logic
Xác nhận toàn bộ các ID điều khiển không bị mất hoặc đổi tên sai lệch:
```javascript
const ids = ['c', 'play', 'tl', 'who', 'rides', 'clips', 'cams', 'pm', 'sw', 'rot', 'btn-photo', 'btn-dn', 'modal'];
// Đảm bảo tất cả ID đều tồn tại trong mã HTML
```

### Bước 3: Mở trực quan trên trình duyệt (Browser Visual Inspection)
Mở trực tiếp file HTML trên trình duyệt Google Chrome hoặc Microsoft Edge:
```powershell
Start-Process "C:\Users\Trung Tin\.gemini\antigravity\scratch\website\index.html"
```
Kiểm tra các tiêu chí:
* Bố cục cân đối ở các kích thước cửa sổ.
* Di chuyển nhân vật, đạp xe, ván trượt, siêu xe êm ái.
* Âm thanh chuông/còi và nhạc nền phát đúng nhịp.
* Chuyển đổi thời tiết sáng/tối không gây giật lag.
* Chụp ảnh màn hình Full HD lưu file thành công.
