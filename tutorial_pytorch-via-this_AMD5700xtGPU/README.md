# Use the RX 5700 XT from PyTorch on macOS

**English** | [简体中文](README_CN.md)

Yes, it works—and PyTorch is using the RX 5700 XT.

On this Ryzen 9 3900X Hackintosh, PyTorch accesses the RX 5700 XT through the
macOS MPS/Metal backend. A successful check reports the device as `mps:0`.
Because this computer has no integrated GPU, there is no second GPU to confuse
with that result.

For the quickest start, open the
[English Jupyter Notebook](install_pytorch_mps_rx5700xt.ipynb), choose either
the `uv` or Conda installation method, and run the environment check, minimal
verification and short benchmark in order.

## Results from this machine

| Test | Result |
|---|---:|
| MPS device | Passed on `mps:0` |
| Short matrix test | **6.36 TFLOP/s** |
| Five-minute average | **6.49 TFLOP/s** |
| GPU utilization during the stress test | About 95%–100% |
| Maximum GPU die temperature | 97°C |

The GPU remained fully loaded during the stress test, confirming that MPS
acceleration and the RX 5700 XT were working correctly. Your result will vary
with background load, GPU clocks and cooling. It does not need to match these
numbers exactly. A 97°C die temperature is high, so check cooling before long
training runs.

## Tested environment

| Item | Configuration |
|---|---|
| CPU / GPU | Ryzen 9 3900X / Radeon RX 5700 XT 8 GB |
| macOS | Sequoia 15.2, x86_64, Metal 3 |
| Python | 3.11 |
| PyTorch | 2.2.2 |
| NumPy | 1.26.4 |

This tutorial pins PyTorch 2.2.2 because the 2.2.x line was the last to provide
official macOS x86_64 packages. Current Apple Silicon builds are not a
replacement for the Intel-architecture package required by this Hackintosh.

## What the notebook includes

- separate `uv` and Conda installation methods;
- a minimal MPS check that can be copied into another project;
- a short RX 5700 XT benchmark that finishes in a few seconds;
- an example of moving a model and its inputs to MPS;
- practical notes on memory limits, unsupported operations and CPU fallback.

Start JupyterLab normally; use `env -u PYTORCH_ENABLE_MPS_FALLBACK` only for
strict GPU verification, where CPU fallback must be disabled.

CUDA and ROCm are not required. On macOS, PyTorch uses MPS/Metal to access this
AMD GPU.
