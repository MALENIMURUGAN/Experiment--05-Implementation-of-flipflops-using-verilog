## NAME: MALENI.M
## REGISTER NAME: 212223040110
# Experiment--05-Implementation-of-flipflops-using-verilog
### AIM: To implement all the flipflops using verilog and validating their functionality using their functional tables
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### PROCEDURE:
1.	Using nand gates and wires construct sr flip flop.

2.Repeat same steps to construct JK,D,T flipflops.

3.Find Rtl logic and timing diagram for all flipflops.

4.end the program.

### THEORY:
### SR Flip-Flop
SR flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, SR latch operates with enable signal. The circuit diagram of SR flip-flop is shown in the following figure.
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/430604d5-3625-423c-8639-94daf517b307)
This circuit has two inputs S & R and two outputs Qtt & Qtt’. The operation of SR flipflop is similar to SR Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable. The following table shows the state table of SR flip-flop.
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/9cc13b12-b53c-411c-9ef4-c6f76248b347)
Here, Qtt & Qt+1t+1 are present state & next state respectively. So, SR flip-flop can be used for one of these three functions such as Hold, Reset & Set based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of SR flip-flop. Present Inputs Present State Next State
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/c95b5200-447a-44cf-98d1-238d9728f0c5)

By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. The three variable K-Map for next state, Qt+1t+1 is shown in the following figure.
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/47f96765-9a51-4c42-8879-5e7b033f4abc)

The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is Q(t+1)=S+R′Q(t)Q(t+1)=S+R′Q(t)

## PROGRAM:
```
module sr(S,R,clk,Q,Qbar);
input S,R,clk;
output reg Q;
output reg Qbar; 
initial Q=0;
initial Qbar=1;
always @(posedge clk)
begin
Q=S|((~R)&Q);
Qbar=R|((~S)&(Qbar));
end
endmodule
```
## RTL LOGIC FOR SR-FLIPFLOP:
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/f8ba3966-95aa-4a50-9cdb-a0a1cb95f430)

## TRUTH TABLE FOR SR-FLIPFLOP:
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/39c2e1af-bf98-4121-8153-b4e6f1a1d68b)
 
## TIMING DIAGRAM FOR SR-FLIPFLOP:
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/d103e121-0805-467d-98a1-e79fd0a21900)

## D Flip-Flop
D flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, D latch operates with enable signal. That means, the output of D flip-flop is insensitive to the changes in the input, D except for active transition of the clock signal. The circuit diagram of D flip-flop is shown in the following figure.
This circuit has single input D and two outputs Qtt & Qtt’. The operation of D flip-flop is similar to D Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable. The following table shows the state table of D flip-flop.

![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/8c46c8f2-18ca-4bb3-9663-f59df1ca5d4d)
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/601f6e50-d3e0-41f1-b780-55e18af66e7d)

Therefore, D flip-flop always Hold the information, which is available on data input, D of earlier positive transition of clock signal. From the above state table, we can directly write the next state equation as Qt+1t+1 = D
 
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/2acd3cb4-b2aa-4afb-ab47-e81687e6ac6c)

Next state of D flip-flop is always equal to data input, D for every positive transition of the clock signal. Hence, D flip-flops can be used in registers, shift registers and some of the counters.

## PROGRAM:
```
module d(d,clk,q,qbar);
input d,clk;
output q,qbar;
reg q,qbar;
always @(posedge clk)
begin
q=d;
qbar=~q;
end
endmodule
```
## RTL LOGIC FOR D-FLIPFLOP:
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/948b2484-55e2-44cd-92b2-1d3ec5422433)

## TRUTH TABLE FOR D-FLIPFLOP:
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/7f676be6-e212-4cb8-8450-4d52b0503d6b)

## TIMING DIAGRAM FOR D-FLIPFLOP:
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/bba79b3f-c23d-459b-8d75-558d89ab2f9e)

