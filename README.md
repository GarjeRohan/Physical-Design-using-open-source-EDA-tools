# Physical_Design_using_open_source_EDA_tools #

#### Description ####
#### This repository is to give brief idea about the VSD's 'Beginner Soc/Physical Design using open source EDA tools' Workshop. The workshop gives me a hands on experience with the open source tools like yosys,magic,opentimer,qrouter that are used in Physical Design. ####
-------------------------------------------------------------------
# Table of contents #
Day 1 - Study and review various components of RISC-V based picoSoC  <br/>
Day 2 - Chip Planning Strategies and Introduction to Foundry Library Cells  <br/>
Day 3 - Design and Characterize one Library Cell using magic Layout Tool and ngspice  <br/>
Day 4 - Pre-Layout Timing Analysis and Importance of Good Clock Tree  <br/>
Day 5 - Final Steps for RTL2GDS  <br/>

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
![image](https://user-images.githubusercontent.com/60166794/110220312-c8213a80-7eea-11eb-948a-a63287c81337.png)

The intersection point is called as swithching threshold. <br/>


Open file called "inv_tran.spice" using below command: <br/>
leafpad inv_tran.spice <br/>
Change PMOS width to 0.75u, Save and Close <br/>
![image](https://user-images.githubusercontent.com/60166794/110218296-f567eb80-7ede-11eb-9ffe-16a9f805ffc7.png)<br/>
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


# Day 4 - Pre-layout timing analysis and importance of good clock tree
## Clock tree synthesis (CTS) and static timing analysis (STA)
* #### Timing modelling using delay tables
* #### Timing analysis with ideal clocks
* #### Clock tree synthesis and signal integrity
* #### Timing analysis with real clocks

### Lab:
Open terminal and Type below commands  <br/>
cd <br/>
git clone https://github.com/kunalg123/ngspice_labs <br/>
cd ngspice_labs <br/>
cat inv_tran.spice <br/>
![image](https://user-images.githubusercontent.com/60166794/110237324-79fb4e00-7f61-11eb-87de-72aab1d8e32e.png) <br/>
The input rise slew and fall slew is 10ps. <br/>
Type below command: <br/>
ngspice inv_tran.spice <br/>

![image](https://user-images.githubusercontent.com/60166794/110237753-a87a2880-7f63-11eb-8068-98b158724155.png)
Go to labs Modify to output load to 20fF in inv_tran.spice Run ngspice  <br/>
![image](https://user-images.githubusercontent.com/60166794/110237871-64d3ee80-7f64-11eb-8b55-cc1e8b219dd2.png)  <br/>

Go to labs Open below file using "leafpad" or "less" or "vim" - whichever you are comfortable with) <br/>

/usr/local/share/qflow/tech/osu018/osu018_stdcells.lib <br/>
Look between line numbers 21 to 24 What is the value of "slew_upper_threshold_pct_fall" ? <br/>

![image](https://user-images.githubusercontent.com/60166794/110238210-51298780-7f66-11eb-8b72-e52b887326e6.png) <br/>
Go to labs Open the below file using leafpad or vim or less - whichever you are comfortable with <br/>

/usr/local/share/qflow/tech/osu018/osu018_stdcells.lib <br/>
Look for lines between 25 to 28 <br/>

What is the value of output_threshold_pct_rise ? <br/>
![image](https://user-images.githubusercontent.com/60166794/110238257-afef0100-7f66-11eb-8596-280d75429033.png) <br/>
What are the 2 variables of "delay_template_5x5"? <br/>
![image](https://user-images.githubusercontent.com/60166794/110238298-ecbaf800-7f66-11eb-935d-5c3b217fcf70.png) <br/>
The delay table below line number 2943 is for which cell ? <br/>
![image](https://user-images.githubusercontent.com/60166794/110238338-22f87780-7f67-11eb-954b-68a6fbcde2bd.png)  <br/>
Which delay template is used for INVX1?  <br/>
delay_template_5x5 <br/>

![image](https://user-images.githubusercontent.com/60166794/110358225-2c1a3f00-8062-11eb-9f2a-7560d9bcfd62.png)
![image](https://user-images.githubusercontent.com/60166794/110358251-35a3a700-8062-11eb-8f47-4da236b006ed.png)
![image](https://user-images.githubusercontent.com/60166794/110358289-3d634b80-8062-11eb-98ad-14d4d80c75b9.png)



<!---
your comment goes here
and here
-->

create_clock -name clk -period 2.5 -waveform {0 1.25} [get_ports clk] <br/>
Save and close the above file <br/>


leafpad prelayout_sta.conf <br/>
Type below lines in prelayout_sta.conf file which you have just opened above <br/>

read_liberty /usr/local/share/qflow/tech/osu018/osu018_stdcells.lib <br/>
read_verilog synthesis/picorv32.rtlnopwr.v <br/>
link_design picorv32 <br/>
read_sdc picorv32.sdc <br/>
report_checks <br/>
Save and close the above file <br/>

Now type below command <br/>

sta prelayout_sta.conf <br/>
What is the SLACK value you see? <br/>
around -0.56ns <br/>



Repeat all steps in D4SK2 - MCQ11 <br/>

NOTE - If you have already done that, then you will see below 'sta' terminal like below <br/>

% <br/>
Type below command <br/>

report_checks -digits 4 <br/>
What is the data arrival time? <br/>

around 2.9001ns <br/>

Repeat all steps in D4SK2 - MCQ12 <br/>

What is data required time ? <br/>
around 2.3389ns <br/>




Perform all steps in D4SK2 - MCQ11 <br/>

You are now at below "sta" terminal <br/>

% <br/>
Type below command in terminal <br/>

set_propagated_clock [all_clocks] <br/>
report_checks <br/>
<!---
What is the SLACK value after clock propagation ? <br/>

around -0.68ns <br/>

Perform all steps in D4SK4 - MCQ2 <br/>

What is launch clock network delay? <br/>

Hint - Scroll a little up at the beginning of report after "report_checks" command. There is line after "clock clk (rise edge)" <br/>

0.58ns <br/>
1.Perform all steps in D4SK4 - MCQ3 <br/>

What is the capture clock network delay? <br/>

Hint - Look in the same report for the line "clock clk (rise edge)" <br/>

around 0.56ns <br/>

-->

# Day 5 - Final steps for RTL2GDS
## Routing, DRC and interactive PNR tutorial

* #### Routing and design rule check (DRC)
* #### PNR interactive flow tutorial

Type below commands

cd
cd vsdflow/my_picorv32
qflow route picorv32
qflow sta picorv32 ...
qflow backanno picorv32
leafpad log/sta.log
<!---
your comment goes here
and here


What is the pre-layout frequency?
the pre-layout frequency is
-->
then open the below file

log/post_sta.log
<!---
your comment goes here
and here


What is post-layout frequency?
the post-layout to pre-layout drop in frequency is 20MHz
the reason for post-layout to pre-layout drop in frequency is parasitics.
-->

# Qrouter : Routing In-Progress
![image](https://user-images.githubusercontent.com/60166794/110356931-c1b4cf00-8060-11eb-9026-548861d1248f.png)

# Qrouter : Routing Complete
![image](https://user-images.githubusercontent.com/60166794/110356855-ac3fa500-8060-11eb-83a8-a69f1f23e26f.png)


