# Physical_Design_using_open_source_EDA_tools #

#### Description ####
-------------------------------------------------------------------
# Table of contents #

# Day 1 - Study and review various components of RISC-V based picoSoC
## IC design terminologies, opensource EDA tools and RISC-V based SoC design

IC design components terminologies <br/>
RISC-V based SoC reference design <br/>
Get familiar to open-source EDA tools <br/>



 Type the command "yosys" in terminal: <br/>
 ![image](https://user-images.githubusercontent.com/60166794/110215078-d90f8300-7ecd-11eb-8ef1-4f9af2535176.png) <br/>
After typing "which sta", the sta tool is linked to following path: <br/>
### /usr/bin/sta ### <br/>
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
![image](https://user-images.githubusercontent.com/60166794/110215385-80d98080-7ecf-11eb-9d86-a0c1d6d943d2.png) <br/>

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







