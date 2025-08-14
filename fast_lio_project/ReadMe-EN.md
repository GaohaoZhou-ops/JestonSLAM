# FAST-LIO

This repository replicates the Fast-LIO project and includes the following source code links:

* FAST-LIO: [https://github.com/hku-mars/FAST_LIO#](https://github.com/hku-mars/FAST_LIO#)
* Livox-SDK2: [https://github.com/Livox-SDK/Livox-SDK2](https://github.com/Livox-SDK/Livox-SDK2)
* livox_ros_driver: [https://github.com/Livox-SDK/livox_ros_driver#](https://github.com/Livox-SDK/livox_ros_driver#)

-----
# Step 1. Initialize the submodule

```bash
$ cd JestonSLAM
$ git submodule update --init third_party/Livox-SDK2
$ git submodule update --init fast_lio_project/src/FAST_LIO
$ git submodule update --init fast_lio_project/src/livox_ros_driver
```

# Step 2. Install Livox-SDK2

```bash
$ cd JestonSLAM
$ cd third_party/Livox-SDK2
$ mkdir build && cd build
$ cmake ..
$ make -j10
$ sudo make install
```

# Step 3. Compile the FAST_LIO project

If your terminal uses the conda base environment by default, exit it before compiling:

```bash
$ conda deactivate
```

Execute the compile command:

```bash
$ cd JestonSLAM
$ cd fast_lio_project/src/FAST_LIO
$ git submodule update --init
$ cd ../../
$ catkin_make
```

# Step4. Run the example

```bash
$ cd JestonSLAM
$ cd fast_lio_project/
$ source devel/setup.bash
$ roslaunch fast_lio mapping_mid360.launch
```