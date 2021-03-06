# Physical_Design_using_open_source_EDA_tools #

#### Description ####
-------------------------------------------------------------------
# Table of contents #

# Day 1 - Study and review various components of RISC-V based picoSoC
## IC design terminologies, opensource EDA tools and RISC-V based SoC design

IC design components terminologies
RISC-V based SoC reference design
Get familiar to open-source EDA tools

### Type below command:
cd
cd vsdflow
mkdir my_picorv32
cd my_picorv32
mkdir source synthesis layout
cp ~/vsdflow/verilog/picorv32.v source/.
qflow gui &

### Select below options in gui:
Technology = osu018
Verilog source file : picorv32.v
Verilog module : picorv32
Click on Set Stop

![image](https://user-images.githubusercontent.com/60166794/110214877-b892f900-7ecc-11eb-9e58-c1297284206d.png)






