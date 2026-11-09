# AGENTS.md — Quy tắc Phát triển Website 3D TT Trung Tín

Tài liệu này xác định các tiêu chuẩn kỹ thuật, phong cách thiết kế và quy tắc làm việc bắt buộc cho **AI Assistant** và **Developer** khi tham gia phát triển, bảo trì và nâng cấp dự án **Website 3D Làng Mèo TT Trung Tín**.

---

## 1. TỔNG QUAN DỰ ÁN & CÔNG NGHỆ

* **Tên dự án:** TT Trung Tín – Làng 3D & Mèo Chibi Animation
* **Mục tiêu:** Không gian 3D tương tác phong cách indie game nghệ thuật, nhẹ nhàng, chạy trực tiếp trên web không cần cài đặt.
* **Ngôn ngữ & Thư viện:**
  * **HTML5 & CSS3:** Giao diện Glassmorphism (kính mờ), CSS Custom Properties, Responsive Layout.
  * **Vanilla JavaScript (ES6+):** Xử lý logic, physics, âm thanh và điều khiển.
  * **Three.js (r128):** Động cơ đồ họa WebGL 3D (nạp qua CDN Cloudflare).
  * **Web Audio API:** Bộ tổng hợp âm thanh dạng sóng native (chiptune, chuông xe, còi xe, tiếng meow).
  * **HTML5 Canvas 2D:** Tạo dynamic textures (biển hiệu neon, bảng phấn, biểu cảm màn hình robot).
* **Kiến trúc mã nguồn:** Standalone Single-File (`index.html`) chạy trực tiếp trên mọi trình duyệt web (desktop, laptop, tablet, mobile).

---

## 2. NGUYÊN TẮC BẮT BUỘC KHI LÀM VIỆC (CORE RULES)

### 2.1. Bảo toàn 100% chức năng hiện có (Preserve Existing Features)
* **Tuyệt đối không làm hỏng:**
  1. Hệ thống 4 phương tiện: Đi bộ (`walk`), Xe đạp xoay bàn đạp (`bike`), Ván trượt điện bay (`board`), Siêu xe mui trần (`car`).
  2. Hệ thống âm thanh: Rung chuông xe `Kính coong 🔔`, còi siêu xe `Bíp bíp 📢`, tiếng kêu mèo `🐾 Meow!`, nhạc nền chiptune.
  3. Chế độ tự lái quanh đường (`🏁 Chạy quanh đường` - phím `R`).
  4. Chế độ phim ngắn điện ảnh (`🎬 Phim ngắn` với kịch bản chuyển camera và phụ đề).
  5. Chuyển đổi 3 chế độ thời tiết & ánh sáng (`☀️ Ban Ngày`, `🌅 Hoàng Hôn`, `🌙 Đêm Neon`).
  6. Tính năng chụp ảnh màn hình Full HD (`📸 Chụp ảnh`).
  7. Cổng không gian Stargate dịch chuyển tức thời sang bên kia hòn đảo.
  8. Hệ thống điều khiển đầy đủ trên cả máy tính (WASD, 1-4, Shift, Space, Q/E, Tab, M/C) và điện thoại (Joystick ảo + các nút cảm ứng).

### 2.2. Không thay đổi cấu trúc dự án tùy tiện (Preserve Project Structure)
* Không chuyển đổi sang React, Vue, Vite, Next.js hay cài đặt các build tool phức tạp trừ khi có yêu cầu phê duyệt rõ ràng từ người dùng.
* Giữ nguyên cấu trúc file:
  * `index.html`: Chứa toàn bộ HTML, CSS và JS của trang web.
  * `README.md`: Hướng dẫn sử dụng và cập nhật tài liệu.
  * `lang_meo_3d_hoanthien.zip`: Gói sao lưu dự án.

### 2.3. Không tự ý thay thế mô hình 3D (Preserve 3D Asset Kit)
* Mọi công trình và đồ vật đều được thiết kế dựa trên bản vẽ concept 3D nguyên gốc:
  * Biệt thự TT Trung Tín 2 tầng có ống khói và biển hiệu vương miện.
  * Tiệm bánh & cà phê mèo chibi có mái hiên sọc và xe tay ga retro.
  * Quầy chợ nông sản & cá tươi cho mèo.
  * Hồ cá Koi thu nhỏ xinh xắn với thác nước, lá sen hồng và đôi cá chép Koi nhảy múa.
  * Cối xay gió quay cánh, guồng nước và tháp quan sát thiên văn.
  * Robot mèo AI mini bay lượn hộ tống và Drone chở hàng trên nóc gara.
  * Cặp nhân vật Mèo Đen và Mèo Trắng Chibi với trang phục, tai nghe gaming và rigging khớp xương.
