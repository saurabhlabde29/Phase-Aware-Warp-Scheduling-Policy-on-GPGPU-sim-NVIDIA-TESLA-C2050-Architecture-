# Phase-Aware-Warp-Scheduling-Policy-on-GPGPU-sim-NVIDIA-TESLA-2050C-Architecture-

Language: C++

Platforms: GPGPU-simulator

Note: Use GPGPU simulator which can be found on github

• Extended GPGPU-sim to include the Phase Aware Warp Scheduling policy which performs closer to the best of GTO and RR policies by leveraging phase information embedded in the PTX Assembly at compile time.

• Benchmarked with CUDA SDK, Rodnia and Parboil kernels and achieved an 8 % improvement in the IPC.

STEPS TO RUN THE CODE:

STEP - I Replace the gpgpu sim files with our modified files

1) Copy abstract_hardware_model.h into the directory ../src
2) Copy ptx_ir.h into the directory ../src/cuda-sim/
3) Copy shader.cc into the directory ../src/gpgpu-sim
4) Copy shader.h into the directory ../src/gpgpu-sim

STEP - II Modify the config file
1) Use the gpgpusim.config file of TESLAC2050 model
2) Set -gpgpu_ptx_convert_to_ptxplus 1. It is usually set to 0 initially. It is important   
   to enable this conversion as we use ptx plus for our calculations.
3) Set -gpgpu_ptx_save_converted_ptxplus 1. Doing this is optional and allows to save the       
   converted ptx plus assembly code.
4) To run the paws scheduler, add the line '-gpgpu_scheduler paws'. Make sure all the 
   other scheduler options are commented out at this moment.
5) To run the two level scheduler with paws scheduling policy, replace the line of two 
   level scheduler option with '-gpgpu_scheduler two_level_active:6:0:7'
   To run two level scheduler with got policy , replace the two level configuration line    
   with '-gpgpu_scheduler two_level_active:6:0:2'

STEP -III Build the simulator
1) Navigate the the gpgpu-sim_distribution directory and type bash followed by make.

STEP -IV Running the kernel
1) Copy the edited gpgpusim.config file and config_fermi_islip.icnt file from TESLAC2050 to the directory of the kernel to be executed.
2) Type make and then run the executable.
 


NOTE : To obtain the same results as us, use the default configuration of TESLAC2050 or set the configuration as specified in the report or use the config file provided in the folder.
