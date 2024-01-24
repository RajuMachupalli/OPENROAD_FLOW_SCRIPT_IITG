# Day 6: The last day of workshop

# Session 1: Hardware Accelerator Design from C/C++ with Open Source High-level Synthesis by Prof. Chandan Karfa, IIT Guwahati
-> Importance of hardware accelerators: Moore's law no more applicable. Multicore processors are used to improve performance. But the performance is not linear with the multicore.
-> Next is to specialize the hardware for specific application. Modern SoCs have rich set of specialized accelerators.
-> How to design hardware accelerator? general methos is to write HDL code but time consume. High-level synthesis can speedup the design time at the cost of possible extra hardware.
-> NPTEL course for high level design ('https://nptel.ac.in/courses/106103229')
Step 1: Preprocessing: Control and dataflow graph. Identify data dependency graph. 
step 2: Scheduling: identify how many clocks needed to operate (scheduling in parallel). Scheduling Techniques:
step 3: Register allocation and binding: Allocate the registers based on life time of variables.
Step 4: Functional unit allocation and binding
Step 5: Register transfer level behavior: Express everything interms of registers.
Step 6: Datapath synthesis and generation.
Step 7: Control signals

HLS Tools: Calypto is for ASIC design. (XLS, https://google.github.io/xls/) is open source HLS from google. Vivado HLS for Xilinx FPGAs.

HLS Demo: 
