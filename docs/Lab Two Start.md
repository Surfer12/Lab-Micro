Below is a suggested approach for working through each of the lab steps. The goal is to ensure you (a) understand exactly what is being built (the single‐bit “adder” block), (b) know how to derive the required logic equations, and (c) can implement and test them in LTSpice (or a similar tool). At the very end, you will simplify the design for the LSB case where \(C_{\mathrm{in}}=0\). 
[[Numbers, data, gates, truth tables, and other digital system design stuff. LTSpice videos.]]

[[Breakdown of the material for Week 2]]

[[Homework due Monday for MicroArch Assignment 1]]
---

## 1. **Understand the Block You’re Designing**

- **Full single-bit adder**  
  - Inputs: \(A\), \(B\), and \(C_{\mathrm{in}}\).  
  - Outputs: \(\text{SUM}\) and \(\text{COUT}\).  

  Mathematically, the adder forms:  
  \[
      A + B + C_{\mathrm{in}} 
      \; \longrightarrow \; 
      \text{SUM}, \quad \text{COUT}.
  \]
  In base-2 (binary), a carry occurs any time the sum in a bit-column is 2 or greater.

- **Special LSB version**  
  - For the least significant bit (LSB), the carry-in \(\;C_{\mathrm{in}}\) is effectively 0.  
  - This simplifies the logic, so you can think of it almost like a “half adder” (\(A+B\)).  

---

## 2. **Create the Truth Table**

You will actually need **two truth tables**:

1. **Full single-bit adder** (with \(C_{\mathrm{in}}\) as an input)  
2. **LSB version** (ignoring \(C_{\mathrm{in}}\))

### 2.1 Full Single-Bit Adder Truth Table

| \(A\) | \(B\) | \(C_{\mathrm{in}}\) | \(\text{SUM}\) | \(\text{COUT}\) |
|:----:|:----:|:---------:|:---------:|:-----------:|
|  0   |  0   |     0     |     0     |      0      |
|  0   |  0   |     1     |     1     |      0      |
|  0   |  1   |     0     |     1     |      0      |
|  0   |  1   |     1     |     0     |      1      |
|  1   |  0   |     0     |     1     |      0      |
|  1   |  0   |     1     |     0     |      1      |
|  1   |  1   |     0     |     0     |      1      |
|  1   |  1   |     1     |     1     |      1      |

### 2.2 LSB Version Truth Table (\(C_{\mathrm{in}}=0\))

Here, you only have two inputs \((A, B)\). The carry in is fixed at 0, so:

| \(A\) | \(B\) | \(\text{SUM}\) | \(\text{COUT}\) |
|:----:|:----:|:---------:|:-----------:|
|  0   |  0   |     0     |      0      |
|  0   |  1   |     1     |      0      |
|  1   |  0   |     1     |      0      |
|  1   |  1   |     0     |      1      |

*(Notice for the LSB block, \(\text{SUM} = A \oplus B\) and \(\text{COUT} = A \cdot B\).)*

---

## 3. **Find the Logic (Sum of Products Form)**

From the full single‐bit adder table, you can derive standard SOP (sum-of-products) equations:

1. **SUM** is logically \(A \oplus B \oplus C_{\mathrm{in}}\).  
   - In SOP form, you can write it out by picking out the rows where SUM=1 and combining them.  

2. **CARRY-OUT** is 1 if at least two of \(\{A,B,C_{\mathrm{in}}\}\) are 1.  
   - One common SOP form is 
     \[
       \text{COUT} = A B \;+\; A C_{\mathrm{in}} \;+\; B C_{\mathrm{in}}.
     \]
   - Or you can derive it directly from the truth table.

For the **LSB** (carry-in = 0), the expressions simplify to the well-known half-adder:

\[
\begin{aligned}
\text{SUM}_{\mathrm{LSB}} &= A \oplus B, \\
\text{CARRY-OUT}_{\mathrm{LSB}} &= A \cdot B.
\end{aligned}
\]

---

## 4. **Enter the Circuits into LTSpice**

1. **Construct the SUM and CARRY-OUT subcircuits** using logic gates corresponding to your SOP forms.  
2. **Keep them together as a single schematic** that implements the 1-bit adder.  
3. **Label inputs** (A, B, \(C_{\mathrm{in}}\)) and outputs (\(\text{SUM}\), \(\text{COUT}\)).

---

