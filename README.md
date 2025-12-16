### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**

4-bit Synchronous UP Counter (JK Flip-Flops)

1.Open Quartus II → New Project → Block Diagram/Schematic File (.bdf).
2.Insert 4 JK flip-flops and connect one common clock to all CLK pins.
3.Connect J = K = 1 (Vcc) for the LSB flip-flop (FF0).
4.Connect Q0 → J1, K1; use AND gates so that
             J2 = K2 = Q0 · Q1
             J3 = K3 = Q0 · Q1 · Q2
5.Compile, assign clock pin, and run simulation to see binary count up.

4-bit Synchronous DOWN Counter (JK Flip-Flops)

1.Open Quartus II → New Project → Block Diagram/Schematic File (.bdf).
2.Insert 4 JK flip-flops and connect one common clock to all CLK pins.
3.Connect J = K = 1 (Vcc) for the LSB flip-flop (FF0).
4.Use NOT gates + AND gates so that
                  J1 = K1 = Q0̅
                  J2 = K2 = Q0̅ · Q1̅
                  J3 = K3 = Q0̅ · Q1̅ · Q2̅
5.Compile, assign clock pin, and run simulation to see binary count up.


**PROGRAM**

```
UP COUNTER
module ex11(out,clk,rst);
input clk,rst;
output reg [3:0]out;
always @ (posedge clk)
begin
   if(rst)
     out<=0;
   else 
     out <= out+1;
end
endmodule

DOWN COUNTER
module ex12(out,clk,rst);
input clk,rst;
output reg [3:0]out;
always @ (posedge clk)
begin
   if(rst)
     out<=0;
   else 
     out <= out-1;
end
endmodule
```

Developed by:R.MOHAMMED ZUBAIR RegisterNumber:25017722

**RTL LOGIC UP COUNTER**

UP counter
<img width="1475" height="652" alt="image" src="https://github.com/user-attachments/assets/e680e5c8-9791-4667-aa55-b5d1680ea810" />

DOWN counter
<img width="1280" height="523" alt="image" src="https://github.com/user-attachments/assets/ea383046-44c9-4a12-9e81-a8e09ae7c495" />

**TIMING DIAGRAM FOR IP COUNTER**

UP  counter
<img width="1501" height="434" alt="image" src="https://github.com/user-attachments/assets/c502ce64-3aa4-422d-a1d8-45bd5c7fdfa4" />

DOWN counter
<img width="1498" height="423" alt="image" src="https://github.com/user-attachments/assets/7402c374-c165-436c-91f8-e516f39416f8" />

**TRUTH TABLE**

SYNCHRONOUS-UP-COUNTER:
| Clock Pulse | Q2 | Q1 | Q0 | Decimal Count |
| :--- | :---: | :---: | :---: | :---: |
| *Initial* | 0 | 0 | 0 | 0 |
| *1* | 0 | 0 | 1 | 1 |
| *2* | 0 | 1 | 0 | 2 |
| *3* | 0 | 1 | 1 | 3 |
| *4* | 1 | 0 | 0 | 4 |
| *5* | 1 | 0 | 1 | 5 |
| *6* | 1 | 1 | 0 | 6 |
| *7* | 1 | 1 | 1 | 7 |
| *8 (reset)* | 0 | 0 | 0 | 0 |

SYNCHRONOUS-DOWN-COUNTER:
| Clock Pulse | Q2 | Q1 | Q0 | Decimal Count |
| :--- | :---: | :---: | :---: | :---: |
| *Initial* | 0 | 0 | 0 | 7 |
| *1* | 0 | 0 | 1 | 6 |
| *2* | 0 | 1 | 0 | 5 |
| *3* | 0 | 1 | 1 | 4 |
| *4* | 1 | 0 | 0 | 3 |
| *5* | 1 | 0 | 1 | 2 |
| *6* | 1 | 1 | 0 | 1 |
| *7* | 1 | 1 | 1 | 0 |
| *8 (reset)* | 0 | 0 | 0 | 7 |

**RESULTS**

Thus,To implement 4 bit synchronous up counter and validate functionality.
