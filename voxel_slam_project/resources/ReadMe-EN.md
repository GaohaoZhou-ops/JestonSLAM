# Voxel SLAM

This repository replicates the Voxel-SLAM project, including the following source code links:

* Voxel-SLAM: [https://github.com/hku-mars/Voxel-SLAM#](https://github.com/hku-mars/Voxel-SLAM#)
* livox_ros_driver: [https://github.com/Livox-SDK/livox_ros_driver#](https://github.com/Livox-SDK/livox_ros_driver#)

Overall, there are no special requirements for compiling this project; simply follow the official instructions step by step.

----
# Step 1. Initialize the submodule

```bash
$ cd JetsonSLAM
$ git submodule update --init voxel_slam_project/src/Voxel-SLAM/
$ git submodule update --init voxel_slam_project/src/livox_ros_driver/
```

----
# Step 2. Compile the project

```bash
$ cd JetsonSLAM
$ cd voxel_slam_project

$ catkin_make
```

----
# Step 3. Run the example

```bash
$ cd JetsonSLAM/voxel_slam_project
$ source devel/setup.bash
$ roslaunch voxel_slam vxlm_avia.launch
```

You can find the examples in the official Fast-Livo2 repository. Download an example from the [Dataset](https://connecthkuhk-my.sharepoint.com/personal/zhengcr_connect_hku_hk/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Fzhengcr%5Fconnect%5Fhku%5Fhk%2FDocuments%2Ffast%2Dlivo2%2Ddataset&ga=1) sample, or download the `CBD_Building_01.bag` data package from my network drive:

```bash
https://pan.baidu.com/s/1nIBZoz2aIX9HakQI_pjKFA?pwd=5fp3
```

Before running, you need to check the configuration file corresponding to the launch file. For example, here we use `launch/mapping_avia.launch`, so the configuration file we need to check is `VoxelSLAM/config/avia.yaml`:

```yaml
General:
lid_topic: "/livox/lidar" 
imu_topic: "/livox/imu" 
# The file path of the map to be saved 
save_path: /home/orin/Desktop/JetsonSLAM/voxel_slam_project"
```

* Play data package:

```bash
$ rosbag play CBD_Building_01.bag
```

![mapping](mapping.png)