# Point-LIO

这个仓库复现了 Point-Lio 工程，涉及到以下源码链接：

* Point-LIO：[https://github.com/hku-mars/Point-LIO#](https://github.com/hku-mars/Point-LIO#)；
* livox_ros_driver: [https://github.com/Livox-SDK/livox_ros_driver#](https://github.com/Livox-SDK/livox_ros_driver#)；

----
# Step1. 初始化子模块

```bash
$ cd JetsonSLAM
$ git submodule update --init --recursive point_lio_project/src/Point-LIO/
$ git submodule update --init point_lio_project/src/livox_ros_driver/
```

# Step2. 安装依赖库

```bash
$ sudo apt-get install ros-$ROS_DISTRO-pcl-conversions
$ sudo apt-get install libeigen3-dev
```

# Step3. 编译源码

如果你的终端默认开启了 conda 的 base 环境，建议在编译之前退出：

```bash
$ conda deactivate
```

执行编译：

```bash
$ cd JetsonSLAM/point_lio_project
$ catkin_make
```

# Step4. 运行示例

* 修改配置文件 `point_lio_project/src/Point-LIO/config/avia.yaml` 用以保存地图，否则将无法保存地图：

```yaml
pcd_save:
    pcd_save_en: true       # false
    interval: -1
```

* 运行建图节点：

```bash
$ cd JetsonSLAM
$ cd point_lio_project
$ source devel/setup.bash
$ roslaunch point_lio mapping_avia.launch
```

你可以在 Fast-Livo2 官方仓库中提供的 [数据集](https://connecthkuhk-my.sharepoint.com/personal/zhengcr_connect_hku_hk/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Fzhengcr%5Fconnect%5Fhku%5Fhk%2FDocuments%2Ffast%2Dlivo2%2Ddataset&ga=1) 样本中下载一个示例，或者在我的网盘中拉取 `CBD_Building_01.bag` 数据包：

```bash
https://pan.baidu.com/s/1nIBZoz2aIX9HakQI_pjKFA?pwd=5fp3
```

* 播放数据包：

```bash
$ rosbag play CBD_Building_01.bag
```

![mapping](mapping.png)

