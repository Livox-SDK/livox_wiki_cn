=======================================
Livox 雷达标定
=======================================

在多传感器智能体导航中，通常会安装多个传感器用以数据的融合与计算。在移动建图和环境感知中，通常需要布置多个Lidar以确保较大的FOV，
为更稳健的姿态估计算法和丰富环境细节提供稳定的数据源。然而无论是哪种传感器：相机、激光雷达、毫米波雷达都有自己的坐标系，也就是
所有的传感器产生的数据都是基于传感器自身的坐标系的。为了方便算法研究和测试，需要将各自传感器获得的数据转换到同一个坐标系下，这既是传感器的外参标定。

Lidar-Lidar外参标定
------------------------------------------



手动标定
~~~~~~~~~~~~~~~~~~~~~~

Livox_Viewer软件中集成了手动标定雷达外参功能，可方便准确的标定多部FOV存在重叠的Livox LiDAR，详情可查看：
`外参标定与点云显示  <https://github.com/Livox-SDK/Livox-SDK/wiki/Calibrate-extrinsic-and-display-under-ros-cn>`_

自动标定
~~~~~~~~~~~~~~~~~~~~~~

Livox提供基于c++的工具实现多雷达之间的标定外参自动计算，详情可参考:
`Livox calibration <https://github.com/Livox-SDK/Livox_automatic_calibration/blob/master/doc/readme-CN.md>`_



Lidar-Camera外参标定
------------------------------------------

Livox提供了一个手动校准Livox雷达和相机之间外参的方法，并在Mid-40，Horizon和Tele-15上进行了验证。其中包含了计算相机内参，获得标定数据，优化计算外参和雷达相机融合应用相关的代码。本方案中使用了标定板角点作为标定目标物，由于Livox雷达非重复性扫描的特点，点云的密度较大，比较易于找到雷达点云中角点的准确位置。相机雷达的标定和融合也可以得到不错的结果。详情可参考:
`Camera-LiDAR-Calibration Manual <https://github.com/Livox-SDK/livox_camera_lidar_calibration/blob/master/README.md>`_

关于多传感器融合扫描方案，可参考Livox开源算法 `livox high precision mapping <https://github.com/Livox-SDK/livox_high_precision_mapping>`_ ，该方案详细展示了如何对Mid-40激光雷达和apx-15惯导模块进行同步和标定，并使用该组件进行实时高精度建图。
