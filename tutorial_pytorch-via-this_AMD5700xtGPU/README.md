# Use the RX 5700 XT from PyTorch on macOS

[English](README.md) | [简体中文](README_CN.md)

This tutorial shows how to use an AMD Radeon RX 5700 XT from PyTorch through
the macOS MPS/Metal backend on this x86_64 AMD Hackintosh.

Open [the English Jupyter Notebook](install_pytorch_mps_rx5700xt.ipynb) for:

- separate `uv` and Conda installation instructions;
- a beginner-friendly explanation of MPS and `mps:0`;
- minimal GPU verification code;
- a short matrix-performance check;
- measured results from this machine;
- guidance for moving a model and its inputs to MPS.

## Tested environment

| Item | Tested configuration |
|---|---|
| CPU | AMD Ryzen 9 3900X |
| GPU | AMD Radeon RX 5700 XT 8 GB |
| Architecture | x86_64 |
| macOS | 15.2 Sequoia |
| Metal | Metal 3 |
| Python | 3.11 |
| PyTorch | 2.2.2 |
| NumPy | 1.26.4 |

PyTorch 2.2.x is the final release line that provides official prebuilt
packages for macOS x86_64, so the tutorial deliberately uses this older,
tested environment.

## Measured performance

| Test | Result |
|---|---:|
| Minimal MPS check | Passed on `mps:0` |
| Notebook short test | **6.36 TFLOP/s** |
| Five-minute average | **6.49 TFLOP/s** |
| GPU utilization during stress test | About 95%–100% |
| Maximum observed GPU die temperature | 97°C |

These numbers are reference results rather than required pass thresholds.
Cooling should be checked before running long training workloads.
