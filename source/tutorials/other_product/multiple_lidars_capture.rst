===========================================================================
多雷达数据采集（使用览沃枢纽 Livox Hub）
===========================================================================

连接及配置
--------------------------

以一台Livox Mid-40和一台Livox Horizon为例：

**软件部分**：ubuntu 16.04、ROS、Livox-SDK、Livox ROS driver（此部分驱动的下载和安装详细过程见 :doc:`驱动 <../../data_summary>`）

**硬件部分**：Livox Mid-40 × 1、Livox Horizon × 1、Livox Hub × 1、千兆网线 × 1、Livox Hub电源线 × 1、Livox雷达电池 × 1、PC × 1。

**时间戳同步**：关于多部livox LiDAR之间的时间戳同步，可参考： :ref:`Livox时间戳同步`

**连线和IP配置**：Livox Hub通过以太网进行数据通信，采用UDP通信协议，支持两种IP地址配置：静态IP地址和动态IP地址，出厂时默认采用动态主机配置协议（DHCP）分配IP地址。根据IP地址设置形式不同，其物理连接方式也稍有差别。

-  采用静态IP地址进行连接时，其物理连接如下图所示：

.. image:: ../../image/static_ip.png

-  采用动态IP地址进行连接时，其物理连接如下图所示：

.. image:: ../../image/dynamic_ip.png

Livox Hub出厂时默认采用动态主机配置协议（DHCP）分配IP地址，若希望使用静态IP进行连接，需连接路由器进行设置，步骤如下：

1.按照上图动态IP地址连接方式，通过路由器连接Livox Hub、Livox
Lidar、PC和电源。

2.在电脑上运行Livox Viewer，点击打开设备管理器。选择Livox
Hub，点击打开设备属性页面。在设备属性页面中将Livox
Hub的IP地址设置为静态IP地址。注意Livox
Hub的静态IP地址应设置为192.168.1.X（其中，X为2~233之间的任意数字）。

3.设置完毕后，断开Livox Hub的所有连接。

4.若Livox
Hub为静态IP模式，则电脑也应设置为静态IP模式（若电脑采用动态IP模式，可能导致无法读取到Livox
Hub）。电脑的静态IP地址应设置为192.168.1.X（其中，X为2~233之间的任意数字），并且不可与连接的Livox
Hub的IP地址相同。

若对Hub的连线及IP配置存在疑问，可参考Livox官网“Livox Hub用户手册
v1.2”的“连接”部分，下载地址如下 `Livox Hub用户手册v1.2 <https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Livox%20%E6%9E%A2%E7%BA%BD%E7%94%A8%E6%88%B7%E6%89%8B%E5%86%8C.pdf>`_

本示例使用静态IP配置，如下图所示：
.. image:: ../../image/static_IP_config.rst

Livox Hub上最多可同时接入9个Livox Lidar，本示例连接了一台Livox
Horizon和一台Livox
Mid-40，若希望进行更多台Lidar同时采集，可直接进行连接。

使用ROS进行数据采集
------------------------------------------

连接成功后，在本地的ws\_livox路径下编译：

::
   
   catkin_make

更新当前ROS包环境：

::

   source ./devel/setup.bash``

使用ROS launch文件加载LIvox ros driver

::
   
   roslaunch livox_ros_driver livox_hub_rviz.launch``

览沃驱动程序中所有的 launch 文件都位于
"ws\_livox/src/livox\_ros\_driver/launch" 路径下，不同的 launch
文件拥有不同的配置参数值，可根据不同的使用场景，启动不同的launch文件（详细launch配置文件描述可见 `Livox ROS Driver_github <https://github.com/Livox-SDK/livox_ros_driver/blob/master/README_CN.md>`_
4.1 launch配置文件描述部分）

这里选用的livox\_hub\_rviz.launch将自动连接Livox
Hub设备、向外发布pointcloud2格式的点云数据并自动加载rviz显示实时点云数据，如下图所示：

.. image:: ../../image/ros_hub_scanning.png

红色部分点云为Livox Horizon扫描到的图像，紫色部分为Livox
Mid-40扫描到的图像

livox hub当前已停产，多雷达数据采集可通过ros driver实现，启动livox lidar launch文件，默认配置可连接网段内全部雷达，如果只需要连接其中一两个，具体参考ros驱动的config配置。

使用Livox Viewer采集数据
------------------------------------------

连接成功后，在Livox Viewer文件夹内打开终端，运行下列命令打开Livox
Viewer程序：

::
   
   ./livox_viewer.sh

.. |Viewer设备资源管理器| image:: ../../image/devices_manager.png


点击 |Viewer设备资源管理器| 打开设备管理器，选择Livox Hub，第一次连接时可能会显示Livox
Hub的IP地址与PC的IP地址不匹配。若已经按照上面步骤将Livox
Hub和PC进行了静态IP的配置，可点击工具栏Network Adapter—refresh
Adapter刷新配置。

打开Hub按钮并点击播放，即可显示多雷达实时扫描数据，如下图所示：

.. image:: ../../image/two_lidar_scanning.png


黄色部分点云为Livox Horizon扫描的数据，蓝色部分点云为Livox
Mid-40扫描到的数据。

与单雷达数据录制类似，可点击工具栏上的录制按钮进行lvx格式文件的录制，暂停播放或再次点击此按钮结束录制。