## JK Flip-Flop
JK flip-flop is the modified version of SR flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of JK flip-flop is shown in the following figure.
 ![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/72e7fbb5-b016-4fcf-8cd7-04825f01d8e6)

This circuit has two inputs J & K and two outputs Qtt & Qtt’. The operation of JK flip- flop is similar to SR flip-flop. Here, we considered the inputs of SR flip-flop as S = J Qtt’ and R = KQtt in order to utilize the modified SR flip-flop for 4 combinations of inputs. The following table shows the state table of JK flip-flop.
 ![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/dbe8a1c4-27b9-451b-81bf-c140d0c09511)

Here, Qtt & Qt+1t+1 are present state & next state respectively. So, JK flip-flop can be used for one of these four functions such as Hold, Reset, Set & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of JK flip-flop. Present Inputs Present State Next State
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/f9e501dd-2479-4841-8348-9002b44c479e)

By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. Three variable K-Map for next state, Qt+1t+1 is shown in the following figure.
 
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/f1fb9a1f-ddce-48fc-8b1d-2def71aa3371)

The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is Q(t+1)=JQ(t)′
+K′Q(t)Q(t+1)=JQ(t)′+K′Q(t)

## PROGRAM:
```
module jk(J,K,clk,Q,Qbar);
input J,K,clk;
output reg Q;
output reg Qbar;
initial Q=0;
initial Qbar=1;
always @(posedge clk)
begin
Q=(J&(~Q))|((~K)&Q);
Qbar=((~J)&(Qbar))|K&(~Qbar);
end
endmodule
```

## RTL LOGIC FOR JK-FLIPFLOP:
 ![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/7cc30d6e-175b-4608-963b-f38e498ec386)

## TRUTH TABLE FOR JK-FLIPFLOP:
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/e0770a20-4b21-43ff-a5d2-0b128b9615db)

## TIMING DIAGRAM FOR JK-FLIPFLOP:
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/9a59af17-bb29-4256-bdcf-0759b97b65a6)

## T Flip-Flop
T flip-flop is the simplified version of JK flip-flop. It is obtained by connecting the same input ‘T’ to both inputs of JK flip-flop. It operates with only positive clock
 
transitions or negative clock transitions. The circuit diagram of T flip-flop is shown in the following figure.
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/90264652-de88-434f-8727-03b3e97c9b78)

This circuit has single input T and two outputs Qtt & Qtt’. The operation of T flip-flop is same as that of JK flip-flop. Here, we considered the inputs of JK flip-flop as J = T and K = T in order to utilize the modified JK flip-flop for 2 combinations of inputs. So, we eliminated the other two combinations of J & K, for which those two values are complement to each other in T flip-flop. The following table shows the state table of T flip-flop.
Here, Qtt & Qt+1t+1 are present state & next state respectively. So, T flip-flop can be used for one of these two functions such as Hold, & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of T flip-flop. Inputs Present State Next State
![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/1260249b-9a90-4e01-8695-264ce9885610)


From the above characteristic table, we can directly write the next state equation as Q(t+1)=T′Q(t)+TQ(t)′ ⇒Q(t+1)=T⊕Q(t)
 
## PROGRAM:
```
module t(clk,T,q,qbar);
input clk,T;
output q,qbar; reg q,qbar;
always @(posedge clk)
begin q=(T&~q)|(~T&q); qbar=~q;
end
endmodule
```

## RTL LOGIC FOR T-FLIPFLOP:

![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/208801d0-20fc-4727-845d-6e50dbb88ee9)

## TRUTH TABLE FOR T-FLIPFLOP:
 ![image](https://github.com/MALENIMURUGAN/Experiment--05-Implementation-of-flipflops-using-verilog/assets/144870675/69b143e6-665e-4795-b39a-d887d070c628)
## RESULTS:
This implementation of SR,JK,D and T flipflops using nand gates are done successfully.










