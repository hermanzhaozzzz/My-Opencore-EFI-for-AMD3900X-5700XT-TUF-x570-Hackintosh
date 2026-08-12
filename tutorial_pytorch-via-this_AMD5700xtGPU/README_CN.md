# 在 macOS 上用 PyTorch 调用 RX 5700 XT

[English](README.md) | **简体中文**

可以用，而且调用的就是 RX 5700 XT。

在这台 Ryzen 9 3900X 黑苹果上，PyTorch 通过 macOS 的 MPS/Metal 后端使用
RX 5700 XT。验证成功时，PyTorch 会把它显示为 `mps:0`；这台电脑没有核显，
因此不会混淆到其他 GPU。

如果你只想尽快跑起来，直接打开
[中文 Jupyter Notebook](install_pytorch_mps_rx5700xt_CN.ipynb)，选择 `uv` 或
Conda 其中一种安装方式，然后依次运行环境检查、最小验证和性能短测。

## 本机实测结果

| 项目 | 结果 |
|---|---:|
| MPS 设备 | `mps:0`，验证通过 |
| 短时矩阵测试 | **6.36 TFLOP/s** |
| 五分钟压力测试平均性能 | **6.49 TFLOP/s** |
| 压力测试 GPU 占用 | 约 95%–100% |
| 最高 GPU Die 温度 | 97°C |

压力测试期间显卡能够持续满载，说明 MPS 加速和 RX 5700 XT 工作正常。分数会受到
后台负载、显卡频率和散热影响，不必与这里完全一致。97°C 已经偏高，长时间训练前
建议先检查散热。

## 已验证环境

| 项目 | 配置 |
|---|---|
| CPU / GPU | Ryzen 9 3900X / Radeon RX 5700 XT 8 GB |
| macOS | Sequoia 15.2，x86_64，Metal 3 |
| Python | 3.11 |
| PyTorch | 2.2.2 |
| NumPy | 1.26.4 |

这里固定使用 PyTorch 2.2.2，是因为 PyTorch 2.2.x 是最后一代提供官方 macOS
x86_64 安装包的版本。Apple Silicon 上的新版本 PyTorch 不适用于这台 Intel
架构的黑苹果。

## Notebook 包含什么

- `uv` 和 Conda 两种互不混用的安装方式；
- 一段可以复制到其他项目的最小 MPS 验证代码；
- 一个几秒钟即可完成的 RX 5700 XT 性能短测；
- 在自己的模型中把模型和数据移动到 MPS 的示例；
- 显存不足、算子不支持和 CPU fallback 等常见问题说明。

正常使用直接启动 JupyterLab 即可。`env -u PYTORCH_ENABLE_MPS_FALLBACK`
不是 MPS 的安装要求，只在严格验证时使用：它会临时关闭 CPU fallback，避免
不受支持的算子悄悄转到 CPU 执行。

CUDA 和 ROCm 都不需要安装。在 macOS 中，PyTorch 使用 MPS/Metal 调用这张
AMD 显卡。