* Mọi sự bổ sung chỉ mang tính trang trí làm giàu cảnh quan, không xóa hoặc làm biến dạng các mô hình chính.

### 2.4. Không thêm Dependency không cần thiết (Zero Bloat)
* Không nạp thêm các thư viện cồng kềnh từ CDN hoặc npm. Mọi logic hiệu ứng, ánh sáng và âm thanh ưu tiên triển khai bằng Three.js và Web API nguyên bản.

### 2.5. Giữ phong cách thiết kế nhất quán (Design Consistency)
* **Định hướng mỹ thuật:**
  * **Cozy 3D Indie Game World**: Ấm cúng, mộng mơ, phong cách Low Poly hiện đại, tinh gọn.
  * **Cinematic Night Environment**: Ánh sáng ánh trăng tím lavender (`#a5b4fc`), phản xạ môi trường tím mộng mơ (`#8b7cff`), viền sáng xanh ngọc lam (`#2dd4bf`), tương phản cùng ánh đèn vàng ấm áp (`#ffd166`, `#ffb84d`) từ các ô cửa sổ và đèn đường.
  * **Giao diện Glassmorphism cao cấp:** Nền kính mờ (`backdrop-filter: blur(16px)`), viền tím neon mảnh mai, nút bấm bo tròn dạng pill thanh thoát.
  * **Tập trung vào 3D:** Giao diện người dùng phải gọn gàng, không bao giờ che khuất các chi tiết quan trọng của thế giới 3D.

### 2.6. Kiểm tra nghiêm ngặt trước khi bàn giao (Strict Verification)
Trước khi thông báo hoàn thành bất kỳ nhiệm vụ nào:
1. **Kiểm tra cú pháp JS:** Chạy `node --check` để xác nhận 100% không có lỗi cú pháp.
2. **Kiểm tra liên kết DOM ID:** Đảm bảo tất cả 34 ID phần tử HTML liên kết chặt chẽ với logic JavaScript.
3. **Kiểm tra hiệu suất:** Duy trì 60 FPS mượt mà thông qua bộ đệm `_geoCache` và `_matCache`.
4. **Kiểm tra giao diện:** Khởi chạy trang web bằng lệnh `Start-Process` để kiểm tra trực quan trên trình duyệt (Google Chrome / Microsoft Edge).

---

## 3. CHECKLIST KIỂM THỬ KHI CẬP NHẬT (TEST MATRIX)

| STT | Hạng mục kiểm tra | Tiêu chí đạt |
| :---: | :--- | :--- |
| 1 | Khởi động ban đầu | Mở file `index.html` trong trình duyệt, tải ngay cảnh đêm tím ấm cúng, 0 lỗi console đỏ. |
| 2 | Điều khiển di chuyển | Bấm W/A/S/D di chuyển êm, giữ Shift tăng tốc, Space nhảy cao, va chạm trượt tường mượt mà. |
| 3 | Đổi phương tiện | Phím 1: Đi bộ, 2: Đạp xe (bàn đạp và bánh quay), 3: Ván trượt (neon lướt), 4: Siêu xe. |
| 4 | Chuông và còi xe | Phím B hoặc nút chuông: Phát âm thanh chuông xe / còi siêu xe không bị rè hay đơ tiếng. |
| 5 | Tự lái Cruise Mode | Phím R hoặc nút `🏁 Chạy quanh đường`: 2 chú mèo tự động bám làn đường đua, xe nghiêng khi vào cua. |
| 6 | Phim ngắn điện ảnh | Bấm `🎬 Phim ngắn`: Camera tự động lướt qua các góc cảnh, hiển thị phụ đề và thanh tiến trình. |
| 7 | Cổng Stargate | Bước vào cổng: Nhân vật dịch chuyển tức thời sang bên kia đảo; hiệu ứng xoay mềm mại không chói mắt. |
| 8 | Chuyển thời tiết | Bấm `🌙 Đêm Neon` -> `☀️ Ban Ngày` -> `🌅 Hoàng Hôn`: Bầu trời và đèn cửa sổ đổi trạng thái chuẩn xác. |
| 9 | Chụp ảnh lưu niệm | Bấm `📸 Chụp ảnh`: Hiệu ứng chớp sáng camera và tải file ảnh PNG sắc nét về máy. |
| 10 | Bố cục & Responsive | Thay đổi kích thước cửa sổ trình duyệt: Toàn bộ hòn đảo bay luôn nằm trọn vẹn, không bị mất góc. |
