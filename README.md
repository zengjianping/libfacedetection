# libfacedetection

This is a binary library for face detection in images. 
The 32-bit and 64-bit dll files are provided.
To achieve better performance, the 64-bit dll is recommended.

examples/libfacedetect-example.cpp shows how to use the library.

Comparison on Windows
-------------

| Method             | Time<br>(Win32) | FPS<br>(Win32) |Time<br>(X64)   | FPS<br>(X64)  |Time<br>(X64,<br>Multi-Thread) | FPS<br>(X64,<br>Multi-Thread) | Misc   |
|--------------------|-------------|------------|------------|-----------|-----------------------|-----------------------|--------|
|frontal             |  2.92ms     | 342.5      | 2.41ms     | 414.9     | 0.652ms     | 1533.1     | Yaw angle: -60 to 60 degrees|
|frontal-surveillance|  3.83ms     | 261.1      | 3.37ms     | 269.7     | 0.944ms     | 1059.8     | Yaw angle: -70 to 70 degrees |
|multiview           |  7.12ms     | 140.4      | 5.81ms     | 172.1     | 1.597ms     |  626.4     | Yaw angle: -90 to 90 degrees |
|multiview_reinforce | 10.95ms     |  91.3      | 9.15ms     | 109.3     | 2.725ms     |  367.0     | Yaw angle: -90 to 90 degrees |

* 640x480 image size (VGA), scale=1.2, minimal window size = 48
* Intel(R) Core(TM) i7-4770 CPU @ 3.4GHz
* Only one CPU core is utilized. Multi-core parallelization is *disabled* for these four methods.


Comparison on ARM
-------------

| Method             | Time   | FPS  | Misc   |
|--------------------|--------|------|--------|
|frontal             |  12.5ms| 80.0 | Yaw angle: -60 to 60 degrees|
|frontal-surveillance|  15.7ms| 63.7 | Yaw angle: -70 to 70 degrees |
|multiview           |  27.8ms| 36.0 | Yaw angle: -90 to 90 degrees |
|multiview_reinforce |  38.4ms| 26.0 | Yaw angle: -90 to 90 degrees |

* 640x480 image size (VGA), scale=1.2, minimal window size = 48
* NVIDIA TK1 "4-Plus-1" 2.32GHz ARM quad-core Cortex-A15 CPU
* Multi-core parallelization is disabled.
* C programming language, and no SIMD instruction is used.

The dll cannot run on ARM. The library should be recompiled from source code for ARM compatibility. If you need the source code, a commercial license is needed.

Evaluation
-------------
FDDB: http://vis-www.cs.umass.edu/fddb/index.html

![Evaluation on FDDB](https://github.com/ShiqiYu/libfacedetection/blob/master/FDDB-results-of-4functions.png "Evaluation on FDDB")

* scale=1.08
* minimal window size = 16
* the heights of the face rectangles are scaled to 1.2 to fit the ground truth data in FDDB.


Author
-------------
* Shiqi Yu <shiqi.yu@gmail.com> Computer Vision Institute, Shenzhen University, China

Contributors
-------------
* Shengyin Wu, Shenzhen University, China
* Dong Xu, Shenzhen University, China
