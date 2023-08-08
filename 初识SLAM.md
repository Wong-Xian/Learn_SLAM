# 惯性测量单元 IMU

1. 加速度原理
    1. 线位移式
    2. 摆式
2. 角速度原理
    1. 激光陀螺仪
    2. MEMS微机电陀螺仪角速度
3. 磁力原理
    1. 霍尔效应
    2. 洛伦兹力

# IMU 原始数据采集

- 9轴IMU
  - 3轴加速度
  - 3轴角速度
  - 3轴磁力
- IMU 性能参数
  - 量程
  - 非线性度
  - 零点偏移
  - 轴间灵敏度
  - 噪声密度
  - 温度漂移

# 库介绍

## OpenCV

- 计算机视觉库

## Eigen

- 线性代数运算库

## Sophus

- 李群运算库

## ROS

- 机器人操作系统，一系列帮助构建机器人应用的库
- The Robot Operating System (ROS) is a set of software libraries and tools that help you build robot applications.

## Point Cloud

- 点云库，处理点云的库
- The Point Cloud Library (PCL) is a standalone, large scale, open project for 2D/3D image and point cloud processing.

# 入门 SLAM

2023年8月3日

- 安装 ROS

# 《视觉SLAM十四讲》

2.2 经典视觉SLAM框架

1. 传感器信息获取
2. 前端视觉里程计(Visual Odometry, VO)
   1. 相邻图象之间，相机的运动。
   2. 累积漂移(Accumulating Drift)：在最简单地估算两帧图像时产生的误差，随着估算的进行不断累积。
3. 后端（非线性）优化(Optimazation)
   1. 处理噪声问题。
4. 回环检测(Loop Closure Detection)
   1. 机器人回到了原点，但由于漂移，其位置估计值没有回到原点的现象。
   2. 需要后端具有“识别到过的场景”的能力。
5. 建图(Mapping)
   1. 【度量地图】
      1. 强调精确表示地图中物体的位置关系。
      2. 稀疏(Sparse)地图（定位用）选取部分具有代表性的东西(路标Landmark)
      3. 稠密地图（导航用）着重于建模所有看到的东西
   2. 【拓扑地图】
      1. 强调地图中元素之间的关系

2.4 实践：编程基础

2.4.3 使用cmake

- cmake 生成 makefile，再用 make 命令编译程序。
- add_library() 命令可以添加库
- Linux 中库分为
  - 静态库 后缀为.a 静态库每次被调用都会生成一个副本
  - 共享库 后缀为.so 共享库则只有一个副本
- target_link_libraries(*1 *2) 函数使 *1 文件可以调用 *2 库中的函数。

2.4.5 使用 IDE

推荐 kdevelop 软件。

# 概念辨析

- 单目相机(Monocular)
- 双目相机(Stereo)
- 深度相机(RGB-D)
- 视差(Disparity)：相机移动时，离相机距离近的物体移动块，离相机远的物体移动慢。
- 尺度(Scale)：单目 SLAM 估计的轨迹和地图 与 真实轨迹和地图 相差一个因子。
- 尺度不确定性(Scale Ambiguity)：单目 SLAM 无法仅凭图象确定真实尺度。
- 基线(Baseline)：双目相机两个相机之间的距离。

# B站 古月居 SLAM 视频

## ROS 中结点间的通信机制
- ROS 中的结点：就是进程
- 结点间的通信机制
  - 发布订阅模式：一个结点发布，可以有多个结点订阅，非实时。
  - 服务器客户端模式：客户端发送请求，服务器立即返回应答，实时。