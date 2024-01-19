# Its about Day 3

# Session 1
## AJIT Processor by Prof. Madhav Desai, IIT Bombay
AJIT processor started 2016-17: Single core single thread, silicon validated with NAVIC SOC. Quad-core 8-thread configuration validated on FPGA. uses SPARC V8 ISA (load/store architecture) has 2 different features. 
1. Windows of registers, instead of fixed set of registers.
2. Delayed control tracer, predicting next to next instruction to avoid waiting for instrction decoder at the branch condition.

supports linux, working on 256 core processor. Has opensource tool chain github/adhuliya/ajit-toolchain (hare 'https://github.com/adhuliya/ajit-toolchain')
AHIR-V2 tools: used in AJIT, NAVIC, AI/ML 

