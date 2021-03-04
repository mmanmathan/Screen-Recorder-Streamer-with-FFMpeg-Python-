# Screen-Recorder-Streamer-with-FFMpeg-Python-
Desktop Screen &amp; Audio Recorder with FFMpeg &amp; Python, with Scheduler.

2021.03.04 
Trying to implement 5mins recorder + streamer, both audios (mic and out)  and screen. Stream and record simultaneously. External program (python) be able to kill the ffmpeg after the set duration, in case ffmpeg doesnot automatically stop after the set duration. MKV format is stable (verified), in case of killing the ffmpeg from outside.

1.	64k audio, 400k video, full resol, 7.5fps both rec & stream. Approx 8mb for 1min = 500mb for 1 hr.
ffmpeg -f gdigrab -framerate 7.5 -i desktop -f dshow -i audio="Microphone Array (Realtek High Definition Audio)"  -b:a 64k -f mpegts -t 60 - | ffmpeg  -f mpegts -i - -c copy  -f mpegts udp://192.168.0.242:1234?pkt_size=1316  -c  copy  -b 400k TestFFmpegPy.mkv

