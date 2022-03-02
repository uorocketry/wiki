---
title: Live Streaming with Pi
description: 
published: true
date: 2022-03-02T22:52:39.618Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:33:31.768Z
---

The raspberry pi can be used as a camera feed forwarder. To do this, connect a USB capture card to the pi, and it will act like a normal video source.

If using a runcam, this can be connected with an AV capture card and a micro USB to TV-Out cable.

![Cable connection](https://i.imgur.com/1YCzmoR.jpg)

On the rasperry pi, install ffmpeg, and nginx with the rtmp module

```bash
sudo apt install ffmpeg nginx libnginx-mod-rtmp -y
```

Setup the nginx config to be an RTMP forwarder with a low buffer (to reduce latency)

```
load_module /usr/lib/nginx/modules/ngx_stream_module.so;
load_module /usr/lib/nginx/modules/ngx_rtmp_module.so;

worker_processes 1;

events {

}

rtmp {
    server {
        listen 1935;
        chunk_size 2096;

        application live {
            live on;
            record off;
        }
    }
}
```

Restart the nginx service

```bash
sudo service nginx reload
```

You can now stream the video signal with ffmpeg

```bash
ffmpeg -re -i /dev/video0 -f flv -b:v 3000k rtmp://localhost/live
```

If there are multiple cameras connected, increment the number beside `/dev/video`

***

You can view this steam in OBS or VLC by opening up a network stream with `rtmp://<IP of RaspberryPi>/live`. In OBS, you use a "Media Source".

![OBS screenshot](https://i.imgur.com/zC9xZoi.png)
