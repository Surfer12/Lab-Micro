## Lab Report Requirements

Your lab report should include comprehensive documentation for both parts:

- **Problem Description & Function Explanation:** Describe the function of each block.
- **Truth Tables:** Present truth tables for all outputs.
- **Derived Logic Expressions:** Show the logic expressions derived (using SOP or equivalent).
- **LTSpice Schematics:** Include schematics for both the circuit designs and test benches.
- **Block Symbols:** Provide images or descriptions of the symbols created.
- **Simulation Results:** Attach screenshots of simulation outputs for every input combination.
- **File Backup Confirmation:** Confirm that all design files (`*.asc` and `*.asy`) are properly backed up.

> **Note:** This complete documentation, along with your work from Wednesday's lab, forms the full Lab Two report due on Monday, 2/3.

---

# Digital Logic Circuit Analysis: "Input − 2" (3-Bit 2’s-Complement)

Below is a detailed, step-by-step analysis of a circuit that computes “input − 2” for a 3-bit input.

## Core Design Problem

Given a 3-bit input (X2X1X0)(X2​X1​X0​), produce a 3-bit output (Y2Y1Y0)(Y2​Y1​Y0​) such that:

Output=Input−2Output=Input−2

_Note:_ When the result is negative, it is represented in 3-bit 2’s-complement.  
For example:

- 0−20−2 (decimal) is represented as 110110 (which stands for −2−2 in 3-bit 2’s-complement).

---

## 1. Construct the Truth Table

List all 8 possible input combinations and calculate “input − 2” in 3-bit 2’s-complement:

|Decimal|X2X1X0X2​X1​X0​|Input−2Input−2|Y2Y1Y0Y2​Y1​Y0​ (3-bit 2’s-complement)|
|---|---|---|---|
|0|000|−2−2|110|
|1|001|−1−1|111|
|2|010|0|000|
|3|011|1|001|
|4|100|2|010|
|5|101|3|011|
|6|110|4|100|
|7|111|5|101|

---

## 2. Fill the Karnaugh Maps (K-Maps)

For a 3-bit input, the K-map is typically arranged as a 2×4 grid using Gray code order.

**Layout:**

- **Columns:** Represent X2X1X2​X1​ in Gray code order: 0000, 0101, 1111, 1010.
- **Rows:** Represent X0X0​ with values 00 and 11.

Since there are 3 outputs (Y2Y2​, Y1Y1​, Y0Y0​), you create a separate K-map for each.

### (a) K-Map for Y2Y2​

- **Observation:** Y2=1Y2​=1 for inputs with decimal values {0,1,6,7}{0,1,6,7}, corresponding to:
    
    - 000000, 001001, 110110, 111111.
- **Grouping:** By placing 1’s in these cells and grouping adjacent ones (covering two adjacent columns for both X0=0X0​=0 and X0=1X0​=1), the simplified expression is:
    
    Y2=X2′X1′+X2X1Y2​=X2′​X1′​+X2​X1​
    
    This is the equivalence function (X2↔X1X2​↔X1​); Y2Y2​ is 1 when X2X2​ and X1X1​ are the same.
    

### (b) K-Map for Y1Y1​

- **Observation:** Y1=1Y1​=1 for inputs with decimal values {0,1,4,5}{0,1,4,5}, corresponding to:
    
    - 000000, 001001, 100100, 101101.
- **Simplification:** All these cases have X1=0X1​=0. Thus, the simplified expression is:
    
    Y1=X1′Y1​=X1′​

### (c) K-Map for Y0Y0​

- **Observation:** Y0=1Y0​=1 for inputs with decimal values {1,3,5,7}{1,3,5,7}, exactly when:
    
    - X0=1X0​=1.
- **Simplification:** Therefore, the expression is:
    
    Y0=X0Y0​=X0​

---

## 3. Final Simplified Logic

Combine the derived expressions to implement the circuit:

Y2=X2′X1′+X2X1(Equivalence of X2 and X1),Y1=X1′,Y0=X0.Y2​Y1​Y0​​=X2′​X1′​+X2​X1​=X1′​,=X0​.​(Equivalence of X2​ and X1​),

This circuit computes “input – 2” in 3-bit 2’s-complement arithmetic.

---

## Takeaways

1. **K-Map Setup:**
    - Label rows and columns in Gray code to ensure adjacent cells differ by only one bit.
2. **Filling Outputs:**
    - For every input, compute “input – 2” in 3-bit 2’s-complement and fill in the K-map for each output bit.
3. **Grouping and Simplifying:**
    - Group adjacent ones in the K-map to derive minimal Sum of Products (SOP) expressions.
    - Key patterns:
        - Y2Y2​ is the equivalence of X2X2​ and X1X1​.
        - Y1Y1​ simplifies to X1‾X1​​.
        - Y0Y0​ simplifies to X0X0​.

---