---
title: "OpenCV"
date: 2023-06-10T02:04:26+08:00
weight: 2
---

## Build 

Prebuilt packages do not include gstreamer support (mainly for RTSP streaming) and python bindings. 

### Source compilation steps

TODO

## Known Issues

VideoCapture() with cv::CAP_GSTREAMER not aware of rtsp connection error. 
Will keep grabbing same image.
