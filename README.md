# BizArena — Mô phỏng tình huống trong kinh doanh

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21421329.svg)](https://doi.org/10.5281/zenodo.21421329)

Trò chơi mô phỏng kinh doanh dành cho lớp học: 6 vòng đấu, 5 đội chơi, hàm cầu kinh tế, biến cố ngẫu nhiên, bảng xếp hạng — song ngữ Việt–Anh, chạy offline (PWA).

> **Trích dẫn (Zenodo):** Do, T. H. (2026). *BizArena — Business Situation Simulation* [Phần mềm máy tính]. Zenodo. https://doi.org/10.5281/zenodo.21421329

- **Website:** https://thuyhuongctu.github.io/BSS/
- **Chính sách quyền riêng tư:** https://thuyhuongctu.github.io/BSS/privacy.html
- **Tác giả:** PhD Candidate Do Thuy Huong — © 2026, bảo lưu mọi quyền.
- **Phiên bản:** 2.2 (07/2026)

## Cấu trúc

- `index.html` — toàn bộ ứng dụng (tự chứa, đã nhúng font)
- `manifest.json`, `sw.js`, `icons/` — lớp PWA (cài được lên màn hình chính, chạy offline)
- `privacy.html` — chính sách quyền riêng tư song ngữ
- `store-assets/`, `twa-manifest.json`, `.well-known/assetlinks.json` — bộ đóng gói Google Play (TWA)
- `HUONG_DAN_CH_PLAY.md` — hướng dẫn từng bước đưa app lên CH Play

## Triển khai

Website tự động deploy lên GitHub Pages qua GitHub Actions mỗi khi đẩy lên nhánh `main` (xem `.github/workflows/pages.yml`).
