**Revised Lab 2 Directions**

  

**Overview**

In this lab, you will design and test a simpler version of a digital logic block—specifically one where the carry-in is always zero. This block is essentially a full adder without the need to handle a carry-in. You will create the appropriate logic using Sum of Products (SOP) expressions and implement your design in LTSpice. Once the initial block is working, you will design a second, even simpler block for use as the Least Significant Bit (LSB) cell (since its carry-in is guaranteed to be zero). You will document all steps for a complete report.

**1. Understand the Problem**

1. **Describe the Block**

• Clarify that this adder-like block does not require a carry-in input.

• State how it differs from a standard full adder (i.e., the carry-in is fixed to zero).

**2. Create Truth Tables**

2. **SUM Output**

• List all input combinations for the two input bits (A and B).

• Determine the SUM output bit for each combination.

3. **CARRY-OUT Output**

• Using the same input combinations (A and B), determine when the output carry bit is set.

  

You may show these two truth tables side-by-side or separately, as long as they are clear and complete.

**3. Derive Logic Expressions (SOP)**

4. **SUM Expression**

• Use the Sum of Products (SOP) method to derive the simplified Boolean expression that produces the SUM bit.

5. **CARRY-OUT Expression**

• Similarly, derive the SOP expression for the CARRY-OUT bit.

**4. Enter the Circuits into LTSpice**

6. **Implement SUM Circuit**

• Translate your SOP expression for SUM into logic gates within LTSpice.

7. **Implement CARRY-OUT Circuit**

• Translate your SOP expression for CARRY-OUT into LTSpice as well.

8. **Create a Symbol**

• Build a custom symbol (.asy file) to represent this combined block in LTSpice.

9. **Design a Test Schematic**

• Set up a new schematic that instantiates your custom block.

• Connect inputs and any necessary power/ground signals to facilitate simulation.

10. **Simulate and Verify**

• Run LTSpice simulations for all possible input combinations (00, 01, 10, 11).

• Capture screenshots or waveform outputs as proof of correct behavior.

11. **Backup Your Files**

• Save and back up your .asc (schematic) and .asy (symbol) files.

**5. Design a Simpler Block for the LSB**

12. **Understand the LSB Block**

• Since the least significant bit does not receive a carry-in (always zero), design a simplified circuit that handles only the two data inputs (A, B).

13. **Create a Truth Table**

• Show the truth table for this LSB block’s SUM and CARRY-OUT outputs (with carry-in assumed to be 0).

14. **Derive Logic Expression (SOP)**

• Use SOP to simplify and represent the LSB logic.

15. **Implement in LTSpice**

• Create the schematic, symbol, and testbench for this simpler LSB block.

• Confirm correct operation through simulation.

16. **Replace the Original LSB Block**

• Incorporate your new LSB design into the previously created multi-bit adder or test environment.

• Simulate again to ensure proper operation.

**6. Documentation & Submission**

17. **Complete Lab Report**

• Combine your work from Monday and Wednesday into a single, coherent report.

• Include:

• **Problem Description** (why the carry-in is zero and how the block is used)

• **Truth Tables** (for both the standard and simpler block)

• **SOP Derivations** (show the steps to reach the final Boolean expressions)

• **LTSpice Schematics & Symbols** (explain your design choices)

• **Simulation Outputs** (screenshots/waveforms for all input combinations)

• **Any Additional Observations** or notes on what you learned.

18. **Design Files**

• Submit or back up all LTSpice design files (.asc, .asy) associated with both the main block and the LSB block.

**Key Notes**

• Always clarify uncertainties by asking the instructor or peers.

• Document _every_ step thoroughly; your annotated steps form the core of your lab report.

• The final report is due on **Monday (2/3)**, combining the work from both lab sessions.

  

**End of Revised Directions**