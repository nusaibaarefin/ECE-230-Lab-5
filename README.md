# Lab 05 - Combinatorial Logic

In this lab, we learned about real-world applications of digital logic, how to assemble Verilog modules, and how the constraints file maps inputs and outputs to physical FPGA pins.

## Rubric

| Item | Description | Value |
| ---- | ----------- | ----- |
| Summary Answers | Your writings about what you learned in this lab. | 25% |
| Question 1 | Your answers to the question | 25% |
| Question 2 | Your answers to the question | 25% |
| Question 3 | Your answers to the question | 25% |

## Name

Nusaiba Arefin  
Tassen Raihan Trima

## Lab Summary

In this lab, we learned how to design and connect combinational logic circuits using Verilog. We created two separate logic modules and connected them together using a top-level module.

We also used truth tables and K-maps to understand and simplify Boolean expressions. The output of Circuit A was connected to input A of Circuit B, which showed how separate Verilog modules can be combined into a larger system.

We also learned how the constraints file maps the switches and LEDs used in the Verilog code to the actual physical pins on the Basys 3 FPGA board.

## Lab Questions

### 1 - Explain the role of the Top Level file.

The top-level file is the main module that connects all of the smaller Verilog modules together. It defines how the inputs and outputs of the complete design are connected.

In this lab, `top.v` connected the FPGA switches to Circuit A and Circuit B. It also connected the output of Circuit A to input A of Circuit B. The outputs of the two circuits were then connected to `led[0]` and `led[1]`.

### 2 - Explain the function of the Constraints file.

The constraints file tells Vivado which physical FPGA pins correspond to the inputs and outputs used in the Verilog code.

For example, `sw[0]` in the Verilog code must be connected to the physical pin used by switch 0 on the Basys 3 board. The constraints file provides this mapping.

In this lab, we uncommented the constraint lines for `sw[0]` through `sw[6]` and `led[0]` and `led[1]` so that the design used the correct switches and LEDs on the board.

### 3 - Was the selection of Minterm and Maxterm correct for each circuit? What would you have chosen?

The selections were valid because both minterms and maxterms can be used to represent Boolean functions. However, one form may be easier depending on the number of 1s and 0s in the truth table.

For Circuit A, there were only four rows where the output was 1 and twelve rows where the output was 0. Because of this, minterms would have been easier to work with than maxterms.

Using a K-map, Circuit A simplified to:

`Y = ~A & D`

For Circuit B, there were eight rows where the output was 1 and eight rows where the output was 0, so either minterms or maxterms would be reasonable.

Using a K-map, Circuit B simplified to:

`Y = (~C & ~D) | (A & B) | (B & ~D)`

Therefore, we would have chosen minterms for Circuit A because there were fewer 1s to represent. For Circuit B, minterms were a reasonable choice because the number of 1s and 0s was equal.
