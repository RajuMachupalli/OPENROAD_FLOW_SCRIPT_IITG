# Thsi document gives an idea on tools installation

sudo apt-get update; sudo apt-get upgrade; sudo apt install -y build-essential python3 python3-venv python3-pip make

wget https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2024-01-17/oss-cad-suite-linux-x64-20240117.tgz

## For Ubuntu22.04 by WSL installation:
Day 1: 17/01/2024 installation steps. If you’re direct/dual boot/VMware installation
means directly jump to Update ubuntu packages step by skipping wsl installation.
Note: Highlighted in RED should be executed in the terminal.
Open terminal in Ubuntu Machine and type following:
Install wsl
wsl –install
While installing if we get option to select distribution name :
wsl --install -d Ubuntu-22.04
After restart give the user name and create password for your linux account name.
In terminal execute following:
Update Ubuntu Packages
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make
Installing klayout
wget https://www.klayout.org/downloads/Ubuntu-22/klayout_0.28.15-1_amd64.deb
sudo dpkg -i klayout_0.28.15-1_amd64.deb
While installing if we get any error for dependency run following:
sudo apt --fix-broken install
sudo dpkg -i klayout_0.28.15-1_amd64.deb
Installing yosys
wget
https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2024-01-17/oss-c
ad-suite-linux-x64-20240117.tgz
tar -xzvf oss-cad-suite-linux-x64-20240117.tgz
Download the OpenROAD binary
ubuntu 22.04 :
wget
https://github.com/Precision-Innovations/OpenROAD/releases/download/2024-01-16
/openroad_2.0_amd64-ubuntu22.04-2024-01-16.deb
sudo apt install ./openroad_2.0_amd64-ubuntu22.04-2024-01-16.deb
Download ORFS repo
cd
git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git
Install editor tool
sudo apt-get install gedit


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
