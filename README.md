# Physical_Design_using_open_source_EDA_tools #

#### Description ####
#### This repository is to give brief idea about the VSD's 'Beginner Soc/Physical Design using open source EDA tools' Workshop. The workshop gives me a hands on experience with the open source tools like yosys,magic,opentimer,qrouter that are used in Physical Design. ####
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
![image](https://user-images.githubusercontent.com/60166794/111354385-467c9a00-86ac-11eb-9191-ff94a05013fc.png)  <br/>

This specifies the command 'which sta' when typed in terminal it shows the location of sta ie.,where it is present that is in the usr folder to bin sub folder and there sta is present <br/>
![image](https://user-images.githubusercontent.com/60166794/111355604-885a1000-86ad-11eb-8a55-8522a0d15d17.png) <br/>

A git clone command is used to target this existing repository.
![image](https://user-images.githubusercontent.com/60166794/111356513-7331b100-86ae-11eb-9771-b0a391f2fe3a.png)

In image below the .ls -ltr outdir_spi_slave | wc command will show the total 17 number of lines beacuse 1st line will give total number and the rest 16 are the number of flies. <br/>
![image](https://user-images.githubusercontent.com/60166794/111357284-30bca400-86af-11eb-8f56-083335e73be6.png)

### Type below command: <br/>
cd outdir_spi_slave <br/>
qflow display spi_slave <br/>
It will open 2 windows "layout1" and "tkcon" <br/>
On "tkcon" window, type "box". <br/>
The output area in microns is 15420.24 <br/>
![image](https://user-images.githubusercontent.com/60166794/111358705-a70dd600-86b0-11eb-80bc-0c710a462aec.png) <br/>

### Type below command: <br/>

cd vsdflow is a command change the directory to vsdflow, mkdir is a command create the folder, cd my_picorv32 is a command to change the directory to my_picorv32, mkdir source synthesis layout is a command to create folders source, synthesis and layout, cp ~/vsdflow/Verilog/picorv32.v/source/. - copy the Verilog file i.e picorv32 from source to vsdflow, qflow gui &- it open qflow manager in a graphical user interface.
### Select below options in gui: <br/>
Technology = osu018 <br/>
Verilog source file : picorv32.v <br/>
Verilog module : picorv32 <br/>
Click on Set Stop <br/>
![image](https://user-images.githubusercontent.com/60166794/111359492-9316a400-86b1-11eb-9513-946eaff53084.png)  <br/>

# Day 2 - Chip planning strategies and introduction to foundry library cells <br/>
## Floorplanning considerations and process development kits (PDK's) <br/>
* #### Chip Floor planning considerations 
* #### Library Binding and Placement 
* #### Cell design and characterization flows 
* #### General timing characterization parameters
![image](https://user-images.githubusercontent.com/60166794/111362518-e50cf900-86b4-11eb-8fae-7a5985fd8d25.png)  <br/>
![image](https://user-images.githubusercontent.com/60166794/111362718-26050d80-86b5-11eb-866d-1f499469a393.png)  <br/>
The die is imprinted multiple times on wafer to increase its throughput.  <br/>



![image](https://user-images.githubusercontent.com/60166794/111362192-834c8f00-86b4-11eb-9057-73e3267362d0.png)  <br/>
### Lab:
![image](https://user-images.githubusercontent.com/60166794/111363969-b09a3c80-86b6-11eb-8f7e-88a4ffddc51f.png)  <br/>
![image](https://user-images.githubusercontent.com/60166794/111364236-fd7e1300-86b6-11eb-8ef5-143e694c11f1.png)  <br/>
![image](https://user-images.githubusercontent.com/60166794/111364481-47ff8f80-86b7-11eb-9551-ed7c366133b9.png)  <br/>
![image](https://user-images.githubusercontent.com/60166794/111364664-885f0d80-86b7-11eb-8150-a399f92bb767.png) <br/>



The area of chip in microns is 812062.19  <br/>
![image](https://user-images.githubusercontent.com/60166794/111365141-218e2400-86b8-11eb-9093-950dc62dc765.png)  <br/>

# Day 3
* #### Labs for CMOS inverter ngspice simulations
* #### Art of layout using Euler’s path plus stick diagram
* #### Labs for Magic and post-layout ngspice simulations
* #### Inception of Layout – CMOS fabrication process

![image](https://user-images.githubusercontent.com/60166794/111373036-74b8a480-86c1-11eb-833f-2ed92e6c6087.png) <br/>

![image](https://user-images.githubusercontent.com/60166794/111373013-69fe0f80-86c1-11eb-8347-c448302494bf.png) <br/>

### Lab:
#### Type below commands :
cd <br/>
git clone https://github.com/kunalg123/ngspice_labs.git <br/>
cd ngspice_labs <br/>
cat inv.spice <br/>
![image](https://user-images.githubusercontent.com/60166794/111368316-bc3c3200-86bb-11eb-8b34-70b6c12c85b0.png) <br/>

The width of NMOS and PMOS transistor is 0.375u. <br/>

##### Type below commands
cd ngspice_labs <br/>
ngspice inv.spice <br/>
On the above ngspice terminal, type below commands <br/>
run <br/>
setplot dc1 <br/>
plot out in <br/>
This will open a plot with CMOS VTC and Blue 45 degree line <br/>
Click on the intersection of Blue line and CMOS VTC. <br/>
![image](https://user-images.githubusercontent.com/60166794/111368541-08877200-86bc-11eb-8704-88087cac8550.png) <br/>

The intersection point is called as swithching threshold. <br/>


Open file called "inv_tran.spice" using below command: <br/>
leafpad inv_tran.spice <br/>
Change PMOS width to 0.75u, Save and Close <br/>
![image](https://user-images.githubusercontent.com/60166794/111368863-5ef4b080-86bc-11eb-9268-d4b7abed4a52.png)  <br/>
![image](https://user-images.githubusercontent.com/60166794/111369617-46d16100-86bd-11eb-988d-3c5eb774c079.png) <br/>


Transient simulations can be performed using below commands <br/>
ngspice inv_tran.spice <br/>
ngspice 1 -> run <br/>
ngspice 1 -> setplot tran1 <br/>
ngspice 1 -> plot out in <br/>
![image](https://user-images.githubusercontent.com/60166794/111369835-813afe00-86bd-11eb-9817-92eef6113e95.png) <br/>
![image](https://user-images.githubusercontent.com/60166794/111371640-b5172300-86bf-11eb-8c0d-fdf7f4d1097f.png)  <br/>
![image](https://user-images.githubusercontent.com/60166794/111371716-cc561080-86bf-11eb-9abe-651351c5d4be.png)  <br/>


#### Type below commands 
cd <br/>
cd ngspice_labs <br/>
magic -T min2.tech <br/>
This will open magic layout window and tkcon window  <br/>
Go to tkcon window and type below command <br/>
source draw_fn.tcl <br/>

![image](https://user-images.githubusercontent.com/60166794/111370162-e4c52b80-86bd-11eb-842d-31a29ca66318.png)  <br/>

![image](https://user-images.githubusercontent.com/60166794/111370249-01f9fa00-86be-11eb-96be-981249a6d251.png) <br/>

#### Type below command 
cd <br/>
cd ngspice_labs <br/>
magic -T min2.tech fn_postlayout.mag & <br/>
![image](https://user-images.githubusercontent.com/60166794/111370312-15a56080-86be-11eb-968e-359489625d77.png)  <br/>


# Day 4 - Pre-layout timing analysis and importance of good clock tree
## Clock tree synthesis (CTS) and static timing analysis (STA)
* #### Timing modelling using delay tables
* #### Timing analysis with ideal clocks
* #### Clock tree synthesis and signal integrity
* #### Timing analysis with real clocks

![image](https://user-images.githubusercontent.com/60166794/111373174-99148100-86c1-11eb-9a36-8e430d50b0bd.png)  <br/>
![image](https://user-images.githubusercontent.com/60166794/111373193-a03b8f00-86c1-11eb-9e2c-b3634980918a.png)  <br/>

### Lab:
cd ngspice_labs <br/>
cat inv_tran.spice <br/>

![image](https://user-images.githubusercontent.com/60166794/111374388-0ffe4980-86c3-11eb-8df9-4c67d7f9f782.png) <br/>

The input rise slew and fall slew is 10ps. <br/>
Type below command: <br/>
ngspice inv_tran.spice <br/>

![image](https://user-images.githubusercontent.com/60166794/111374026-a3834a80-86c2-11eb-910b-2cd86e0da98c.png)  <br/>
Modify to output load to 20fF in inv_tran.spice Run ngspice  <br/>
![image](https://user-images.githubusercontent.com/60166794/111374595-4dfb6d80-86c3-11eb-8d94-a8cdd0f9d2a4.png)  <br/>

Open the below file  <br/>
/usr/local/share/qflow/tech/osu018/osu018_stdcells.lib <br/>
The value of "slew_upper_threshold_pct_rise" is 80 <br/>
![image](https://user-images.githubusercontent.com/60166794/111375011-c9f5b580-86c3-11eb-9175-7fd0c2b9c626.png) <br/>


The value of output_threshold_pct_rise is 50 c
![image](https://user-images.githubusercontent.com/60166794/111375472-49838480-86c4-11eb-87dd-2c452ade6ac3.png)  <br/>

![image](https://user-images.githubusercontent.com/60166794/111375594-72a41500-86c4-11eb-94d3-dda665621e5d.png) <br/>

![image](https://user-images.githubusercontent.com/60166794/111375755-a67f3a80-86c4-11eb-9f6d-cfa62e1137d3.png)  <br/>


![image](https://user-images.githubusercontent.com/60166794/110358225-2c1a3f00-8062-11eb-9f2a-7560d9bcfd62.png) <br/>
![image](https://user-images.githubusercontent.com/60166794/110358251-35a3a700-8062-11eb-8f47-4da236b006ed.png) <br/>
![image](https://user-images.githubusercontent.com/60166794/110358289-3d634b80-8062-11eb-98ad-14d4d80c75b9.png) <br/>
![image](https://user-images.githubusercontent.com/60166794/111377415-a1bb8600-86c6-11eb-8c8a-2b71dd718a34.png) <br/>

![image](https://user-images.githubusercontent.com/60166794/111377470-b435bf80-86c6-11eb-9514-ffd8889a1d3e.png) <br/>
![image](https://user-images.githubusercontent.com/60166794/111377503-bb5ccd80-86c6-11eb-9dd4-e4820e2c5caa.png) <br/>



<!---
your comment gojes here
and her
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
--> 
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

![image](https://user-images.githubusercontent.com/60166794/111377713-fe1ea580-86c6-11eb-8d63-38f88977d440.png) <br/>

Type below commands

cd
cd vsdflow/my_picorv32
qflow route picorv32
qflow sta picorv32 ...
qflow backanno picorv32
leafpad log/sta.log
![image](https://user-images.githubusercontent.com/60166794/111378792-53a78200-86c8-11eb-8297-1df1ff0121f8.png)  <br/>
![image](https://user-images.githubusercontent.com/60166794/111378870-7174e700-86c8-11eb-80ae-b8d5dbcf8779.png) <br/>


<!---
your comment goes here
and here
What is the pre-layout frequency?
the pre-layout frequency is
--then open the below file
log/post_sta.log
<!---
your comment goes here
and here
What is post-layout frequency?
the post-layout to pre-layout drop in frequency is 20MHz
the reason for post-layout to pre-layout drop in frequency is parasitics.
-->

# Qrouter : Routing In-Progress
![image](https://user-images.githubusercontent.com/60166794/111378993-9ec19500-86c8-11eb-8ce0-de56c6759e2b.png)  <br/>

# Qrouter : Routing Complete
![image](https://user-images.githubusercontent.com/60166794/110356855-ac3fa500-8060-11eb-83a8-a69f1f23e26f.png)  <br/>


