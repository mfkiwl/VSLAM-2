# TX2开发记录  

硬件： TX2核心板 + 瑞泰9003U扩展板  

[无处不在的小土](https://gaoyichao.com/Xiaotu/?book=ros&title=%E7%94%A8SDF%E6%96%87%E4%BB%B6%E6%A8%A1%E6%8B%9F%E6%BF%80%E5%85%89%E9%9B%B7%E8%BE%BE)


## 瑞泰官方资料  

http://yun.realtimes.cn/   账号realtimes    密码realtimes2020  


## 系统备份（配合）





## cv_bridge重新安装  
https://editor.csdn.net/md/?articleId=115000313  
https://blog.csdn.net/fb_941219/article/details/105705759

刷Jetpack4.3
Opencv3.4.1 使用cuda10.0编译
下载melodic版本的cv_bridge，在设置CMakelists中设置opencv路径编译，安装在/usr/local/cv_bridge341/
后面在ROS程序的CMake文件的find_package前设置上cv_bridge341的路径

### Opencv3.4.1安装


jasper 2.0.12 

## cv_bridge
具体操作参考：
[ROS工程不使用ROS自带的OpenCV](https://blog.csdn.net/fb_941219/article/details/105705759)
需要注意的就是
注意切换好cv_bridge的分支与自己的ros版本对应
CMakeLists.txt文件中正确设置好Opencv版本和路径
记录一下我自己的设置
```cpp
set(OpenCV_DIR "usr/local/share/OpenCV")
find_package(OpenCV 3.4.1 REQUIRED
   COMPONENTS
    opencv_core
    opencv_imgproc
    opencv_imgcodecs
 CONFIG
)
```
另外就是编译时我设置的安装路径如下

```bash
cmake -D CMAKE_INSTALL_PREFIX=/usr/local/cv_bridge341 ..
```
因此需要在用到cv_bridge的地方先设置好路径
```cpp
set(cv_bridge_DIR /usr/local/cv_bridge341/share/cv_bridge/cmake)
find_package(
  cv_bridge
)
```


