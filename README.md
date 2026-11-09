# 🐾 TT Trung Tín – Làng 3D & Mèo Animation

<p align="center">
  <b>Thế giới 3D tương tác mô phỏng Làng Mèo huyền ảo chạy trực tiếp trên trình duyệt web</b><br>
  <i>Xây dựng bằng Three.js (WebGL) • Chạy trực tiếp không cần cài đặt</i>
</p>

<p align="center">
  <a href="https://tinn2673-create.github.io/lang-meo-3d/" target="_blank">
    <img src="https://img.shields.io/badge/🌐_Trải_nghiệm_ngay-Xem_Mô_Hình_3D-ff5fa8?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Live Demo">
  </a>
</p>

---

## 🌟 Trải nghiệm trực tiếp (Live Demo)

> 💡 **Xem mô hình 3D chạy trực tuyến tại:**  
> 👉 **[https://tinn2673-create.github.io/lang-meo-3d/](https://tinn2673-create.github.io/lang-meo-3d/)**  
> *(Hỗ trợ mượt mà trên cả máy tính, laptop, máy tính bảng và điện thoại di động).*

---

## 📖 Giới thiệu dự án

**TT Trung Tín – Làng 3D & Mèo Animation** là một tác phẩm đồ họa 3D tương tác nghệ thuật. Toàn bộ bối cảnh là một hòn đảo lơ lửng giữa trời đêm tĩnh lặng mang hơi hướng phong cách low-poly & cyberpunk lung linh:

- **Hai nhân vật chính:** Mèo Đen 🐈‍⬛ và Mèo Trắng 🐱 với hệ thống animation độc lập (đi bộ, chạy nước rút, nhảy cao, vẫy tay, làm trò vui nhộn).
- **Ngôi làng sống động:** Có nhà phố, tháp quan sát, cối xay gió tự quay, đài radar phát tín hiệu hologram lập trình `</>`, gara ô tô, hồ nước với thác chảy và đàn cá nhảy.
- **Hệ thống giao thông:** Các phương tiện (ô tô, xe máy điện, xe đạp) tự động lưu thông tuần hoàn trên tuyến đường quanh đảo.
- **Âm thanh & Nhạc nền:** Trình tổng hợp âm thanh Web Audio API tạo nhạc nền 8-bit thư giãn cùng hiệu ứng tiếng mèo kêu sinh động.

---

## ✨ Các tính năng chính

| Tính năng | Mô tả chi tiết |
| :--- | :--- |
| 🎮 **Chế độ Chơi Mèo (Gameplay)** | Cho phép bạn tự tay điều khiển chú mèo khám phá toàn bộ ngôi làng, vượt chướng ngại vật. Hỗ trợ bàn phím PC và Joystick cảm ứng ảo trên điện thoại. |
| 🎬 **Chế độ Phim ngắn (Cinema)** | Kịch bản điện ảnh tự động điều khiển góc quay camera chuyển cảnh mượt mà, ghi lại câu chuyện vui nhộn giữa hai chú mèo. |
| 🐾 **Thư viện Animation** | Kích hoạt các điệu bộ: Đứng chào, Nhảy múa (Dance), Tập thể dục, Lăn lộn, Nằm ngủ... cho từng chú mèo hoặc cả hai cùng lúc. |
| 🔄 **Đa góc máy quan sát** | Chuyển đổi nhanh 4 góc nhìn chuẩn: *Toàn cảnh đảo*, *Cận cảnh mèo*, *Đường phố*, *Cổng & hồ nước*, hoặc bật chế độ tự động xoay 360°. |
| ℹ️ **Bảng giới thiệu tích hợp** | Popup hướng dẫn chi tiết ngay trên giao diện web giúp người xem lần đầu hiểu ngay câu chuyện và cách tương tác. |

---

## 🕹️ Hướng dẫn điều khiển (Controls)

### 🖥️ Trên Máy tính / Laptop:
* **W / A / S / D** hoặc **Phím Mũi tên**: Di chuyển mèo đi tới, lui, rẽ trái, rẽ phải (tốc độ linh hoạt, có trượt tường êm).
* **Giữ Shift**: Chạy nước rút (Sprint cực nhanh).
* **Phím Space (Phím cách)**: Nhảy cao (vọt lên dứt khoát kèm tiếng meo 😸).
* **Phím Q / E**: Xoay góc nhìn camera sang trái / phải tiện lợi không cần dùng chuột.
* **Phím M**: Kêu meo meo và hiện bong bóng cảm xúc `🐾 Meow!`.
* **Phím Tab**: Chuyển đổi điều khiển giữa **Mèo Đen** và **Mèo Trắng** (mèo còn lại sẽ tự động đi theo bạn).
* **Kéo chuột trái**: Xoay góc nhìn tự do 360°.
* **Cuộn chuột (Scroll)**: Phóng to / Thu nhỏ (Zoom in / Zoom out).

### 📱 Trên Điện thoại / Máy tính bảng (Touch):
* **Cần gạt Joystick (bên trái)**: Kéo để di chuyển, kéo mạnh hơn 75% để chạy nhanh.
* **Nút bấm ⤒ (bên phải)**: Nhấn để nhảy.
* **Nút 🔁 Đổi mèo**: Đổi chú mèo đang điều khiển (chú mèo kia sẽ chạy theo sau).
* **Chạm và vuốt màn hình**: Xoay góc nhìn camera.
* **Chụm 2 ngón tay**: Thu phóng góc nhìn.

---

## 🛠️ Công nghệ sử dụng

* **Three.js (r128)**: Thư viện WebGL dựng hình khối, ánh sáng, đổ bóng mềm (PCFSoftShadowMap) và hoạt họa 3D.
* **Web Audio API**: Bộ tổng hợp âm thanh tạo giai điệu âm nhạc và tiếng kêu sound effect không cần dùng file mp3 ngoài.
* **Pure HTML5 / CSS3 / Vanilla JavaScript**: Dự án được đóng gói tối ưu, tải cực nhanh, không cần cài đặt Node.js hay bundle phức tạp.

---

## 🚀 Hướng dẫn chạy thử trên máy (Local)

1. Tải repository về máy tính:
   ```bash
   git clone https://github.com/tinn2673-create/lang-meo-3d.git
   ```
2. Mở file `index.html` bằng bất kỳ trình duyệt nào (Chrome, Edge, Firefox, Safari) để trải nghiệm ngay.

---

## 🌐 Hướng dẫn xuất bản lên GitHub Pages

Để mô hình 3D chạy online thành trang web sống:
1. Vào trang GitHub repository của bạn: `https://github.com/tinn2673-create/lang-meo-3d`
2. Chọn tab **Settings** (Cài đặt) ở thanh menu trên cùng.
3. Ở menu bên trái, chọn **Pages**.
4. Tại mục **Branch**:
   * Chọn nhánh: `main`
   * Chọn thư mục: `/(root)`
   * Bấm nút **Save**.
5. Sau 1 - 2 phút, GitHub sẽ tạo đường link trang web tại:  
   👉 **`https://tinn2673-create.github.io/lang-meo-3d/`**

---

## 👤 Tác giả

* **TT · Trung Tín**
* GitHub: [@tinn2673-create](https://github.com/tinn2673-create)
* Slogan: *“Dream Big, Code Better 🐾”*
