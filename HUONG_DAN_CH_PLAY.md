# Hướng dẫn đưa BizArena lên CH Play (Google Play Store)

Tài liệu này dành cho tác giả BizArena. Mọi thứ kỹ thuật đã được chuẩn bị sẵn trong repo — bạn chỉ cần làm theo đúng thứ tự.

## Những gì đã có sẵn trong repo

| File | Công dụng |
|---|---|
| `index.html` | Ứng dụng BizArena v2.1 (tự chứa, đã nhúng font) |
| `manifest.json` | Khai báo PWA (tên, icon, màu) — điều kiện bắt buộc của TWA |
| `sw.js` | Service worker — cho phép chạy offline, điều kiện của TWA |
| `privacy.html` | Chính sách quyền riêng tư song ngữ (bắt buộc khi khai Play Console) |
| `icons/` | Icon ứng dụng 192/512 + bản maskable |
| `store-assets/` | Icon 512, ảnh bìa 1024×500, 3 ảnh chụp màn hình điện thoại — dùng khi tạo trang ứng dụng trên Play Console |
| `twa-manifest.json` | Cấu hình Bubblewrap đã điền sẵn |
| `.well-known/assetlinks.json` | File xác thực tên miền (cần điền fingerprint ở Bước 3) |
| `.github/workflows/pages.yml` | Tự động deploy website mỗi khi đẩy code lên nhánh `main` |

## Bước 1 — Kích hoạt website (làm 1 lần)

1. Merge pull request vào nhánh `main`.
2. Vào repo trên GitHub → **Settings → Pages** → mục **Source** chọn **GitHub Actions** (nếu chưa tự bật).
3. Chờ workflow "Deploy to GitHub Pages" chạy xong (tab **Actions**), website sẽ hoạt động tại:
   **https://thuyhuongctu.github.io/BSS/**
4. Kiểm tra trên điện thoại: mở link, thấy trình duyệt gợi ý "Thêm vào màn hình chính" là PWA đã đạt chuẩn.

## Bước 2 — Tạo file .aab bằng Bubblewrap (công cụ chính thức của Google, miễn phí)

Cần cài Node.js trên máy tính cá nhân, sau đó:

```bash
npm i -g @bubblewrap/cli
cd <thư-mục-làm-việc>   # copy sẵn file twa-manifest.json trong repo vào đây
bubblewrap init --manifest https://thuyhuongctu.github.io/BSS/manifest.json
# Lần đầu chạy, Bubblewrap tự tải JDK + Android SDK (đồng ý các câu hỏi)
# Khi được hỏi thông tin, các giá trị khuyến nghị đã có trong twa-manifest.json:
#   Package ID: com.dothuyhuong.bizarena
#   Key alias:  bizarena
bubblewrap build
```

Kết quả: file **`app-release-bundle.aab`** (nộp lên Play) và file **`android.keystore`**.

> ⚠️ **CỰC KỲ QUAN TRỌNG**: Lưu `android.keystore` + mật khẩu vào nơi an toàn (Google Drive riêng + USB). Mất file này là mất khả năng cập nhật app vĩnh viễn — Google không cấp lại được.

## Bước 3 — Điền fingerprint vào assetlinks.json

Để app mở website toàn màn hình (không hiện thanh địa chỉ), Google cần xác thực bạn sở hữu tên miền:

```bash
keytool -list -v -keystore android.keystore -alias bizarena | grep SHA256
```

Copy chuỗi dạng `AA:BB:CC:...` rồi thay vào chỗ `THAY_BANG_SHA256_FINGERPRINT_CUA_KEYSTORE` trong file `.well-known/assetlinks.json` của repo, đẩy lên `main` để deploy lại.

## Bước 4 — Google Play Console

1. Đăng ký tài khoản nhà phát triển tại play.google.com/console (phí $25, một lần).
2. **Create app**: tên "BizArena", ngôn ngữ mặc định Tiếng Việt, loại **App**, chế độ **Free**.
3. Hoàn thành **Set up your app**:
   - Privacy Policy: dán link `https://thuyhuongctu.github.io/BSS/privacy.html`
   - Data safety: khai "Không thu thập dữ liệu" (đúng thực tế — app chỉ lưu localStorage)
   - Content rating: trả lời bảng câu hỏi (app giáo dục, không có nội dung nhạy cảm)
4. **Store listing**: dùng ảnh trong `store-assets/`:
   - App icon: `play-icon-512.png`
   - Feature graphic: `feature-graphic-1024x500.png`
   - Screenshots: `screenshot-setup.png`, `screenshot-play.png`, `screenshot-score.png`
5. **Production → Create new release** → tải file `.aab` lên → Review → **Start rollout**.

⏳ Tài khoản mới thường được duyệt trong 3–7 ngày.

## Gợi ý mô tả ứng dụng (Store listing)

**Mô tả ngắn (80 ký tự):**
> Trò chơi mô phỏng kinh doanh cho lớp học: 6 vòng đấu, 5 đội, bảng xếp hạng.

**Mô tả đầy đủ:**
> BizArena là trò chơi mô phỏng tình huống trong kinh doanh dành cho lớp học. 5 đội chơi cạnh tranh qua 6 vòng: mỗi vòng ra quyết định về Giá bán, Sản lượng và Ngân sách marketing; hệ thống tự tính doanh thu, chi phí, lợi nhuận theo hàm cầu kinh tế và các biến cố ngẫu nhiên (mùa Tết, dịch bệnh, lạm phát...). Có đồng hồ đếm giờ, bảng xếp hạng, lịch sử từng vòng, song ngữ Việt–Anh, chạy offline và không thu thập bất kỳ dữ liệu nào.
