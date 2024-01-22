# Day4

# Session 1: Security Vulnerabilities in IC Supply Chain by Prof. Sukumar Nandi, IIT Guwahati
-> good inputs and good outputs
-> CIA: Confidentiality, Integrity and availability.
-> 1. Undefined inputs, Undefined states in FSM or Unwanted Optimization causes vulranability in system. Attacker can use the vulnability to hack the syste,m.
-> Cycle: Predict potential breaches and vulnerabilities, consider possible countermeasures or control, 
-> Methods of defence: Prevent attack, deter attack, Deflect attack, Detect attack, recover from attack.
design Vulnerabilities: Circuit modifications/Hardware Trojans: Adding additional hardware which is hidden in test mode.
        Map unused inputs/states to lead dead output/state
Design Vulnerability Prevention: Use trusted 3rd party IPS. Formal verification and testing. Obfuscation, Increase the time and effort required for reverse analysis.
Synthesis Vulnerability: Side channel leaks: Power at particular ports or pins. 
Synthesis Vulnerability Prevention: Logic locking/Camouflaging. Secure verification. Watermarking/Fingerprinting. 
Placement and routing Vulnerabilities: Side channel leakage. Hardware Trojans: Can add extra circuit at empty places. Invasive reverse engineering: Uderstand circuit functionality, De-layering. Glitching: Altering power supply or clock signals.
Placement and routing Vulnerabilities Preventions: Clock tree synthesis and optimization. Shielding. routing randomization and obfuscation. removed unused spaces. 
IC Mask Vulnerabilitis: errors. reverse engineering. hardware trojans. over production. 
IC Mask Vulnerabilitis Prevention: Split manufacturing. Utilizing specialized mask materils. obfuscation. 
PUFs: physically unclonable ...

# Session 2: Concept of SOC Design by A. Sahu, IIT Guwahati
SOC Components: Core, memory, 'Timer, DMA, PIC, UART, Peripheral controller': These are most important components in SOC, and driver writting skill. 
-> 

![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/1badae39-dac5-4252-bdad-37020d1b62ad)

-> OPENSOC

![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/fa8972bc-21d5-430f-8044-bed59915c947)

-> IO Control devices
![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/86437a7c-ca29-48b8-9e34-e52010a176aa)

8255: PPC programmable peripheral controller


