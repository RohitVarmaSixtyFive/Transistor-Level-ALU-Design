# VLSI - ALU Design

## Circuit Design Details

The implemented ALU circuit includes logic gates and multiplexers for various operations controlled by select inputs. A 2:4 decoder manages operation selection, directing the 4-bit inputs by the enable line. Modules such as the adder, subtractor, comparator, and AND gate operate based on the enable signal and select inputs, ensuring accurate 4-bit addition, subtraction, comparison, and ANDing.

## Adder-Subtractor

The ALU features a fast adder and subtractor using a carry-lookahead adder, which speeds up calculations. Subtraction is performed with an XOR gate, assuming 2's complement numbers. The ALU can add or subtract four numbers at once, enhancing versatility. This is achieved using the same fast adder design and a "Mode" input, enabling a wider range of efficient calculations.

## Comparator

The comparator module analyzes four-bit inputs to determine if they are equal, greater, or less than each other by comparing individual bits. The output is valuable for decision-making in various applications.

## AND Block

This module performs the AND operation on each bit of the two four-bit input values.

## Verilog Implementation

The ALU was implemented using a modular design in Verilog, with individual modules for each circuit block. An enable block is shared for the Adder and Subtractor due to their common operation. All functions (modules) were called in the testbench, and the output was saved in a VCD file for viewing in GTKWave.

## Common Mistakes and Solutions

1. **Comparator Enable Issue**: The output for "equal to" was always 1 when the enable for the comparator was off. This was corrected by ANDing with the enable signal.
2. **Irregular Outputs**: Pulse inputs caused confusion, and some modules were not grounded, leading to incorrect outputs.
3. **Segmentation Fault**: Connecting multiple wires with different labels caused segmentation faults.
4. **Overlapping Wires**: This caused errors and a series of incorrect outputs.

## Delay Analysis

A Python script was used to iteratively run and analyze the circuits, determining delays for all inputs and outputs. Delays can be caused by propagation delay, component speed, and capacitance/inductance effects, which slow down electrical signals.

## Critical Path

The critical path in the ALU was identified by calculating the maximum delay using a Python script. The critical path, from the inputs to the output of the adder-subtractor module, represents the most complex calculations. Addressing delays in this path optimizes the overall ALU performance.

## Conclusion

The VLSI Final Project successfully designed and implemented an ALU capable of accurate 4-bit addition, subtraction, comparison, and ANDing operations. Rigorous simulations with Verilog HDL and NgSpice validated the design, and the physical layout was simulated using MAGIC. A thorough delay analysis identified the critical path, with improvements promising to enhance overall performance. This project demonstrates the ability to create a functional and efficient circuit, making the ALU a valuable component in digital systems.
