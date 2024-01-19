# Its about Day 3

# Session 1: AJIT Processor by Prof. Madhav Desai, IIT Bombay
-> AJIT processor started 2016-17: Single core single thread, silicon validated with NAVIC SOC. Quad-core 8-thread configuration validated on FPGA. 

-> Uses SPARC V8 ISA (load/store architecture) has 2 different features: 
1. Windows of registers, instead of fixed set of registers.
2. Delayed control tracer, predicting next to next instruction to avoid waiting for instrction decoder at the branch condition.

-> Supports linux, working on 256 core processor. Has opensource tool chain 'https://github.com/adhuliya/ajit-toolchain'.

-> Planning to opensource few configurations.

# Session 2: Expert Lecture by Prof. Anand Balusu, IIT Roorkee
Title: 'A Reliable and Robus Framework for accurate timing sign-off of Digital ICs'
1. Variabilioty issues:
     a. Spacial variation: Impact of stress variability: channel stress with number of fingers.
     b. Temporal variability: when apply -ve vgs, generates traps at si-sio2 interface. Hot carrier injection mechanism: at saturation stage, electron can enter into gate-oxide region. These two are againg effects.

   Solution: considering variations and making variation aware timing models. Derive model co-efficients as a function of device level parameter variations.
