# NVIDIA DeepStream + Triton — CCTV MKHC

DeepStream pipeline chạy inference (nvinfer / YOLO11n person detection) trên luồng RTSP camera CCTV.

## Ví dụ chạy

```bash
export RTSP_URL='rtsp://<user>:<password>@<camera-ip>:554/media/stream.sdp?profile=Profile101'

python3 deepstream_test_3.py -i "$RTSP_URL"

python3 deepstream_test_3.py -i "$RTSP_URL" -g nvinfer -c dstest3_meiko.txt

python3 deepstream_test_3_yolo11n_person.py -i "$RTSP_URL" -c dstest3_yolo11n_person.txt
```

**Không đặt URL/credential camera trực tiếp trong source, notebook, hay README** — luôn dùng biến môi trường.
