# Jetson SLAM

This project implements some popular SLAM projects on the Nvidia Jetson device, from source code compilation to real-device experiments. The project has been tested on the following software and hardware platforms. We will conduct experiments on more end-side devices in the future.

这个项目在 Nvidia Jetson 设备上实现了一些常用的 SLAM 工程，包含了从源码编译到真机实验。该项目在以下软硬件平台上通过了测试，未来我们会在更多端侧设备上展开实验。

|Device|JetPack|Operation System|ROS|
|--|--|--|--|
|Nvidia Jetson Orin DK 64GB|5.1.5|Ubuntu 20.04|Noetic|


----
# News

* 2025-08-14: Add Point-LIO project；
* 2025-08-14: Add Fast-LIVO2 project；
* 2025-08-14: Add Fast-LIO project；

---
# Note

Here are a few things you need to know before you start your project:

1. Since our main device is `Jetson Orin DK`, if you are also using this device and it is a brand new host, we recommend that you refer to [this blog](https://blog.csdn.net/nenchoumi3119/article/details/149779298?spm=1001.2014.3001.5502) post for flashing;
2. Because different projects require different dependencies, we put all the dependencies involved in the `third_party` folder and reference the contents of this folder during compilation.
3. To avoid a single `Readme` file being too large, separate Readme files are provided for different projects.
4. To avoid the entire repository from being too large, all projects only retain the file structure and the corresponding ReadMe file. You need to read the `ReadMe` file carefully to ensure correct compilation;
5. You should treat each project in this repository as an independent project, and the Readme file is the deployment guide for the corresponding project;
6. We provide Readme files in multiple languages for each sub-project;

在正式开始项目之前你需要知道以下几点：

1. 由于我们的主力设备是 `Jetson Orin DK`，如果你使用的也是这款设备，并且是一台全新的主机，那么建议参考我们所写的 [这篇博客](https://blog.csdn.net/nenchoumi3119/article/details/149779298?spm=1001.2014.3001.5502) 进行刷机；
2. 由于不同的项目工程需要不同的依赖，为此我们将涉及到的依赖统一放在 `third_party` 文件夹中，在编译时将引用这个文件夹中的内容；
3. 为了避免一篇 Readme 文件过大，在不同的工程中提供了各自的 Readme 文件；
4. 为了避免整个仓库体积过于庞大，所有项目都仅保留文件结构和对应的 ReadMe 文件，你需要认真阅读 `ReadMe` 文件以确保正确编译；
5. 你应该将这个仓库中每一个工程都当作是一个独立项目，Readme 文件是对应工程的部署指南；
6. 每一个子工程我们都提供了多个语言版本的 Readme 文件；


----


# Contributors

The hardware and testing facilities for this project were provided by the `Institute of Automation, Chinese Academy of Sciences`. The following individuals made significant contributions to the development of this project, and we would like to thank them for their efforts:

该工程由 `中国科学院自动化研究所` 提供硬件与测试场地，同时以下人员在该项目的开发中做出了巨大贡献，在此感谢他们的付出：

[WenJiang Xu 徐文江](https://github.com/HEA1OR)，[PengFei Yi 易鹏飞](https://github.com/alfie010)，[JingKai Xu 徐靖凯](https://github.com/Triumphant-strain)，[XingYu Wang 王行宇](https://github.com/xywang227)，[YaNan Hao 郝亚楠](https://github.com/haoyanan2024)，[YuWei Wang 王雨薇](https://github.com/YuweiWang2002)


----
# News & Future Work

* 2025-08-14: Init repo;

* Target: add ORB SLAM;
