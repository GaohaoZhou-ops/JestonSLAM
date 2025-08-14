# FAST-LIO

这个仓库复现了 Fast-Lio 工程，涉及到以下源码链接：

* FAST-LIO：[https://github.com/hku-mars/FAST_LIO#](https://github.com/hku-mars/FAST_LIO#)
* Livox-SDK2：[https://github.com/Livox-SDK/Livox-SDK2](https://github.com/Livox-SDK/Livox-SDK2)
* livox_ros_driver：[https://github.com/Livox-SDK/livox_ros_driver#](https://github.com/Livox-SDK/livox_ros_driver#)

-----
# Step1. 初始化子模块

```bash
$ cd JestonSLAM
$ git submodule update --init third_party/Livox-SDK2 
$ git submodule update --init fast_lio_project/src/FAST_LIO
$ git submodule update --init fast_lio_project/src/livox_ros_driver
```

# Step2. 安装 Livox-SDK2

```bash
$ cd JestonSLAM
$ cd third_party/Livox-SDK2
$ mkdir build && cd build
$ cmake ..
$ make -j10
$ sudo make install 
```

# Step3. 编译 FAST_LIO 工程

如果你的终端默认启动了 conda 的 base 环境，需要在编译之前先退出环境：

```bash
$ conda deactivate 
```

执行编译命令：


```bash
$ cd JestonSLAM
$ cd fast_lio_project/src/FAST_LIO
$ git submodule update --init
$ cd ../../
$ catkin_make
```

# Step4. 运行示例

```bash
$ cd JestonSLAM
$ cd fast_lio_project/
$ source devel/setup.bash
$ roslaunch fast_lio mapping_mid360.launch 
```

