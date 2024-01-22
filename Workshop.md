# This is contains workshop flow



# Day3: Friday Januray 19 2024
## Synthesis flow
1. Design files
      a. RTL code (.v)
       b. Constraint files (.sdc)
3. Technology files:
     a. .lib file: contains cells information, like power, capacitance, delay at different pins levels. logical information.
     b. .lef file: contains physical information of cells. size, pin name, pin location


   technology file: layer name, type and direction of metal, pitch, 
   .def file: cell info, pin
   two types of contraints: optimization constrains and design constraints

   synthesis output: netlist (.v), .sdc


step 1:
![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/7b22f945-a15e-4446-852b-c3b67ac3cf10)

proc: converts all operations to rtl
opt: optimization
fsm: FSM converts
memory: converts RTL
techmap: maps to technology
dfflibmap -liberty mycells.lib 
abc: mapping logic to mycells.lib
clean
write_verilog synth.v: write the gatelevel netlist





## Floorplan
define size and shape of core.
placing macros and IO pads in core area.



inputs: netlist (.v)

![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/b84199c3-e7f0-4e7a-b9e2-2bcc8c1f9b4e)

Sanity check:
![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/c49415ea-add5-445f-abaa-b1b812861846)

sanity check 2:
![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/6735bc66-c639-4f90-9501-97737b18987a)

Floorplan control parameters: Aspect ratio and core utilization

Place macros
Blockages: soft, hard, partial blockages: to avoid keeping all the cells at same place

fly lines: 
## Placement

