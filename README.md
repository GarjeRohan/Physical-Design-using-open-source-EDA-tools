# Physical_Design_using_open_source_EDA_tools #

#### Description ####
-------------------------------------------------------------------
# Table of contents #

# Day 1 - Study and review various components of RISC-V based picoSoC
## IC design terminologies, opensource EDA tools and RISC-V based SoC design

* #### IC design components terminologies 
* #### RISC-V based SoC reference design 
* #### Get familiar to open-source EDA tools

### Lab:
Type the command "yosys" in terminal: <br/>
![image](https://user-images.githubusercontent.com/60166794/110215078-d90f8300-7ecd-11eb-8ef1-4f9af2535176.png) <br/>
After typing "which sta", the sta tool is linked to following path: <br/>
/usr/bin/sta <br/>
![image](https://user-images.githubusercontent.com/60166794/110215232-8d110e00-7ece-11eb-8cf2-b041c8d1d724.png)  <br/>

Type below command from current working directory <br/>
git clone https://github.com/kunalg123/vsdflow.git <br/>
cd vsdflow <br/>
./vsdflow spi_slave_design_details.csv <br/>
ls -ltr outdir_spi_slave/ <br/>
Here you will see lot of files created. <br/>
Now type below command <br/>
ls -ltr outdir_spi_slave | wc <br/>
This will give you 3 numbers in one row, where 1st number represents number of files. <br/> 
The total numbers of file we can see is: 16 <br/>
![image](https://user-images.githubusercontent.com/60166794/110219637-7d052880-7ee6-11eb-9a3e-1dd0e1e10e92.png)

### Type below command: <br/>
cd outdir_spi_slave <br/>
qflow display spi_slave <br/>
It will open 2 windows "layout1" and "tkcon" <br/>
On "tkcon" window, type "box". <br/>
The output area in microns is 15420.24 <br/>
![image](https://user-images.githubusercontent.com/60166794/110215574-86839600-7ed0-11eb-8a37-ebb60888a943.png)  <br/>
### Type below command: <br/>
cd <br/>
cd vsdflow <br/>
mkdir my_picorv32 <br/>
cd my_picorv32 <br/>
mkdir source synthesis layout <br/> 
cp ~/vsdflow/verilog/picorv32.v source/. <br/>
qflow gui & <br/>
### Select below options in gui: <br/>
Technology = osu018 <br/>
Verilog source file : picorv32.v <br/>
Verilog module : picorv32 <br/>
Click on Set Stop <br/>
![image](https://user-images.githubusercontent.com/60166794/110214877-b892f900-7ecc-11eb-9e58-c1297284206d.png) <br/>
# Day 2 - Chip planning strategies and introduction to foundry library cells <br/>
## Floorplanning considerations and process development kits (PDK's) <br/>
* #### Chip Floor planning considerations 
* #### Library Binding and Placement 
* #### Cell design and characterization flows 
* #### General timing characterization parameters
### Lab:
#### Type below command : 
cd <br/>
cd vsdflow/my_picorv32 <br/>
qflow display picorv32 & <br/>
This will open layout and tkcon window In the layout window, select whole chip using below steps <br/>
Take cursor to bottom left <br/>
Left mouse click <br/>
Take cursor to top right <br/>
Right mouse click <br/>
Press Shift+i <br/>
This will select the whole layout Now in tkcon window, type below command <br/>
box <br/>
The area of chip in microns is 812062.19  <br/>
![image](https://user-images.githubusercontent.com/60166794/110216981-a074a700-7ed7-11eb-86c4-f8586a1bb323.png) <br/>

# Day 3
* #### Labs for CMOS inverter ngspice simulations
* #### Art of layout using Euler’s path plus stick diagram
* #### Labs for Magic and post-layout ngspice simulations
* #### Inception of Layout – CMOS fabrication process

### Lab:
#### Type below commands :
cd <br/>
git clone https://github.com/kunalg123/ngspice_labs.git <br/>
cd ngspice_labs <br/>
cat inv.spice <br/>
![image](https://user-images.githubusercontent.com/60166794/110218111-ce5cea00-7edd-11eb-88d0-9d12e3c14569.png) <br/>
The width of NMOS and PMOS transistor is 0.375u. <br/>

##### Type below commands

cd <br/>
cd ngspice_labs <br/>
ngspice inv.spice <br/>
There will be terminal like below <br/>
ngspice 1 -> <br/>
On the above ngspice terminal, type below commands <br/>
run <br/>
setplot dc1 <br/>
plot out in <br/>
This will open a plot with CMOS VTC and Blue 45 degree line <br/>
Click on the intersection of Blue line and CMOS VTC. <br/>
Go to terminal <br/>
![image](https://user-images.githubusercontent.com/60166794/110218296-f567eb80-7ede-11eb-9ffe-16a9f805ffc7.png)<br/>
The intersection point is called as swithching threshold. <br/>


Open file called "inv_tran.spice" using below command: <br/>
leafpad inv_tran.spice <br/>
Change PMOS width to 0.75u, Save and Close <br/>
Type below commands for transient simulations <br/>
ngspice inv_tran.spice <br/>
ngspice 1 -> run <br/>
ngspice 1 -> setplot tran1 <br/>
ngspice 1 -> plot out in <br/>
![image](https://user-images.githubusercontent.com/60166794/110218472-f5b4b680-7edf-11eb-8fa0-c8a9e67bbf2f.png) <br/>


#### Type below commands 
cd <br/>
cd ngspice_labs <br/>
magic -T min2.tech <br/>
This will open magic layout window and tkcon window  <br/>
Go to tkcon window and type below command <br/>
source draw_fn.tcl <br/>

![image](https://user-images.githubusercontent.com/60166794/110218739-555f9180-7ee1-11eb-886a-48f9412109c6.png) <br/>
![image](https://user-images.githubusercontent.com/60166794/110218772-8213a900-7ee1-11eb-9ce0-aa1de11da71d.png) <br/>

#### Type below command 
cd <br/>
cd ngspice_labs <br/>
magic -T min2.tech fn_postlayout.mag & <br/>
![image](https://user-images.githubusercontent.com/60166794/110218825-c3a45400-7ee1-11eb-8081-fb28e7afddc8.png) <br/>


