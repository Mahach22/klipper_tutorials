# klipper_tutorials



настройка камер:

устанавливаем crownest
подключаем камеры
ищем в логах подобное устройство /dev/v4l/by-id/usb-046d_0825_A991C400-video-index0 или два 
```
cat /home/orangepi/printer_data/logs/crowsnest.log | grep video
```

добавляем в crownest.conf

пример моего конфига

```

[crowsnest]
log_path: /home/orangepi/printer_data/logs/crowsnest.log
log_level: verbose                      # Valid Options are quiet/verbose/debug
delete_log: false                       # Deletes log on every restart, if set to true
no_proxy: false

[cam Logitech]
mode: ustreamer                         # ustreamer - Provides mjpg and snapshots. (All devices)
                                        # camera-streamer - Provides webrtc, mjpg and snapshots. (rpi + Raspi OS based only)
enable_rtsp: true                      # If camera-streamer is used, this enables also usage of an rtsp server
rtsp_port: 8554                         # Set different ports for each device!
port: 8080                              # HTTP/MJPG Stream/Snapshot Port
device: /dev/v4l/by-id/usb-046d_0825_A991C400-video-index0                     # See Log for available ...
resolution: 1280x720                     # widthxheight format
max_fps: 15                             # If Hardware Supports this it will be forced, otherwise ignored/coerced.
#custom_flags:                          # You can run the Stream Services with custom flags.
#v4l2ctl:                               # Add v4l2-ctl parameters to setup your camera, see Log what your cam is capable of.


[cam Sonix]
mode: ustreamer                         # ustreamer - Provides mjpg and snapshots. (All devices)
                                        # camera-streamer - Provides webrtc, mjpg and snapshots. (rpi + Raspi OS based only)
enable_rtsp: true                      # If camera-streamer is used, this enables also usage of an rtsp server
rtsp_port: 8555                         # Set different ports for each device!
port: 8081                              # HTTP/MJPG Stream/Snapshot Port
device: /dev/v4l/by-id/usb-Sonix_Technology_Co.__Ltd._Webcam_Webcam-video-index0                     # See Log for available ...
resolution: 640x480                     # widthxheight format
max_fps: 15                             # If Hardware Supports this it will be forced, otherwise ignored/coerced.
#custom_flags:                          # You can run the Stream Services with custom flags.
#v4l2ctl:                               # Add v4l2-ctl parameters to setup your camera, see Log what your cam is capable of.


```
