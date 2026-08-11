# 在 macOS 上通过 PyTorch 使用 RX 5700 XT

[English](README.md) | [简体中文](README_CN.md)

这篇教程介绍如何在 x86_64 AMD 黑苹果中，通过 macOS 的 MPS/Metal 后端，
让 PyTorch 使用 AMD Radeon RX 5700 XT。

打开[中文 Jupyter Notebook](install_pytorch_mps_rx5700xt_CN.ipynb)，可以查看：

- 相互独立的 `uv` 和 Conda 安装方法；
- 面向初学者的 MPS 与 `mps:0` 说明；
- 最小 GPU 验证代码；
- 简短的矩阵性能测试；
- 这台电脑的实测成绩；
- 把模型及输入数据放到 MPS 的方法。

## 已验证环境

| 项目 | 测试配置 |
|---|---|
| CPU | AMD Ryzen 9 3900X |
| GPU | AMD Radeon RX 5700 XT 8 GB |
| 系统架构 | x86_64 |
| macOS | 15.2 Sequoia |
| Metal | Metal 3 |
| Python | 3.11 |
| PyTorch | 2.2.2 |
| NumPy | 1.26.4 |

PyTorch 2.2.x 是最后一代提供官方 macOS x86_64 安装包的版本，因此教程有意
使用这套较旧但已经完成验证的环境。

## 本机实测性能

| 测试 | 结果 |
|---|---:|
| 最小 MPS 验证 | 通过，设备为 `mps:0` |
| Notebook 短测 | **6.36 TFLOP/s** |
| 五分钟压力测试平均性能 | **6.49 TFLOP/s** |
| 压力测试 GPU 占用 | 约 95%–100% |
| 观察到的最高 GPU Die 温度 | 97°C |

这些数字用于参考，并不是安装成功必须达到的分数。长时间训练前应先检查散热。
