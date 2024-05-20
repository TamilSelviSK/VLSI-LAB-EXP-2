# SIMULATE AND SYNTHESIS ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR USING VIVADO.

## AIM:

To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using VIVADO.

## APPARATUS REQUIRED:

VIVADO 2023.2

## PROCEDURE:

### STEP:1 
Start the Vivado, Select and Name the New project.
### STEP:2 
Select the device family, device, package and speed.
### STEP:3
Select new source in the New Project and select Verilog Module as the Source type.
### STEP:4
Type the File Name and Click Next and then finish button. Type the code and save it.
### STEP:5 
Select the Behavioural Simulation in the Source Window and click the check syntax.
### STEP:6
Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

## ENCODER 8:3:

![321538223-9545fd02-934d-4d04-8e15-7f4b703cc91a](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/1784400f-3406-41b7-b1a3-43bcd140717b)

## PROGRAM:
```
module encoder83df(i, a, b, c);
input [7:0]i;
output a,b,c;
assign a=i[4] | i[5] | i[6] | i[7];
assign b=i[2] | i[3] | i[6] | i[7];
assign c=i[1] | i[3] | i[5] | i[7];
endmodule
```
## OUTPUT:

![321538295-aa76db81-e951-434e-a613-62aa608d6f4f](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/9918291c-1b64-48c7-93e8-86bde00bd665)

## DECODER3:8:

![321538368-bbd40d54-e59a-4b83-a17b-b2bb381e8018](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/49cf3bf3-aff8-401b-92e7-9715f2042569)

## PROGRAM:
```
module decoder_3_8(s,y);
input [2:0]s;
output [7:0]y;
assign y[0]=~s[2]&~s[1]&~s[0];
assign y[1]=~s[2]&~s[1]&s[0];
assign y[2]=~s[2]&s[1]&~s[0];
assign y[3]=~s[2]&s[1]&s[0];
assign y[4]=s[2]&~s[1]&~s[0];
assign y[5]=s[2]&~s[1]&s[0];
assign y[6]=s[2]&s[1]&~s[0];
assign y[7]=s[2]&s[1]&s[0];
endmodule
```
## OUTPUT:
![321538441-2c430127-9fa0-4dbb-aeeb-1930978a8754](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/1838238f-56cf-409e-bc97-5762187067f5)


## ENCODER3:8:
![321538441-2c430127-9fa0-4dbb-aeeb-1930978a8754-1](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/5390c491-3a14-4db7-991a-35b54c17fbc3)


## MULTIPLEXER 8:1:

![321538505-81e886bb-97d6-4a51-aa2f-d7e6429f6525](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/c9855ddb-70fa-4f0f-a32c-64e2322a3b80)

## PROGRAM:
```
module Mux 8 1 (s0,s1,s2, i,y);
input [7:0]i;
input 50, s1,s2;
output y;
wire [7:0]w;
assign w[0]=(~s2) & (~sl) & (~50)&i[0];
assign w[1]=(~32)&(~51) & (50) &i [1];
assign w[2]=(~52) & (sl) & (~50)&i [2];
assign w[3]=(~52) & (51) & (50) &i [3];
assign w[4]=(s2) & (sl) & (~50)&i [4];
assign w[5]=(s2) & (sl) & (s0) &i [5];
assign w[6]=(52) & (51)&(~50)&i [6];
assign w[7]=(s2) & (51) & (s0)&i [7];
assign y=w[0][w[1] w[2] w[3] w[4] w[5] w[6] w[7];
endmodule
```
## OUTPUT:

![321538634-bb7f4511-0128-414b-9dba-b54a8fedb5ae](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/55f1eb59-23b1-4def-9360-a80f6dab9a24)

## DEMULTIPLEXER 1:8:

![321538727-ae62dd34-ad89-4413-9c09-5a86b5c1237b](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/1d1c425f-eb84-4fb3-bac3-05026ca130f9)

## PROGRAM:
```
module fa (a,b,c,sum, carry);
input a,b,c;
output sum, carry;
wire w1,w2,w3;
xor gl(wl,a,b);
xor g2 (w2,a,b);
xor g3 (sum, w1,c);
and (w3,c,w1);
or g5 (carry, w3,w2);
endmodule
```
## OUTPUT:

![321538896-d6b8fb93-d57c-4592-aff2-99b387590e9d](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/062d1def-4b20-4c3d-8f02-7fcf014f1c7e)

## COMPARATOR:

![321538951-ab00026f-7936-4353-b9e2-847bad0c7bff](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/da23834d-5eee-4ba7-a093-62c189ae7451)

## PROGRAM:
```
module comparator(a,b,l,g,e);
input [3:0]a,b;
output reg l,g,e;
always@(*)
begin
if(a>b)
begin
l=1'b0;
g=1'b1;
e=1'b0;
end
else if(a<b)
begin
l=1'b1;
g=1'b0;
e=1'b0;
end
else
begin
l=1'b0;
g=1'b0;
e=1'b1;
end
end
endmodule
```
## OUTPUT:

![321539020-263f8572-ecce-421e-a09f-0f252ee44691](https://github.com/Sachita02/VLSI-LAB-EXP-2/assets/162723490/855d1417-b810-465d-954e-5c12fa558e43)

## RESULT:
The simulate and sythesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using VIVADO is successfully verified.
