# EXP NO:4
# Date:02/04/24

# SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS
# AIM:
To simulate and synthesis JK-Flipflop, SR-Flipflop, T-Flipflop, D-Flipflop And counters using Vivado 2023.2

# APPARATUS REQUIRED:
vivado 2023.2

# PROCEDURE:

Open Vivado: Launch Xilinx Vivado software on your computer.

Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

# LOGIC DIAGRAM

# SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

# CODE

module srff(s,r,clk,reset,q);
input s,r,clk,reset;
output reg q;
always@(posedge clk)
begin
if(reset==1)
q =1'b0;
else 
begin
case({s,r})
 2'b00: q = q;
 2'b01: q = 1'b0;
 2'b10: q = 1'b1;
 2'b11: q = 1'bx;
 default:q = ~q;
endcase
end 
end
endmodule

# OUTPUT
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/1d4d5b7f-8a18-427e-8814-5a7f07906a09)


# JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

# CODE

module jk_ff(j,k,clk,reset,q);
input j,k,clk,reset;
output reg q;
always@(posedge clk)
begin
if(reset==1)
q =1'b0;
else 
begin
case({j,k})
 2'b00: q = q;
 2'b01: q = 1'b0;
 2'b10: q = 1'b1;
 2'b11: q = ~q;
 default:q =1'b0;
endcase
end 
end
endmodule

# OUTPUT
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/21359b55-2104-41cd-aeae-00fb4605a397)


# T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

# CODE

module tff(clk,rst,j,q);
input clk,rst,j;
output reg q;
always@(posedge clk)
begin
case(t)
1'b0:q=q;
1'b1:q=~q;
default=q=1'b0;
endcase
end
endmodule

# OUTPUT

![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/5bf07416-a668-4812-b114-4bce82d8b7d4)

# D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

# CODE

module dff(clk,rst,d,q);
input clk,rst,d;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=1'b0;
else
q=d;
end
endmodule

# OUTPUT  
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/9c0ee77e-6084-4e56-a295-9d3ebdfcdf81)


# COUNTER
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/1f537f12-00bb-4fd4-a18d-2b8e28d4b66b)

# UPDOWNCOUNTER

![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/5eb7c973-241e-48ce-bd0f-dc72bad2f2c0)

CODE

module updown(clk,rst,up_down,count);
input clk,rst,up_down;
output reg[3:0]count;
always@(posedge clk)
begin
if(rst==1)
count <= 4'b0000;
else if (up_down == 1'b1)
count <= count + 1'b1;
else
count <= count-1'b1;
end
endmodule

# OUTPUT

![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/659ae1b9-a76f-492b-ad47-309691472027)

# MOD10COUNTER
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/79d72faf-3fe5-4b98-a5ed-5e3b550fd7e3)

# CODE

module mod(clk,rst,count);
input clk,rst;
output reg[3:0]count;
always @(posedge clk)
begin
if(rst==1 | count==4'b1001)
count <= 4'b0000;
else
count <= count +1;
end
endmodule

# OUTPUT

![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/e4318e0d-e117-46cd-9f27-c88a6d3154e9)

# RIPPLECARRYCOUNTER
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/d27422cc-b36a-406a-b4bb-5b50bbde886c)

![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/0d896d59-836a-428e-bd89-d79455242f27)

# CODE

module ripplecounter(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tff1(q[0],clk,rst);
tff tff2(q[1],q[0],rst);
tff tff3(q[2],q[1],rst);
tff tff4(q[3],q[2],rst);
endmodule
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule
module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always@(posedge clk or posedge rst)
begin
if(rst)
q=1'b10;
else
q=d;
end
endmodule

# OUTPUT
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/aab03730-262c-415c-b516-f88a7d2328a3)

# RESULT:
Thus simulate and synthesis JK-Flipflop, SR-Flipflop, T-Flipflop, D-Flipflop And counters was succesfully executed and verified.


