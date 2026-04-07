# Anti-UAV Dataset & YOLOv8l Model for Drone Detection

> **Language** · [中文](#中文) | [English](#english)

---

<h2 id="english">🇬🇧 English</h2>

## Introduction

This repository provides the **Anti-UAV dataset** and **YOLOv8l model weights** trained on it. The dataset focuses on two common types of loitering munition / drones:

- **`copter_drone`** – multi‑rotor (e.g., quadcopter), typically slower
- **`motor_drone`** – fixed‑wing / motor‑driven (e.g., Shahed‑136), typically faster

The model achieves **98.05% mAP@0.5** on the validation set, making it suitable for anti‑drone visual detection tasks.

## 1. Dataset Overview

| Property                 | Description                                                              |
| ------------------------ | ------------------------------------------------------------------------ |
| **Name**                 | Anti-UAV                                                                 |
| **Classes**              | `copter_drone`, `motor_drone`                                            |
| **Total Images**         | 73,751                                                                   |
| **Split**                | Train : Val = 8 : 2 (≈59k / ≈14.8k)                                      |
| **Annotation Format**    | YOLO format (`    `)                                |
| **Scenario**             | Complex backgrounds (urban, suburban, sky), varying illumination/weather |

> Images have diverse resolutions. Training used YOLOv8’s default 640×640 input.

## 2. Training Details

| Item               | Value                         |
| ------------------ | ----------------------------- |
| Base Model         | YOLOv8l (large)               |
| Epochs             | 24 (can be fine‑tuned)        |
| Optimizer          | SGD                           |
| Hardware           | Dual A100 GPU                 |

## 3. Model Performance (Validation Set)

| Metric               | Value    |
| -------------------- | -------- |
| Precision            | 0.9808   |
| Recall               | 0.9621   |
| mAP@0.5              | 0.9805   |
| mAP@0.5:0.95         | 0.8205   |


## 4. Download Links

| Item                                      | Link                                                                  |
| ----------------------------------------- | --------------------------------------------------------------------- |
| **YOLOv8l weights** (`best.pt`)           | [Google Drive](https://drive.google.com/file/d/1Q3Ge8UFjanGjhtFioC3iNX0LH3DmYMvA/view?usp=drive_link)                   |
| **Anti-UAV dataset** (73,751 images + labels) | [Google Drive](https://drive.google.com/file/d/1eJsAAB1Nj1KD6nEZnAKxLXz5bqSxOqpG/view?usp=drive_link)                   |

> Please replace the above links with your actual Google Drive shared URLs.

## 5. Quick Start – Inference

```python
from ultralytics import YOLO

# Load trained weights
model = YOLO('path/to/anti-uav-best.pt')

# Inference on a single image
results = model('path/to/drone_image.jpg', conf=0.5)
results[0].show()

# Batch prediction
model.predict('data/images', save=True, conf=0.5)
```

<h2 id="中文">🇨🇳 中文</h2>

## 介绍

本仓库提供 **Anti-UAV 数据集** 以及在此数据集上训练的 ​**YOLOv8l 模型权重**​。数据集专注于两种常见类型的自杀式无人机：

* **`copter_drone`（多旋翼无人机）** – 以四旋翼为例，通常速度较慢
* **`motor_drone`（固定翼/电机驱动无人机）** – 以 Shahed-136 为例，通常速度较快

模型在验证集上取得了 ​**98.05% 的 mAP@0.5**​，可用于反无人机视觉检测任务。

## 1. 数据集概述

| 属性               | 说明                                                           |
| -------------------- | ---------------------------------------------------------------- |
| **名称**     | Anti-UAV                                                       |
| **目标类别** | `copter_drone`，`motor_drone`                          |
| **图像总数** | 73,751 张                                                      |
| **划分比例** | 训练集 : 验证集 = 8 : 2（约 5.9 万 / 1.48 万）                 |
| **标注格式** | YOLO 格式（`<类别>   <宽> <高>`）                  |
| **应用场景** | 复杂背景（城市、郊区、天空）、不同光照和天气条件下的无人机检测 |

> 图像分辨率多样，训练时统一使用 YOLOv8 默认的 640×640 输入。

## 2. 模型训练详情

| 项目     | 内容                |
| ---------- | --------------------- |
| 基础模型 | YOLOv8l (large)     |
| 训练轮数 | 24 轮（可继续微调） |
| 优化器   | SGD                 |
| 训练硬件 | 双卡 A100 GPU       |

## 3. 模型性能评估（验证集）

| 指标              | 数值   |
| ------------------- | -------- |
| 精度（Precision） | 0.9808 |
| 召回率（Recall）  | 0.9621 |
| mAP@0.5           | 0.9805 |
| mAP@0.5:0.95      | 0.8205 |

模型对两类无人机均表现出极高的检测精度，误检和漏检率低，适合部署在实时反无人机系统中。

## 4. 下载链接

| 内容                                                  | 下载链接                                         |
| ------------------------------------------------------- | -------------------------------------------------- |
| **YOLOv8l 模型权重**(`best.pt`)             | [Google Drive](https://drive.google.com/file/d/1Q3Ge8UFjanGjhtFioC3iNX0LH3DmYMvA/view?usp=drive_link) |
| ​**Anti-UAV 数据集**​（73,751 张图片 + 标签） | [Google Drive](https://drive.google.com/file/d/1eJsAAB1Nj1KD6nEZnAKxLXz5bqSxOqpG/view?usp=drive_link) |

## 5. 快速开始 – 模型推理

python
```

from ultralytics import YOLO

# 加载训练好的权重

model = YOLO('path/to/anti-uav-best.pt')

# 单张图像预测

results = model('path/to/drone_image.jpg', conf=0.5)
results[0].show()

# 批量'''''预测并保存

model.predict('data/images', save=True, conf=0.5)

```
---

*For academic use only. Please cite if you use this dataset or model.*
*仅限学术研究使用。*
```


