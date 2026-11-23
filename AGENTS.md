# CLAUDE.md

Guidance for Claude Code (and similar agents) working in this repository.

## What this repo is

Pipeline NVIDIA DeepStream chạy inference (nvinfer / YOLO11n person detection) trên luồng RTSP camera CCTV tại MKHC. `Notebook/Code.ipynb` là notebook thử nghiệm/debug pipeline (gst-launch).

## ⚠️ Đã xử lý sự cố bảo mật ngày 2026-09-28

`README.md` và `Notebook/Code.ipynb` từng chứa **credentials RTSP thật dạng plaintext** (`rtsp://root:<password>@<internal-ip>:554/...`) ngay trong bản HEAD hiện tại (không chỉ lịch sử cũ). Đã scrub và thay bằng biến môi trường / placeholder. **Đổi mật khẩu camera đó nếu chưa đổi** — ai đã clone repo trước khi sửa vẫn còn giữ credential cũ.

**Quy tắc bắt buộc từ giờ**: không bao giờ đặt `rtsp://user:pass@ip` trực tiếp trong code, notebook, README, hay file config — luôn dùng biến môi trường (`RTSP_URL`).

## Lưu ý cấu trúc

- NVIDIA DeepStream SDK 8.0 **không còn được commit** (đã gỡ ~1.400 file / 54MB khỏi git 2026-11-23): cài SDK từ NVIDIA (mặc định `/opt/nvidia/deepstream/deepstream-8.0`). Trong `deepstream/deepstream-8.0/` repo chỉ giữ `samples/models/Meiko_CCTV/labels.txt` (7 lớp PPE của dự án, notebook dùng đường dẫn này); `.gitignore` chặn phần còn lại. Trọng số `ppe_detector.pt/.onnx/.engine` cũng không commit. `deepstream/deepstream` là symlink tới `deepstream-8.0`.
- Các file config/mẫu của SDK (`samples/configs/...`, `sources/...`) lấy từ bản cài DeepStream, không có trong repo.

## Kiểm thử an toàn

Không có camera RTSP thật/GPU NVIDIA trong môi trường agent — chỉ kiểm tra syntax, không chạy `deepstream_test_3*.py` hay lệnh `gst-launch` thật.
