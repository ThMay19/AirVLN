# 🚁 **AerialVLN: 基于视觉和语言导航的无人机项目**

[![GitHub stars](https://img.shields.io/github/stars/AirVLN/AirVLN?style=social)](https://github.com/AirVLN/AirVLN) 
[![License](https://img.shields.io/github/license/AirVLN/AirVLN)](LICENSE) 
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)](https://github.com/AirVLN/AirVLN/actions)

---

## 📖 **目录**
1. [简介](#简介)
2. [项目特色](#项目特色)
3. [快速开始](#快速开始)
4. [模拟器与数据集](#模拟器与数据集)
5. [使用示例](#使用示例)
6. [引用](#引用)
7. [联系方式](#联系方式)

You may refer to the [English version of this page](https://github.com/AirVLN/AirVLN/blob/main/README.md).


---

## 🌟 **简介**

**摘要：**
Recently emerged Vision-and-Language Navigation (VLN) tasks have drawn significant attention in both computer vision and natural language processing communities. Existing VLN tasks are built for agents that navigate on the ground, either indoors or outdoors. However, many tasks require intelligent agents to carry out in the sky, such as UAV-based goods delivery, traffic/security patrol, and scenery tour, to name a few. Navigating in the sky is more complicated than on the ground because agents need to consider the flying height and more complex spatial relationship reasoning. To fill this gap and facilitate research in this field, we propose a new task named AerialVLN, which is UAV-based and towards outdoor environments. We develop a 3D simulator rendered by near-realistic pictures of 25 city-level scenarios. Our simulator supports continuous navigation, environment extension and configuration. We also proposed an extended baseline model based on the widely-used cross-modal-alignment (CMA) navigation methods. We find that there is still a significant gap between the baseline model and human performance, which suggests AerialVLN is a new challenging task.

近年来，视觉与语言导航（Vision-and-Language Navigation，简称 VLN）任务在计算机视觉和自然语言处理领域引起了广泛关注。然而，现有的 VLN 任务主要面向地面导航代理，无论是在室内还是室外。然而，许多实际任务需要智能代理在空中执行操作，例如基于无人机（UAV）的货物配送、交通/安全巡逻以及风景巡游等。相比地面导航，空中导航更加复杂，因为代理需要考虑飞行高度以及更复杂的空间关系推理。为填补这一空白并促进该领域的研究，我们提出了一项新任务，名为 AerialVLN，专注于基于无人机的户外导航。我们开发了一个3D模拟器，该模拟器使用接近真实的图像渲染了 25 个城市级场景。我们的模拟器支持连续导航、环境扩展和配置功能。此外，我们基于广泛使用的CMA方法，提出了一个扩展的基线模型。研究表明，基线模型与人类性能之间仍存在显著差距，这表明 AerialVLN 是一项具有挑战性的全新任务。

---

## 🚀 **项目特色**

- **真实感3D模拟器**：提供 25 个城市级场景，图像逼真。
- **跨模态对齐模型**：通过视觉和语言信息实现高级导航。
- **可扩展框架**：支持添加新的环境和配置。
- **综合数据集**：包括 AerialVLN 和 AerialVLN-S，用于模型训练和评估。

![Instruction: Take off, fly through the tower of cable bridge and down to the end of the road. Turn left, fly over the five-floor building with a yellow shop sign and down to the intersection on the left. Head to the park and turn right, fly along the edge of the park. March forward, at the intersection turn right, and finally land in front of the building with a red billboard on its rooftop.](./files/instruction_graph.jpg)
Instruction: Take off, fly through the tower of cable bridge and down to the end of the road. Turn left, fly over the five-floor building with a yellow shop sign and down to the intersection on the left. Head to the park and turn right, fly along the edge of the park. March forward, at the intersection turn right, and finally land in front of the building with a red billboard on its rooftop.

---

## 🛠️ **快速开始**

### 前置条件
- Python 3.8+
- Conda
- CUDA Device(s)

### 安装步骤
```bash
# 克隆代码仓库
git clone https://github.com/AirVLN/AirVLN.git
cd AirVLN

# 创建并激活虚拟环境
conda create -n AerialVLN python=3.8
conda activate AerialVLN

# 安装依赖
pip install -r requirements.txt
```

最终，项目目录结构如下所示：

```bash
- 项目目录
    - [AirVLN](https://www.kaggle.com/datasets/shuboliu/aerialvln-simulators) # 本代码库
    - DATA
        - data
            - aerialvln # 数据集（可为AerialVLN-S)
    - ENVs
      - env_1 # 模拟器1
      - env_2 # 模拟器2
      - ...
```

## 📦 **模拟器与数据集**
### 模拟器下载

AerialVLN 模拟器（约 35GB） 可通过 Kaggle 网站 下载，也可使用以下 cURL 命令：
```bash
#!/bin/bash
curl -L -o ~/Downloads/aerialvln-simulators.zip\
  https://www.kaggle.com/api/v1/datasets/download/shuboliu/aerialvln-simulators
```

您还可以通过 kagglehub 下载，并将其放置到 AerialVLN 项目目录下：
```bash
import kagglehub

# 下载最新版本
path = kagglehub.dataset_download("shuboliu/aerialvln")

print("数据集文件路径:", path)
```


### 数据集下载

AerialVLN 和 AerialVLN-S 注释数据集（均小于 100MB） 可通过以下方法获取：

- AerialVLN 数据集: [https://www.kaggle.com/datasets/shuboliu/aerialvln](https://www.kaggle.com/datasets/shuboliu/aerialvln)
- AerialVLN-S 数据集: [https://www.kaggle.com/datasets/shuboliu/aerialvln-s](https://www.kaggle.com/datasets/shuboliu/aerialvln-s)

或者使用以下命令下载：
```bash
#!/bin/bash
curl -L -o ~/Downloads/aerialvln.zip\
  https://www.kaggle.com/api/v1/datasets/download/shuboliu/aerialvln
```
以及
```bash
#!/bin/bash
curl -L -o ~/Downloads/aerialvln.zip\
  https://www.kaggle.com/api/v1/datasets/download/shuboliu/aerialvln-s
```

## 🔧 **使用示例**

导航脚本示例，请参考 [scripts 文件夹](https://github.com/AirVLN/AirVLN/tree/main/scripts)下的文件。

## 📜 **引用**

如果您在研究中使用了 AerialVLN，请引用以下文献：

```
@inproceedings{liu_2023_AerialVLN,
  title={AerialVLN: Vision-and-language Navigation for UAVs},
  author={Shubo Liu and Hongsheng Zhang and Yuankai Qi and Peng Wang and Yanning Zhang and Qi Wu},
  booktitle={International Conference on Computer Vision (ICCV)},
  year={2023}
}
```

此外，我们注意到有些学者希望将AerialVLN数据集及其仿真器应用于除VLN以外的其他研究领域，我们欢迎这样的做法！我们同样欢迎您与我们联络告知[我们](mailto:shubo.liu@mail.nwpu.edu.cn)您的拟应用领域。

## ✉️ **Contact**
如果您有任何问题，请联络： [Shubo LIU](mailto:shubo.liu@mail.nwpu.edu.cn)
