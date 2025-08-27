# Voxel Map

This repository replicates the VoxelMap project, including the following source code links:

* VoxelMap: [https://github.com/hku-mars/VoxelMap?tab=readme-ov-file#](https://github.com/hku-mars/VoxelMap?tab=readme-ov-file#)
* livox_ros_driver: [https://github.com/Livox-SDK/livox_ros_driver#](https://github.com/Livox-SDK/livox_ros_driver#)
* librealsense: [https://github.com/IntelRealSense/librealsense](https://github.com/IntelRealSense/librealsense)
* realsense-ros: [https://github.com/IntelRealSense/realsense-ros#](https://github.com/IntelRealSense/realsense-ros#)

Overall, there are no special compilation requirements for this project. Simply follow the official instructions step by step.

----
# Step 1. Initialize the submodule

```bash
$ cd JetsonSLAM
$ git submodule update --init voxel_map_project/src/VoxelMap/
$ git submodule update --init voxel_map_project/src/livox_ros_driver/
```

----
# Step 2. Compile the project

```bash
$ cd JetsonSLAM
$ cd voxel_map_project

$ catkin_make
```

If you encounter errors related to the livox header files during compilation, you can run the following command after the compilation is complete to recompile:

```bash
$ source devel/setup.bash
$ catkin_make
```

----
# Step 3. Run the example

```bash
$ cd JetsonSLAM/voxel_map_project
$ source devel/setup.bash
$ roslaunch voxel_map mapping_l515.launch
```

You can download an example from the [dataset](https://connecthkuhk-my.sharepoint.com/personal/ycj1_connect_hku_hk/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Fycj1%5Fconnect%5Fhku%5Fhk%2FDocuments%2FL515%5Fdataset&ga=1) sample provided in the VoxelMap official repository, or download `l5152.bag` from my cloud drive. Data Pack:

```bash
https://pan.baidu.com/s/1nIBZoz2aIX9HakQI_pjKFA?pwd=5fp3
```

[Note]: **We've found that the data packs provided in the official repository may have issues. If you receive the error `Error reading from file: wanted 4 bytes, read 0 bytes` when playing the data pack, you will need to reset the index using the following command. If you obtained the data packs directly from our network drive, this step is not necessary. **

```bash
$ rosbag reindex l5152.bag
```

* Play the data pack:

```bash
$ rosbag play l5152.bag
```

---
# Step 4. Using Your Own L515 Camera

Since the L515 The discounted camera is no longer maintained. If you wish to use your own camera in this project, you will need to manually compile librealsense against version `v2.50.0`. If you plan to use the D435i camera, simply modify the point cloud topic in the project configuration file.

## 4.1 Pull Source Code and Switch Branches
* Initialize the repository:
```bash
$ cd JetsonSLAM

$ git submodule update --init voxel_map_project/librealsense
$ git submodule update --init voxel_map_project/src/realsense-ros
```

* Switch to a specific version of `librealsense`:

```bash
$ cd JetsonSLAM
$ cd voxel_map_project/librealsense

$ git checkout v2.50.0
```

* Switch to a specific version of `realsense-ros`:

```bash
$ cd JetsonSLAM
$ cd voxel_map_project/src/realsense-ros

$ git checkout ros1-legacy
```

## 4.2 Compile librealsense

```bash
$ cd JetsonSLAM
$ cd voxel_map_project/librealsense

$ mkdir build && cd build
$ cmake ../ -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=../install
$ make -j${nproc}
$ make install # Do not use sudo make install
```

## 4.3 Compiling the Workspace

* Modify the `realsense_ws/src/realsense-ros/realsense2_camera/CMakeLists.txt` file:

```cmake
# Location 1: Add the `realsense2_DIR` path. Modify it to your desired path.

set(realsense2_DIR "/home/orin/Desktop/JetsonSLAM/voxel_map_project/librealsense/install/lib/cmake/realsense2")

# Location 2: Add OpenCV Library
find_package(OpenCV REQUIRED)

# Location 3: Add header library
include_directories(
include
${realsense2_INCLUDE_DIR}
${catkin_INCLUDE_DIRS}
${OpenCV_INCLUDE_DIRS}
)

# Location 4: Add link libraries
target_link_libraries(${PROJECT_NAME}
${realsense2_LIBRARY}
${catkin_LIBRARIES}
${CMAKE_THREAD_LIBS_INIT}
${OpenCV_LIBS}
)
```

* Compile workspace:

```bash
$ cd JetsonSLAM
$ cd voxel_map_project

$ catkin_make
```

## 4.4 Using the L515 Camera

Every time you start the L515 Before installing the camera, you need to set the environment variables. If you plan to use this camera long-term, it is recommended to add the environment variables directly to the `~/.bashrc` file. If you only plan to use it in this project, simply add the following environment variables in the terminal:

```bash
$ export LD_LIBRARY_PATH=/home/orin/Desktop/JetsonSLAM/voxel_map_project/librealsense/install/lib:$LD_LIBRARY_PATH
```

![l515](l515.png)