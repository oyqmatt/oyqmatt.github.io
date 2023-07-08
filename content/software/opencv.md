---
title: "OpenCV"
date: 2023-06-10T02:04:26+08:00
weight: 3
---

## Build 

Prebuilt packages do not include gstreamer support (mainly for RTSP streaming) and python bindings. 

### Source compilation steps
Instructions based on [this](https://developer.ridgerun.com/wiki/index.php/Compiling_OpenCV_from_Source)

Install dependencies
```bash
sudo apt install build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev \
python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libdc1394-22-dev python3-pip python3-numpy
```

For Gstreamer support
```
sudo apt install gstreamer1.0*
sudo apt install ubuntu-restricted-extras
sudo apt install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
```

Clone and compile
```
export VERSION=4.8.0
git clone https://github.com/opencv/opencv.git -b $VERSION --depth 1
git clone https://github.com/RidgeRun/opencv_contrib.git --depth 1
```

```
cd opencv
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D BUILD_EXAMPLES=OFF \
-D INSTALL_PYTHON_EXAMPLES=OFF \
-D INSTALL_C_EXAMPLES=OFF \
-D PYTHON_EXECUTABLE=$(which python2) \
-D BUILD_opencv_python2=OFF \
-D PYTHON3_EXECUTABLE=$(which python3) \
-D PYTHON3_INCLUDE_DIR=$(python3 -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())") \
-D PYTHON3_PACKAGES_PATH=$(python3 -c "from distutils.sysconfig import get_python_lib; print(get_python_lib())") \
 ..
```

**Contrib Extra Modules**
```
-D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules/ \
```
**Gstreamer**
```
-D WITH_GSTREAMER=ON \
```
**CUDA**
```
-D WITH_CUDA=ON \
```

## Known Issues

VideoCapture() with cv::CAP_GSTREAMER not aware of rtsp connection error. 
Will keep grabbing same image.
