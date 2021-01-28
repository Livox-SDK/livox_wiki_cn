========================================
数据集
========================================

仿真数据集Livox Simu-dataset v1.0    `EN <https://livox-wiki-en.readthedocs.io/en/latest/data_summary/dataset.html>`_
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**简介:**

Livox仿真数据集是基于自动驾驶仿真测试平台生成的点云数据和对应标注，支持3D目标检测和语义分割任务。其中传感器配置了5个浩界Horizon激光雷达和1个泰览Tele-15超远距激光雷达，整个数据集包含了14445帧360°Lidar点云数据，6种目标的3D包围框标注和14种类别的点云语义标注。本次开放下载的数据集场景主要为市区宽阔道路场景，包括双向12车道和双向8车道。相应地，该仿真场景中也包含了多种车辆和行人模型，以及更贴近真实场景的交通流模拟。此外，丰富的红绿灯、交通标识牌、隔离物（包括隔离栏杆、绿化带、隔离墩等）、树木建筑等都让整个仿真场景更加贴近实际驾驶路况。

**仿真场景示例:**

.. image:: ../image/simulation_dataset_1.png

**标注示例:**

.. image:: ../image/simulation_dataset_2.png

**数据格式及下载链接:**

*在下载数据集之前，请仔细阅读这些条款。下载或使用数据集即表示您接受这些条款:*
`GNU General Public License v3.0 <https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/update/LICENSE.txt>`_

`数据集说明文档 <https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Avia/readme_CN.md>`_

`数据集 <https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/dataset/simu_data.zip>`_

`数据集Rosbag <https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/dataset/simu_data_rosbag.zip>`_

**目标检测案例:**

`Livox_detection_simu <https://github.com/Livox-SDK/livox_detection_simu>`_
