# This contains theoretical explanation for ASIC design flow

# Day3: Friday Januray 19 2024
## Synthesis flow
Requirements: 

1. Design files
      a. RTL code (.v)
      b. Constraint files (.sdc)

2. Technology files:
     a. .lib file: contains cells information, like power, capacitance, delay at different pins levels. logical information.
     b. .lef file: contains physical information of cells. size, pin name, pin location


technology file contains: layer name, type and direction of metal, pitch. .def file contains: cell info, pin

Two types of contraints: optimization constrains and design constraints

Synthesis output: netlist (.v), .sdc


step 1:
![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/7b22f945-a15e-4446-852b-c3b67ac3cf10)

proc: converts all operations to rtl

opt: optimization

fsm: FSM converts

memory: converts RTL

techmap: maps to technology

dfflibmap -liberty mycells.lib 

abc: mapping logic to mycells.lib

clean: cleans temporary files generated in above flow.

write_verilog synth.v: write the gatelevel netlist


## Floorplan
Define size and shape of core. Place macros and IO pads in core area.

inputs: netlist (.v)
![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/b84199c3-e7f0-4e7a-b9e2-2bcc8c1f9b4e)

Sanity check:
![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/c49415ea-add5-445f-abaa-b1b812861846)

sanity check 2:
![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/6735bc66-c639-4f90-9501-97737b18987a)

Floorplan control parameters: Aspect ratio and core utilization

Place macros

Blockages: soft, hard, partial blockages: to avoid keeping all the cells at same place.

requires macro's library files, size, orientation and location details.

fly lines: 

# Day 6
## Placement
Process of placing all standard cells.

Goal: Timing, Area, Routable. Minimize congestion, cell density and no DRC violation.

Inputs: Netlist, Physical libraries, Floorplan DEF file, Timing libraries, RC cornesrs, SDC file, UPF file (if the design has multiple voltage domains)
![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/14f256be-649c-48c4-a74a-c5515db3c005)

Checks: Clean netlist, Floor plan def should have: proper pin placement, macros and pre-placed cells in fix status and power planning free of DRCs, don't use or don't touch cells.

Pre-placement: Checks pre-placement cells. Macros, tap cells. 
Placement: 1.Global placement: to get approximate initial location according to timing, power and pre-placed cells 2. Legalization and 3. High fanout net synthesis: buffering high fanout nets.

Post-placement: Tries to meet all design timing requirements, WNS, TNS and DRVs.

Congestion: Routing congestion analysis, cell congestion analysis.

Congestion fixes: add placement blockages. Review the macro placement. Reduce local cell density using density screens. Congestion driven placement with high effort.
![image](https://github.com/RajuMachupalli/OPENROAD_FLOW_SCRIPT_IITG/assets/52839597/e88c7194-2f66-4302-ab55-fb5245334007)

## Clock Tree Synthesis
Process of distributing clock signals to clock pins of sequential circuits

Checks: Placement completed, power and ground nets pre-routed, acceptable congestion, acceptable timing, no max cap/trans violations.

Goals: minimum skew, no or acceptable timing violations, no or minimal congession, acceptable power number, acceptable utilization jumps at post CTS.

Inputs: Placement def, Target latency and skew

Outputs: Timing report, skew report, insertion delay, 

## Routing
Making signal connections between signal pins using metals

Objective: Skew requirements, open/short circuit clean, must meet setup and timing margin.

Goals: Minimize the total interconnect length, minimize the critical path delay, minimize the number of layers change, meeting timing DRCs, eliminate cross-tols noise.

Routing flow: Global routing, track assignment, detail routing, and search and repair.

Global routing: Identifies routable paths.
Detailed paths: 
search and repair: 

Filler cell insertion: non logical cells or filler cells insderted to make n/p-wells continuty.

Outputs: SPEF file, GDS-II, netlist, sdc. (OpenRC used to extract SPEF files)


OpenSTA will follow for static timing analysis.
