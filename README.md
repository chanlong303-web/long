# Chiến Trường

Cờ chiến thuật 2 người chơi **chung một máy** (ngồi đối diện nhau), hỗ trợ chơi **offline** trên điện thoại sau khi cài thành app (PWA).

## Luật chơi (bản hiện tại)

- Bàn cờ 11×13, có sông ngang giữa, cầu, và nhiều núi.
- Mỗi bên có: **1 Tướng**, **2 Kỵ binh**, **2 Cung thủ**, **2 Khiên**, **3 Bộ binh**.
- **Không còn Sứ giả**. Không còn ô rừng (toàn bộ đã thành núi).
- Mỗi lượt người chơi được thực hiện **tối đa 4 thao tác**.
- Mỗi quân chỉ được hành động **tối đa 2 lần** trong một lượt.
- Mục tiêu: hạ Tướng đối phương. Cả hai Tướng cùng ngã → hòa.

### Khả năng quân

| Quân       | Di chuyển / tấn |
|------------|-------------------|
| Tướng     | 1 ô 8 hướng (ăn được), hoặc 2 ô nếu ô giữa trống (chỉ đi). Tầm chỉ huy 3 ô. |
| Bộ binh   | 1 ô 8 hướng. Có thể Đào hào / Xây cầu / Phá cầu ở ô kề (4 hướng). |
| Kỵ binh   | Chạy thẳng 1–3 ô, ăn ở ô cuối. |
| Cung thủ  | Đi/ăn 1 ô 4 hướng. Bắn đúng 2 ô (8 hướng), xuyên núi, không bị phản. Hạ mọi quân trừ Khiên. |
| Khiên     | 1 ô 8 hướng. Miễn nhiễm đạn cung. |

## Cách chơi trên điện thoại (không cần WiFi)

1. Up toàn bộ file lên GitHub (hoặc bất kỳ hosting tĩnh nào hỗ trợ HTTPS).
2. Mở link bằng trình duyệt trên điện thoại **lần đầu có mạng**.
3. Thêm vào Màn hình chính:
   - **iOS Safari**: nút Chia sẻ → “Thêm vào Màn hình chính”.
   - **Android Chrome**: menu ⋮ → “Cài đặt ứng dụng” / “Thêm vào Màn hình chính”.
4. Sau đó mở icon đã thêm → chơi offline hoàn toàn.

## Cấu trúc file

```
index.html              # game chính
manifest.webmanifest    # PWA manifest
sw.js                   # Service Worker (cache offline)
icon-192.png
icon-512.png
apple-touch-icon.png
README.md
```

## Chạy local nhanh

Chỉ cần mở `index.html` bằng trình duyệt (một số tính năng PWA cần HTTP/HTTPS, không dùng `file://`).

Hoặc dùng bất kỳ static server nào:

```bash
npx serve .
# hoặc
python3 -m http.server 8080
```

## Ghi chú kỹ thuật

- Toàn bộ logic + UI nằm trong một file HTML (dễ bảo trì và offline).
- Service Worker cache các file cần thiết để chơi không mạng.
- Board luôn nhìn từ phía Xanh; icon quân tự xoay 180° khi đến lượt Đỏ để người ngồi đối diện nhìn đúng chiều.
