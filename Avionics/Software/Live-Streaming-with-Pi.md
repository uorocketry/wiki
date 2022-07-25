---
title: Live Streaming with Pi
description: 
published: true
date: 2022-07-25T23:33:48.989Z
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

For further streams, add on another folder after `/live` such as `/live/1`.

***

The webcam pi has everything setup with a script called `stream.sh` in the home folder. To stream multiple cameras use screen or `&` to run commands in parrallel.

***

To set max bandwith usage, see https://superuser.com/questions/945413/how-to-consider-bitrate-maxrate-and-bufsize-of-a-video-for-web

> `bufsize` will determine how religious ffmpeg is about keeping your bitrate constant. If you set a `bufsize` of 64k, as per [FFmpeg Wiki: Limiting the output bitrate][1], it will calculate its current bitrate every 64 kilobytes and adjust accordingly. Smaller sizes for `bufsize` can be harmful to quality in that they don't allow enough space between checks for x264 to do sudden changes - you will get blockiness.
> 
> If your `maxrate` is 640kbps, and your `bufsize` is 64k, then every tenth of a second x264 would check. This is sub-optimal - [FFmpeg Wiki: Encoding for streaming sites][2] recommends to run it every 1 to 2 seconds. If this didn't make sense, think of it as `maxrate`/`bufsize` = frequency of checks. Keep this frequency between 1 and 2 seconds as a rule of thumb.
> 
> If you set both `maxrate` and `bufsize`, you should:
> 
>  - set `maxrate` to whatever your lowest upload speed will likely be (in the [ffmpeg wiki example][2], this is 80% of total upload speed, but your mileage may vary). 
>  - set `bufsize` to somewhere between the same as your `maxrate` (one second) and twice of your `maxrate` (2 seconds). If this is still not low enough, lower your `maxrate` and then re-set `bufsize` accordingly. 
> 
> Then, you'll have to play around a bit, but since you have to start somewhere I'd just start at a `maxrate` around 600k, which was usually satisfying enough for me back before I used `crf` for everything.
> 
> If you'd like, you can try lower values for `bufsize`, like for every three or four seconds, just to see how the value changes how your output looks. Then you can determine how much you should worry about it for your video.
> 
> There is no normal value, really - what `crf` does is to optimize output based on what it thinks is the best buffer size for maintaining whatever it's rate is set at. It tries to keep as low a file size while maintaining some quality, at the cost of occasional spikes.
