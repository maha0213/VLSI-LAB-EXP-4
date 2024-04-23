# VLSI-LAB-EXP-4
# SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS
# AIM:
To simulate and synthesis JK-Flipflop, SR-Flipflop, T-Flipflop, D-Flipflop And counters using Vivado 2023.2

# APPARATUS REQUIRED:
vivado 2023.2
# LOGIC DIAGRAM

# SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)


# JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

# T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)


# D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)


# COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)


  
# PROCEDURE:
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

# VERILOG CODE
SR FLIPFLOP:
module SR(clk,s,r,rst,q );

input s,r,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({s,r})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=1'bx;

endcase

end

end

endmodule

# JK FLIPFLOP:
module jk(j,k,clk,rst,Q);

input j,k,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)Q=0;

else

begin

case({j,k})

2'b00:Q=Q;

2'b01:Q=0;

2'b10:Q=1;

2'b11:Q=~Q;

endcase

end

end

endmodule

# T FLIPFLOP:
module tff(t,clk,rst,Q);

input t,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)

Q=1'b0;

else if(t==0)

Q=Q;

else

Q=~Q;

end

endmodule

# D FLIPFLOP:
module dff(d,clk,rst,Q);

input d,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)

Q=1'b0;

else

Q=d;

end

endmodule

# COUNTER
# UPDOWN COUNTER:
module updown(clk,rst,updown,out);

input clk,rst,updown;

output reg[3:0]out;

always@(posedge clk)

begin

if(rst==1)

out=4'b0000;

else if(updown==1);

out=out-1;

end

endmodule

# MOD 10 COUNTER:
module mod(clk,rst,out);

input clk,rst;

output reg[3:0]out;

always @(posedge clk)

begin

if(rst==1 | out==4'b1001)

out=4'b0000;

else

out=out+1;

end

endmodule

# RIPPLE CARRY COUNTER:
module ripple_carry_counter(q, clk, reset);

output [3:0] q;

input clk, reset;

T_FF tff0(q[0], clk, reset);

T_FF tff1(q[1], q[0], reset);

T_FF tff2(q[2], q[1], reset);

T_FF tff3(q[3], q[2], reset);

endmodule

module T_FF(q, clk, reset);

output q;

input clk, reset;

wire d;

D_FF dff0(q, d, clk, reset);

not n1(d, q);

endmodule

module D_FF(q, d, clk, reset);

output q;

input d, clk, reset;

reg q;

always @(posedge reset or negedge clk)

if (reset)

q = 1'b0;

else

q = d;

endmodule



# OUTPUT WAVEFORM
# SR FLIPFLOP:
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/219ed8c1-dbb3-47c6-a984-1c1a1d6310fa)
# K FLIPFLOP:
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/40c6e4b6-caba-4fde-9636-549434317b14)
# T FLIPFLOP:
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/044c2ccd-a604-4307-ba26-106410986966)
# D FLIPFLOP:
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/14b11b26-28b2-46a5-9fa6-7a27dd408202)
# COUNTER:
# UPDOWN COUNTER:
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/799bfd3b-f9d4-49b4-9548-081cc81eb0c4)
# MOD 10 COUNTER:
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/8d830d04-1bbb-4c59-9b00-239cc872cfe2)
# RIPPLE CARRY COUNTER:
![image](https://github.com/maha0213/VLSI-LAB-EXP-4/assets/159602131/7baf0cd6-0093-4040-a3e6-ef810a712dbb)

# RESULT:
Thus simulate and synthesis JK-Flipflop, SR-Flipflop, T-Flipflop, D-Flipflop And counters was succesfully executed and verified.


