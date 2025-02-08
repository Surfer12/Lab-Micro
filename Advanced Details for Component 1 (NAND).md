Input --[NAND (1-bit)]--> --[NAND (1-bit)]--> --[XNOR (1-bit)]--> Output

--- Advanced Details for Component 1 (NAND) ---
Truth Table:
A B | NAND
0 0 | 1
0 1 | 1
1 0 | 1
1 1 | 0

K-map:
      B=0   B=1
A=0:   1     1
A=1:   1     0

SOP Expression:
Output = A'B' + A'B + AB'