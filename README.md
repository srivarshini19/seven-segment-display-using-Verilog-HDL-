# Seven-Segment Display Driver using Verilog HDL

## Aim  
To design and simulate a seven-segment display driver using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment. The objective is to implement the logic that converts a 4-bit binary input into the corresponding 7-segment display output for the digits 0 to 9.

## Apparatus Required  
- **Vivado 2023.1**  

## Procedure  

### 1. Launch Vivado 2023.1  
- Open Vivado and create a new project.  

### 2. Design the Verilog Code  
- Write the Verilog code for the seven-segment display, defining the logic that maps a 4-bit binary input to the corresponding segments (a to g) of the display.  

### 3. Create the Testbench  
- Write a testbench to simulate the seven-segment display behavior. The testbench should apply various 4-bit input values and monitor the corresponding output on the seven-segment display.  

### 4. Create the Verilog Files  
- Create both the design module and the testbench in the Vivado project.  

### 5. Run Simulation  
- Run the behavioral simulation to verify the output. Ensure the seven-segment display behaves correctly for binary inputs **0000 to 1001** (decimal **0 to 9**).  

### 6. Observe the Waveforms  
- Analyze the output waveforms in the simulation window, and verify that the correct segments light up for each digit.  

### 7. Save and Document Results  
- Capture screenshots of the waveform and save the simulation logs. These will be included in the lab report.  

---
## Logic Diagram

![image](https://github.com/user-attachments/assets/e561cdb5-b1b0-42d0-94f5-e1efaec9704c)

![image](https://github.com/user-attachments/assets/dc32254e-f88d-471a-a2ba-e4ec5eb3fc11)

![image](https://github.com/user-attachments/assets/a8a8921e-0a37-4697-86d8-0c43cd8aef5a)

## Verilog Code for Seven-Segment Display  

```verilog
module BCD_TO_7SEG (
    input  wire [3:0] binary_input,
    output reg  [6:0] seg_output
);
    always @(*) begin
        case (binary_input)
            4'd0: seg_output = 7'b1111110;
            4'd1: seg_output = 7'b0110000;
            4'd2: seg_output = 7'b1101101;
            4'd3: seg_output = 7'b1111001;
            4'd4: seg_output = 7'b0110011;
            4'd5: seg_output = 7'b1011011;
            4'd6: seg_output = 7'b1011111;
            4'd7: seg_output = 7'b1110000;
            4'd8: seg_output = 7'b1111111;
            4'd9: seg_output = 7'b1111011;
            default: seg_output = 7'b0000000;
        endcase
    end
endmodule

```
## Testbench for Seven-Segment Display
```verilog
`timescale 1ns / 1ps
module BCD_TO_7SEG_tb;
    reg [3:0] binary_input;
    wire [6:0] seg_output;

    BCD_TO_7SEG uut (
        .binary_input(binary_input),
        .seg_output(seg_output)
    );

    initial begin
        binary_input = 4'd0;
        #10 binary_input = 4'd1;
        #10 binary_input = 4'd2;
        #10 binary_input = 4'd3;
        #10 binary_input = 4'd4;
        #10 binary_input = 4'd5;
        #10 binary_input = 4'd6;
        #10 binary_input = 4'd7;
        #10 binary_input = 4'd8;
        #10 binary_input = 4'd9;
        #10 $stop;
    end

    initial begin
        $monitor("Time=%0t | binary_input=%b | seg_output=%b",
                 $time, binary_input, seg_output);
    end
endmodule
```
## Simulated Output

<img width="1446" height="805" alt="EXP 2" src="https://github.com/user-attachments/assets/42e5d078-b140-4710-8762-230cd801c781" />

---

## Conclusion
In this experiment, a seven-segment display driver was successfully designed and simulated using Verilog HDL. The simulation results confirmed that the display correctly represented the digits 0 to 9 based on the 4-bit binary input. The testbench effectively verified the functionality of the seven-segment display by applying various input combinations and observing the corresponding segment outputs.

This experiment highlights how Verilog HDL can be used to control hardware components like a seven-segment display in digital systems.
