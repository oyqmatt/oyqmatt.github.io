---
title: "Gstreamer"
date: 2023-07-08T02:29:05+08:00
weight: 4
---

## GStreamer

### To link third party apps
```bash
export GST_PLUGIN_PATH=$GST_PLUGIN_PATH:[path_to_plugin]
```

### To start generic sources
file://{path_to_file}

rtsp://{admin}:{password}@{path_to_rtsp}

```bash
gst-launch-1.0 uridecodebin uri={uri} ! fpsdisplaysink
gst-launch-1.0 v4l2src device=path ! autovideconvert ! fpsdisplaysink
```

### Other cameras
#### CSI Camera (Nvidia SBC)

```bash
gst-launch-1.0 nvarguscamerasrc ! nvvideoconvert ! nv3dsink
```

#### GigE Camera (Aravis SDK)

Install Aravis SDK [here](https://aravisproject.github.io/aravis/building.html)

```bash
# e.g. x86 computers
export GST_PLUGIN_PATH=$GST_PLUGIN_PATH:/usr/local/lib/x86_64-linux-gnu/gstreamer-1.0/
gst-launch-1.0 aravissrc name=[ip_address] ! bgr2rgb ! autovideoconvert ! fpsdisplaysink
```

### Debugging
Start low and increase verbosity generally I find 2-4 sufficient
```bash
export GST_DEBUG=[1-9]
```