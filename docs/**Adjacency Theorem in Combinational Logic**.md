Below is a revised version of your Notion page content, reorganized for clarity and consistency while preserving the original technical insights:

**Adjacency Theorem in Combinational Logic**

**Core Principle:**

_If changing an input doesn’t change the output, then that input is irrelevant to the function._

This concept—known as the **Adjacency Theorem**—forms the basis for many logic minimization techniques, such as those used in Karnaugh maps (K-maps).

**Example 1: 3-Bit Binary Combinations (x₂, x₁, x₀)**

**Table: 3-Bit Combinations**

|**x₂**|**x₁**|**x₀**|**Decimal Value**|
|---|---|---|---|
|0|0|0|0|
|0|0|1|1|
|0|1|0|2|
|0|1|1|3|
|1|0|0|4|
|1|0|1|5|
|1|1|0|6|
|1|1|1|7|

**Explanation:**

• **Bit Positions:**

• **x₂:** Most Significant Bit (MSB)

• **x₀:** Least Significant Bit (LSB)

• **Decimal Conversion Formula:**

• Each row represents a unique 3-bit combination, useful for understanding binary counting and digital circuit design.

**Example 2: 3-Bit Binary Combinations with Alternative Labeling**

**Initial Version: (y₁, y₂, y₃)**

**Table: 3-Bit Combinations (y₁, y₂, y₃)**

|**y₁**|**y₂**|**y₃**|**Decimal Value**|
|---|---|---|---|
|0|0|0|0|
|0|0|1|1|
|0|1|0|2|
|0|1|1|3|
|1|0|0|4|
|1|0|1|5|
|1|1|0|6|
|1|1|1|7|

**Explanation:**

• **Bit Positions:**

• **y₁:** Treated as the MSB

• **y₃:** Treated as the LSB

• **Decimal Conversion:** Calculated similarly using the binary-to-decimal formula.

• This table serves as another reference for binary counting and logic design.

**Revised Version: Consistent Labeling (y₂, y₁, y₀)**

To align with Example 1, the bit labels are revised so that the leftmost bit is the MSB.

**Table: 3-Bit Combinations (y₂, y₁, y₀)**

|**y₂**|**y₁**|**y₀**|**Decimal Value**|
|---|---|---|---|
|0|0|0|0|
|0|0|1|1|
|0|1|0|2|
|0|1|1|3|
|1|0|0|4|
|1|0|1|5|
|1|1|0|6|
|1|1|1|7|

**Explanation:**

• **Bit Positions:**

• **y₂:** Most Significant Bit (MSB)

• **y₀:** Least Significant Bit (LSB)

• **Decimal Calculation:**

• Consistent labeling makes it easier to compare adjacent rows, which is crucial when applying the adjacency theorem for logic simplification.

**Applying the Adjacency Theorem in Logic Minimization**

When only one bit changes between two adjacent rows—and the output remains unchanged—the changing bit is inconsequential. This insight is used in logic minimization:

• **Step 4 (SOP/K-map Example):**

Identify adjacent minterms in a Karnaugh map where only one input variable changes. If this change does not affect the output, you can combine these terms to simplify the Sum of Products (SOP) expression.

By using these tables and explanations, you can effectively apply the adjacency theorem to streamline combinational logic designs, reduce redundancy, and optimize digital circuits.