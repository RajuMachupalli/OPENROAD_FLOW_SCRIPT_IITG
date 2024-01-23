> Open flow script tutorial 'https://openroad-flow-scripts.readthedocs.io/en/latest/tutorials/FlowTutorial.html'
> Document to add new designs: 'https://openroad-flow-scripts.readthedocs.io/en/latest/user/AddingNewDesign.html#adding-new-designs-to-the-orfs'
# Thsi document gives an idea on tools installation

sudo apt-get update; sudo apt-get upgrade; sudo apt install -y build-essential python3 python3-venv python3-pip make

wget https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2024-01-17/oss-cad-suite-linux-x64-20240117.tgz
## Install Linux on windows 10/11 through WSL
Open cmd window and type
> wsl –install

While installing if we get option to select distribution name :

> wsl --install -d Ubuntu-22.04

After restart give the user name and create password for your linux account name.

## For Ubuntu 22.04 by WSL installation:
Update Ubuntu Packages. In terminal execute following:
> sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make

We are going to use pre-build binaries, developed by 'precision innovations'

Installing klayout
> wget https://www.klayout.org/downloads/Ubuntu-22/klayout_0.28.15-1_amd64.deb
> sudo dpkg -i klayout_0.28.15-1_amd64.deb

While installing if we get any error for dependency run the following command:
>sudo apt --fix-broken install
>sudo dpkg -i klayout_0.28.15-1_amd64.deb

Install yosys
> wget https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2024-01-17/oss-cad-suite-linux-x64-20240117.tgz
> tar -xzvf oss-cad-suite-linux-x64-20240117.tgz

Download the OpenROAD binary
> wget https://github.com/Precision-Innovations/OpenROAD/releases/download/2024-01-16/openroad_2.0_amd64-ubuntu22.04-2024-01-16.deb
> sudo apt install ./openroad_2.0_amd64-ubuntu22.04-2024-01-16.deb

Download ORFS (OpenRoad Flow Script) repo. Its always good idea to create a folder and start working at that folder.
> cd
> git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git

Install editor tool
> sudo apt-get install gedit


## For Ubuntu20.04 with local/VM installation:
Day 1: 17/01/2024 installation steps.
Note: Highlighted in RED should be executed in the terminal.
Open terminal in Ubuntu Machine and type following:
cd
sudo apt-get update && sudo apt-get upgrade
Installing klayout
wget https://www.klayout.org/downloads/Ubuntu-20/klayout_0.28.15-1_amd64.deb
sudo dpkg -i klayout_0.28.15-1_amd64.deb
While installing if we get any dependency or package error :
sudo apt --fix-broken install
sudo dpkg -i klayout_0.28.15-1_amd64.deb
Installing yosys
wget
https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2024-01-17/oss-cadsuite-
linux-x64-20240117.tgz
tar -xzvf oss-cad-suite-linux-x64-20240117.tgz
Download the OpenROAD binary
wget
https://github.com/Precision-Innovations/OpenROAD/releases/download/2024-01-16/op
enroad_2.0_amd64-ubuntu20.04-2024-01-16.deb
sudo apt install ./openroad_2.0_amd64-ubuntu20.04-2024-01-16.deb
Download ORFS repo
cd
git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git
Install editor tool
sudo apt-get install gedit
// Linux independent commands
Edit env.sh file by appending the following commands
export OPENROAD_EXE=$(command -v /usr/bin/openroad)
export YOSYS_CMD=$(command -v ~/oss-cad-suite/bin/yosys)
export PATH="~/oss-cad-suite/bin:$PATH"
// Testing the install
cd OpenROAD-flow-scripts
cd flow
make
cd ..
git checkout master
git pull

# Day3
How to Run the design?

Step 1: Open WSL terminal or Ubuntu terminal based on Linux OS installation.
Step 2: Type cd and Press enter button
Step 3: source or_source.sh
Step 4: cd OpenROAD-flow-scripts/flow
Step 5: make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk

Note: If you’re creating a directory format ORFS/OpenROAD-flow-scripts mean change into that directory and execute make command mentioned above.

Also all commands should be executed inside flow directory for RTL-GDSII generation.

For the new terminal, it is mandatory to run source or_source.sh to run rtl-gdsii flow.

Now flow will run from synthesis to GDSII generation. If the RTL-GDSII flow already completed, it will display following message:

./logs/nangate45/gcd/base
Log                       Elapsed seconds
1_1_yosys                          1
3_3_place_gp                       1
4_1_cts                           11
No elapsed time found in logs/nangate45/gcd/base/4_equivalence_check.log
5_1_grt                            2
5_3_route                         13
6_1_merge                          3
6_report                           7
Total                             38

How to run stage by stage?

To run the OpenROAD flow stage by stage, for synthesis, floorplan, placement, cts, routing and gdsii generation, use following commands.

Synthesis with yosys: make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk synth

If you’re getting Nothing to do mean, clean up previous run results by,

make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk clean_all

Again execute : 


make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk synth

Floorplan includes floorplan initialization/IO placement/Macro placement/Power planning
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk floorplan

Placement includes global placement/resizer/detail placement
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk place

CTS includes clock tree build/optimization
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk cts

Routing includes global routing/detail routing
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk route

Finishing includes post route timing extraction/GDSII generation with KLayout
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk finish

How to view Layout in OpenROAD GUI?

To view any stage with OpenROAD GUI prefix stage name with gui.

For example to view floorplan stage:
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk gui_floorplan

How to create a new tag name instead of base?

To create different tag name for flow changes use

make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk FLOW_VARIANT=run1

Otherwise default base tag created for each logs/results/reports directory for each execution.

You can access logs as follows: gedit ./logs/nangate45/gcd/base/1_yosys.log

The format is ./logs/<platform name>/<design Name>/<flow tag>/xxx.log

To clean any particular stage and want to run for update configuration, prefix stage name with clean.

How to clean the previous run database?

make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk clean_floorplan

To remove entire logs/results/reports for specific run, use

make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk clean_all

