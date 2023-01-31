# Images for MSM testing

1. rtsp-client
2. rtsp-server

Both images are ubuntu with FFMPEG

rtsp-server adds rtsp-simple-server (see [https://github.com/aler9/rtsp-simple-server]()) and a test video stream.

For rtsp-server do:

`ffmpeg -re -stream_loop -100 -i testsrc.mp4 -c copy -f rtsp rtsp://0.0.0.0:554/mystream`

For rtsp-client do:

`ffmpeg -rtsp_transport tcp -i rtsp://10.43.10.1:554/mystream -c copy output.mp4`
