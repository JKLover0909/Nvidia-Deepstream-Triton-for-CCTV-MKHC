# CLAUDE.md

Guidance for Claude Code (and similar agents) working in this repository.

## What this repo is

Pipeline NVIDIA DeepStream chạy inference (nvinfer / YOLO11n person detection) trên luồng RTSP camera CCTV tại MKHC. `Notebook/Code.ipynb` là notebook thử nghiệm/debug pipeline (gst-launch).

## ⚠️ Đã xử lý sự cố bảo mật ngày 2026-09-28

`README.md` và `Notebook/Code.ipynb` từng chứa **credentials RTSP thật dạng plaintext** (`rtsp://root:<password>@<internal-ip>:554/...`) ngay trong bản HEAD hiện tại (không chỉ lịch sử cũ). Đã scrub và thay bằng biến môi trường / placeholder. **Đổi mật khẩu camera đó nếu chưa đổi** — ai đã clone repo trước khi sửa vẫn còn giữ credential cũ.

**Quy tắc bắt buộc từ giờ**: không bao giờ đặt `rtsp://user:pass@ip` trực tiếp trong code, notebook, README, hay file config — luôn dùng biến môi trường (`RTSP_URL`).

## Lưu ý cấu trúc

- `deepstream/deepstream-8.0/` (54MB, ~1400 file) là **toàn bộ SDK NVIDIA DeepStream** được commit nguyên khối vào repo — không phải code của user, thuộc giấy phép riêng của NVIDIA. Đây là repo bloat đáng kể; cân nhắc bỏ khỏi git (dùng submodule/install script thay vì commit thẳng) — nhưng đây là quyết định lớn, **hỏi lại người dùng trước khi xóa**, không tự ý làm.
- Các file config DeepStream mẫu trong `deepstream/deepstream-8.0/sources/.../configs/*.txt` có chứa `rtsp://foo.com/...` — đây là placeholder gốc của NVIDIA, không phải bí mật thật, không cần sửa.

## Kiểm thử an toàn

Không có camera RTSP thật/GPU NVIDIA trong môi trường agent — chỉ kiểm tra syntax, không chạy `deepstream_test_3*.py` hay lệnh `gst-launch` thật.
