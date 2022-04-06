# opencv安装
## opencv 具体安装步骤
###安装opencv依赖库
`sudo apt-get install cmake libgtk2.0-dev libavcodec-dev libavformat-devlibjpeg.devlibpng-devlibtiffdevlibtiff5.devlibswscale-devlibjasper-devlibcurl4-openssl-dev libtbb2 libdc1394-22-dev`

###可能出现的错误
软件包无法下载，要不运行 apt-get update 或者加上 --fix-missing 的选项再试试？
解决方法：
`sudo apt-get update sudo apt-get install --fix-missing`


OpenCV安装libjasper-dev依赖包错误：E: Unable to locate package libjasper-dev

解决方法：

```
sudo add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
sudo apt update
sudo apt install libjasper-de
```

###安装opencv

在opencv-3.2.0同级别目录下创建文件夹opencv-3.2.0_install，mybuild目录下执行

`cmake -D CMAKE_BUILD_TYPE=Release -D OPENCV_GENERATE_PKGCONFIG=ON -D CMAKE_INSTALL_PREFIX=/home/jjw/imgproc/opencv-3.2.0_install -D OPENCV_EXTRA_MODULES_PATH=/home/jjw/imgproc/opencv_contrib-3.2.0/modules ..`

问题：Downloading ippicv_linux_20151201.tgz...或者别的文件名错误。

解决办法:
下载`ippicv_linux_20151201.tgz`然后复制替换到

`opencv-3.2.0/3rdparty/ippicv/downloads/linux-808b791a6eac9ed78d32a7666804320e`

下载`protobuf-cpp-3.1.0.tar.gz`然后复制替换

`opencv_contrib-3.2.0/modules/dnn/.download/bd5e3.../v3.1.0/`

下载.i文件，放入

`opencv_contrib-3.2.0/modules/xfeatures2d/src/ `

###进入mybuild目录下执行
`make -j4`

`make install`


出错就根据提示进入代码中替换，没有提示的那个用`AVFMT_NOFILE`替换，若有其他情况可以查看日志

###添加 opencv 库 :

打开或创建 `opencv.conf` 文件，并添加 opencv 安装路径 

`sudo gedit /etc/ld.so.conf.d/opencv.conf /home/ljx/imgproc/opencv-3.2.0_install/lib <添加内容>`

###使 opencv 配置文件生效 :

`sudo ldconfig`

###配置 bash 环境变量 :

`sudo gedit ~/.bashrc `

在文件末尾添加如下内容 

`export PKG_CONFIG_PATH=/home/ljx/imgproc/opencv-3.2.0_install/lib/pkgconfig`

生效配置文件 :

`source ~/.bashrc <使环境变量立即生效> `

验证 opencv 环境配置是否成功 :

`pkg-config --cflags --libs opencv`

###opencv 测试 :

`opencv-3.2.0/samples/cpp/example_cmake` 目录配置编译之前需要修改`CMakeLists.txt`


在文件中添加
`set(OpenCV_DIR /home/edu/ai/opencv-3.2.0/mybuild)`

执行 cmake .`用于生成 `makefile 

`cmake .`

执行

 `make`

执行生成的可执行文件 

`./opencv_example`
