python3 deepstream_test_3.py -i "rtsp://root:Mkvc%402025@192.168.40.40:554/media/stream.sdp?profile=Profile101" 

python3 deepstream_test_3.py -i "rtsp://root:Mkvc%402025@192.168.40.40:554/media/stream.sdp?profile=Profile100" -g nvinfer -c dstest3_meiko.txt 

python3 deepstream_test_3_yolo11n_person.py -i "rtsp://root:Mkvc%402025@192.168.40.40:554/media/stream.sdp?profile=Profile100" -c dstest3_yolo11n_person.txt