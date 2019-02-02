# Phase-Aware-Warp-Scheduling-Policy-on-GPGPU-sim-NVIDIA-TESLA-C2050-Architecture-

Language: C++

Platforms: GPGPU-simulator

• Extended GPGPU-sim to include the Phase Aware Warp Scheduling policy which performs closer to the best of GTO and RR policies by leveraging phase information embedded in the PTX Assembly at compile time.

• Benchmarked with CUDA SDK, Rodnia and Parboil kernels and achieved an 8 % improvement in the IPC.