## 5. **Make a Symbol for the Block**

- In LTSpice, you typically create a top‐level schematic (the adder) and then turn it into a reusable symbol \(*.asy*\).  
- Make sure you have the pins named correctly (A, B, Cin, Sum, Cout).

---

## 6. **Make a New Schematic to Test the Block**

- Create a **testbench** schematic.  
- Place your new adder symbol and connect all possible combinations of \(A, B, C_{\mathrm{in}}\) (through voltage sources or logic-level sources).  
- Probe \(\text{SUM}\) and \(\text{COUT}\) in simulation.

---

## 7. **Simulate for All Possible Inputs**

- Run a transient analysis where \(A\) and \(B\) (and \(C_{\mathrm{in}}\) if relevant) step through 0/1.  
- Capture screenshots of waveforms.  
- Verify that for each combination of \(A, B, C_{\mathrm{in}}\), your outputs match your truth table.

*(This becomes part of your lab report—show that the schematic’s outputs match the theoretical truth table.)*

---

## 8. **Simplify for the LSB Block**

Now that you’ve verified the full 1-bit adder, **design a simpler block** where \(C_{\mathrm{in}} = 0\). Steps:

4. **Understand** that for the LSB, we don’t need \(C_{\mathrm{in}}\) at all.  
5. **Create the (A,B) → (SUM, CARRY) truth table** (already shown above).  
6. **Derive logic** (which is basically \( \text{SUM} = A \oplus B,\;\; \text{CARRY} = A \cdot B \)).  
7. **Enter the new circuit** into LTSpice.  
8. **Make a symbol** for the new LSB.  
9. **Test** it (simulate again).  

Finally, **replace the LSB block** in your full 4-bit adder chain with this simpler half-adder for the least significant position. Confirm that the entire adder still works correctly when you feed it 4-bit input signals.

---

## 9. **Putting It All Together in Your Report**

Your final report should include:

10. **Design Rationale**  
   - Short explanation of what a single-bit adder is doing.  
   - Why we can ignore \(C_{\mathrm{in}}\) for the LSB.  

11. **Truth Tables**  
   - Full adder (3 inputs: \(A,B,C_{\mathrm{in}}\)).  
   - LSB half-adder (2 inputs: \(A,B\)).  

12. **Derivations of SOP**  
   - Show how you obtained \(\text{SUM}\) and \(\text{COUT}\) from each truth table.  
   - Show simplified Boolean expressions or final gate‐level equations.  

13. **Schematics and Symbols**  
   - Screenshots or schematics for your circuit in LTSpice.  
   - The *.asc and *.asy files (these are typically the schematic and symbol files for LTSpice).  

14. **Simulation Results**  
   - Waveforms (screen captures) confirming that the outputs match your predicted truth table entries.  
   - A quick note verifying each combination works.  

15. **Replacement of the LSB**  
   - Show your final 4-bit cascade with the simplified LSB block.  
   - Provide any further simulation waveforms that confirm correct operation.  

---

### Why “Subtracting the Base” Appears in Binary Addition

From your notes, you see talk of “sum becomes 3 then subtracting the base (2) => final sum bit 1 and a carry 1.” In binary, *any time the temporary sum in one bit-position is 2 or 3* (i.e., in decimal terms, out of that single column of addition), you “subtract 2” from the sum bits and set a carry to the next column.

- In binary, *base = 2*.  
- A temporary sum of 2 in one bit-column is “10” in binary ⇒ sum bit = 0, carry = 1.  
- A temporary sum of 3 in one bit-column is “11” in binary ⇒ sum bit = 1, carry = 1.  

Hence the notion “if sum \(\geq\) base, subtract base and set carry to 1.”

---

## Takeaways

16. **One-Bit Adder**: Standard “textbook” circuit with \(A,B,C_{\mathrm{in}}\to \{\text{SUM}, \text{COUT}\}\).  
17. **LSB (Half-Adder)**: Drops \(C_{\mathrm{in}}\) since it’s always zero.  
18. **Multi-Bit Cascade**: Chain single-bit adders from LSB to MSB, passing \(C_{\mathrm{out}}\) of each stage to the \(C_{\mathrm{in}}\) of the next.  

Follow the lab instructions step by step—truth tables, SOP logic, LTSpice schematic, symbol creation, and then final testing. Documenting each step with screenshots and brief explanations is typically exactly what your instructor is looking for in the final submission.