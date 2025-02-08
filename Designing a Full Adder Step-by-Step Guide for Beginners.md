[[Design Template for Building Your Own Adders]]
[[Further Reading and Resources]]
1. **Step-by-Step Guide**: This will include detailed explanations and worked-out examples covering conceptualization, truth table creation, K-map simplification, LTSpice implementation, symbol creation, testing, and cascading to a 4-bit adder.
2. **Template for Reference**: A structured template that users can follow for their own designs.
3. **High-Level Summary with Further Reading**: A condensed overview with links to relevant resources, including the referenced RISC-V book and other high-quality materials.

I will let you know when the research is ready.

# Designing a Full Adder: Step-by-Step Guide for Beginners

## Step-by-Step Guide with Worked Examples

### Conceptualizing the Full Adder  
A **full adder** is a fundamental digital circuit that computes the sum of three input bits: two significant bits (often called A and B) and a carry-in (Cin) from a previous addition ([
            LTspice Wizardry: Crafting Full Adder for Digital Circuits!
        ](https://www.digikey.com/en/maker/tutorials/2024/ltspice-wizardry-crafting-a-full-adder-for-digital-circuits#:~:text=A%20full%20adder%20is%20a,and%20other%20complex%20digital%20circuits)). It produces a one-bit **Sum (S)** output and a one-bit **Carry-out (Cout)**. In essence, the full adder adds A, B, and Cin just like ordinary binary addition:
- **Sum (S)** represents the least significant bit of A + B + Cin.
- **Carry-out (Cout)** represents the carry bit that is produced by this addition, which can be forwarded into the next higher bit position.  

Full adders build upon **half adders** (which add only two bits without a carry-in) to handle that third input (Cin). They are crucial for constructing multi-bit adders: by chaining full adders, we can add binary numbers of arbitrary length (e.g. 4-bit, 8-bit adders, etc.) ([
            LTspice Wizardry: Crafting Full Adder for Digital Circuits!
        ](https://www.digikey.com/en/maker/tutorials/2024/ltspice-wizardry-crafting-a-full-adder-for-digital-circuits#:~:text=A%20full%20adder%20is%20a,and%20other%20complex%20digital%20circuits)). Before diving into design, remember these key properties of a full adder’s logic: the sum output is 1 whenever an *odd* number of the inputs are 1, and the carry-out is 1 whenever *at least two* of the inputs are 1 ([](https://ece.mst.edu/media/academic/ece/documents/coursenotes/cpe2211computerengineeringlab/cpe2211-fall2024/Hierarchical%20Design%20of%20a%20Four%20Bit%20Adder.pdf#:~:text=A%20logic%20diagram%20for%20a,This)). This intuition will align with the truth table and Boolean expressions we derive next.

### Constructing the Truth Table  
The truth table defines how the outputs (Sum and Cout) respond to every combination of inputs (A, B, Cin). With three binary inputs, there are 2^3 = 8 possible input combinations. Below is the full adder truth table:

| **A** | **B** | **Cin** | **Sum (S)** | **Carry-out (Cout)** |
|:-----:|:-----:|:-------:|:-----------:|:--------------------:|
| 0     | 0     | 0       | 0           | 0                    |
| 0     | 0     | 1       | 1           | 0                    |
| 0     | 1     | 0       | 1           | 0                    |
| 0     | 1     | 1       | 0           | 1                    |
| 1     | 0     | 0       | 1           | 0                    |
| 1     | 0     | 1       | 0           | 1                    |
| 1     | 1     | 0       | 0           | 1                    |
| 1     | 1     | 1       | 1           | 1                    |

This table can be read as follows: for example, when A=1, B=1, Cin=0, the sum is 0 and carry-out is 1 (because two inputs are 1, producing a carry) ([notes1-2.dvi](https://www.classe.cornell.edu/~ib38/teaching/p360/lectures/wk09/l25/notes2.pdf#:~:text=sum%20of%20the%20i%20%2B,1%201%201%201%201)). When all three inputs are 1 (last line), the binary sum 1+1+1 = 11₂ (which is 3 in decimal) produces a sum bit of 1 and a carry-out of 1, matching the table. You can verify that the Sum column has 1s for exactly those cases where an odd number of inputs are 1, and Cout is 1 for cases where two or three inputs are 1 ([](https://ece.mst.edu/media/academic/ece/documents/coursenotes/cpe2211computerengineeringlab/cpe2211-fall2024/Hierarchical%20Design%20of%20a%20Four%20Bit%20Adder.pdf#:~:text=A%20logic%20diagram%20for%20a,This)). This correspondence will guide our Boolean simplification.

### Deriving Boolean Expressions (K-Map Simplification)  
Using the truth table, we derive simplified Boolean expressions for **Sum** and **Carry-out**. A Karnaugh Map (K-Map) helps minimize the logic by grouping adjacent 1s in the truth table output columns. We create separate K-maps for S and Cout (each a 3-variable map, with variables A, B, Cin):

- **For Sum (S)**: Mark 1s for input combinations where Sum=1 (from the table). If we group those 1s optimally, we find the Sum expression simplifies to an XOR of all three inputs:  
  **\[Sum = A ⊕ B ⊕ Cin\]** ([notes1-2.dvi](https://www.classe.cornell.edu/~ib38/teaching/p360/lectures/wk09/l25/notes2.pdf#:~:text=With%20Cini%20%3D%200%2C%20we,1%200%201%201%201)).  
  In other words, the sum bit is 1 if an odd number of A, B, Cin are 1, which is exactly the XOR logic. (This matches our earlier intuition that Sum is 1 for inputs counts 1 or 3.)

- **For Carry-out (Cout)**: Mark 1s for input combos where Cout=1. The K-map groups yield a Sum-of-Products expression. One simplified form is:  
  **\[Cout = A·B + A·Cin + B·Cin\]** ([notes1-2.dvi](https://www.classe.cornell.edu/~ib38/teaching/p360/lectures/wk09/l25/notes2.pdf#:~:text=This%20yields%20Couti%20%3D%20aibi,can%20be%205%20bits%2C%20where)).  
  This means a carry-out occurs if **any two** of the inputs are 1 (or all three). You can also factor this as \(Cout = A·B + Cin·(A + B)\), which is logically equivalent. Another way to think of this formula is: Cout = 1 if **majority** of the inputs are 1. This is consistent with the truth table and our earlier understanding ([](https://ece.mst.edu/media/academic/ece/documents/coursenotes/cpe2211computerengineeringlab/cpe2211-fall2024/Hierarchical%20Design%20of%20a%20Four%20Bit%20Adder.pdf#:~:text=A%20logic%20diagram%20for%20a,This)).  

**Worked Example (Boolean Simplification):**  
From the truth table, one of the minterms where Sum=1 is A=0, B=0, Cin=1. This gives a product term ¬A·¬B·Cin. Repeating for all Sum=1 rows and combining (ORing) them yields the unsimplified Sum-of-Products. Using K-map grouping or Boolean algebra, these terms reduce to the XOR form above. Similarly, for Cout, minterms like A=1, B=1, Cin=0 yield A·B·¬Cin, etc., which simplify to the expression given for Cout. If you prefer a more intuitive check: plug in some values. For instance, \(Cout = A·B + A·Cin + B·Cin\) — if A=1, B=1, Cin=0, this gives Cout=1 (since A·B=1), matching the table. If A=1, B=0, Cin=1, it gives Cout=1 (since A·Cin=1), etc. All eight cases will match the truth table. 

**Side note:** The Sum output can also be derived using two half-adders: First, compute `X = A XOR B` (half-sum of A and B) and `C1 = A AND B` (carry from A+B). Then compute final Sum = `X XOR Cin`, and second carry `C2 = X AND Cin`. Finally, Cout = `C1 OR C2`. If you simplify these two carry terms `C1` and `C2`, you'll get the same Cout expression as above ([notes1-2.dvi](https://www.classe.cornell.edu/~ib38/teaching/p360/lectures/wk09/l25/notes2.pdf#:~:text=This%20yields%20Couti%20%3D%20aibi,can%20be%205%20bits%2C%20where)). This two-half-adder method is a common way to conceptualize the full adder's implementation.

### Implementing the Full Adder in LTSpice (Circuit Schematic)  
With the Boolean expressions in hand, we can now draw the logic circuit. We’ll use **LTSpice**, a free SPICE-based circuit simulator from Analog Devices, to implement and test the full adder. (LTSpice is widely used by engineers and hobbyists to simulate circuits, providing an easy way to build schematics and run simulations.) 

**Building the Circuit:** In LTSpice, create a new schematic (File → New Schematic). We will need three types of logic gates: XOR, AND, and OR ([
            LTspice Wizardry: Crafting Full Adder for Digital Circuits!
        ](https://www.digikey.com/en/maker/tutorials/2024/ltspice-wizardry-crafting-a-full-adder-for-digital-circuits#:~:text=Step,adder%27s%20sum%20and%20carry%20below)). Using the component selection dialog in LTSpice, place the following gates to realize the expressions: 

- **Sum Logic:** Place two XOR gates. Connect A and B into the first XOR (producing A⊕B). Then feed the output of that into a second XOR along with Cin. The output of the second XOR is the Sum (S). This implements S = A ⊕ B ⊕ Cin as derived above.  
- **Carry-out Logic:** Place two 2-input AND gates and one 2-input OR gate. Connect A and B into the first AND (giving A·B). Connect A and Cin into the second AND (this yields A·Cin). Now, take the outputs of both AND gates into the OR gate. The OR’s output will be \(A·B + A·Cin\). To also include the \(B·Cin\) term, we have two options: (a) use a second OR gate to OR the above result with a third AND gate for B·Cin, or (b) realize that \(A·Cin + B·Cin = Cin·(A+B)\) and simply add one more connection: use an OR gate with three inputs (if available) or chain OR gates. For simplicity, you might add a third AND gate for B·Cin and then OR its output with the previous OR output. The final OR output is Cout. (Alternatively, a clever implementation is to reuse the XOR output: \(B·Cin\) can be obtained by ANDing Cin with the output of the first XOR (A⊕B), since \(A⊕B = 1\) exactly when one of A or B is 1, thus \(Cin*(A⊕B) = A·Cin + B·Cin\). Then Cout = OR( A·B, Cin·(A⊕B) ). This saves one gate.)  

**Power and Ground:** In LTSpice’s digital logic gate library, logic gates typically treat any input voltage above a threshold as logic 1 and 0V as logic 0. To provide input bits A, B, Cin, you can use **voltage sources** set to generate 0V or 5V (or 1V) levels. A convenient approach is to use pulsed voltage sources (`VPULSE`) set at different intervals so that they cycle through all combinations (more on this in the testing section). Place a ground reference (`GND`) and connect the negative side of each source to ground, and the positive side to the gate inputs. Label the node after the final XOR as “S” (Sum) and after the OR gate as “Cout” (Carry-out) using the net label tool (so that we can probe these easily in simulation) ([
            LTspice Wizardry: Crafting Full Adder for Digital Circuits!
        ](https://www.digikey.com/en/maker/tutorials/2024/ltspice-wizardry-crafting-a-full-adder-for-digital-circuits#:~:text=,Full%20Adder%20for%20Digital%20Circuits)).  

**Example Schematic Setup:** Arrange the gates so that A, B, Cin inputs come from the left. Connect A and B to the first XOR and first AND; connect Cin and the output of first XOR to the second XOR; connect Cin to the second AND (with A) and to a third AND (with B). OR together the outputs of the first AND, second AND, and third AND (using two OR gates cascaded if needed) to produce Cout. In sum, your schematic should resemble the classic full adder logic diagram: two XORs for the sum path, and a network of AND/OR for the carry path ([notes1-2.dvi](https://www.classe.cornell.edu/~ib38/teaching/p360/lectures/wk09/l25/notes2.pdf#:~:text=This%20yields%20Couti%20%3D%20aibi,can%20be%205%20bits%2C%20where)). Ensure all unused inputs of any gate are properly connected (in our design, all gate inputs are used by signals). 

> **Learning Tip:** If you are new to digital simulators, a more visual tool like *iCircuit* can be helpful for experimentation. *iCircuit* is an easy-to-use circuit simulator (available on PC, Mac, and mobile) that lets you drop in logic gates and interactively flip input switches to see outputs change. It’s great for learning because it provides real-time feedback. However, in this guide we focus on LTSpice, as it offers more rigorous simulation capabilities and prepares you for industry-standard workflows.

### Symbol Creation in LTSpice (Hierarchical Design)  
After building and verifying the single-bit full adder, you can encapsulate it as a reusable component. LTSpice supports **hierarchical design** by allowing you to create a custom symbol for your schematic and then use that symbol in higher-level circuits (like a building block). This is useful when making a multi-bit adder, as you can place multiple full adders without redrawing the entire gate-level schematic each time.

**Creating a Custom Symbol:** In your full adder schematic window, click **Hierarchy → Create New Symbol**. LTSpice will open the symbol editor, showing a blank canvas ([Creating a schematic symbol in LTspice - Electrical Engineering Stack Exchange](https://electronics.stackexchange.com/questions/529478/creating-a-schematic-symbol-in-ltspice#:~:text=)). Here, draw a simple shape (e.g. a rectangle) to represent the adder and add pin labels for each input and output. For example, add pins named “A”, “B”, “Cin” on the left side, and “S”, “Cout” on the right side. Ensure the pin names exactly match the net labels or port names in your schematic (case-sensitive). In the symbol’s attributes (Edit → Attributes → Edit Attributes), set the prefix to “X” (which denotes a hierarchical block in LTSpice) and the symbol type to “Block” for a hierarchical symbol ([Creating a schematic symbol in LTspice - Electrical Engineering Stack Exchange](https://electronics.stackexchange.com/questions/529478/creating-a-schematic-symbol-in-ltspice#:~:text=1,This%20is%20an%20example)) ([Creating a schematic symbol in LTspice - Electrical Engineering Stack Exchange](https://electronics.stackexchange.com/questions/529478/creating-a-schematic-symbol-in-ltspice#:~:text=In%20LTSpice%2C%20in%20the%20window,option)). Save the symbol with the same name as your schematic (e.g., `full_adder.asy` for `full_adder.asc`) in LTSpice’s sym folder or the working directory. Once saved, you can now use this symbol in any schematic by selecting “Add Component” and finding it in the list (it will appear under the “AutoGenerated” or “Top Level” category if placed in the same directory as the project).

**Why use a symbol?** This makes the design **scalable and modular**. Instead of a cluttered schematic with dozens of gates for multi-bit adders, you’ll have a clean block representation. This also allows you to easily reuse the full adder in different projects. (In large designs, this approach is called *bottom-up design*: build small components, then integrate them into bigger ones ([](https://ece.mst.edu/media/academic/ece/documents/coursenotes/cpe2211computerengineeringlab/cpe2211-fall2024/Hierarchical%20Design%20of%20a%20Four%20Bit%20Adder.pdf#:~:text=language,complexity%20of%20the%20higher%20level)) ([](https://ece.mst.edu/media/academic/ece/documents/coursenotes/cpe2211computerengineeringlab/cpe2211-fall2024/Hierarchical%20Design%20of%20a%20Four%20Bit%20Adder.pdf#:~:text=which%20consist%20entirely%20of%20primitive,solid%20understanding%20of%20the%20basics)).)

### Testing and Validation through Simulation  
With the full adder schematic (or symbol) ready, it’s time to test it to ensure it behaves according to the truth table. We will perform a **transient analysis** (time-domain simulation) in LTSpice to simulate logic transitions. 

**Setting Up Inputs:** A straightforward way to test all input combinations is to drive A, B, and Cin with square waves of different frequencies so that they cycle through 0/1 patterns. For example:
- Let Cin toggle the fastest (e.g., a pulse with period 2 ms, 50% duty cycle).
- Let B toggle a bit slower (period 4 ms, so it changes state every 2 ms).
- Let A toggle slower yet (period 8 ms, changes every 4 ms).  

If you start all at 0 at time 0, over an 8 ms interval this will generate all 8 combinations of (A, B, Cin). (At 0–2ms: 000, 2–4ms: 001, 4–6ms: 010, 6–8ms: 011, then 8–10ms: 100, etc., eventually covering 111 by 14–16ms, if you extend the sim that far). You can achieve this by setting up each input as a `VPULSE` source: e.g., for Cin, initial 0V, pulsed to 5V, with a period of 2ms; for B, period 4ms; for A, period 8ms (adjust rise/fall times to very small values to emulate ideal logic transitions). An alternative if you prefer manual testing is to run multiple simulations, each with A, B, Cin set to a fixed combination (using DC voltage sources set to 0 or 5V and editing between runs). But the pulsed approach is faster and more thorough.

**Running the Simulation:** In LTSpice, add a transient command (`.tran`) for an appropriate duration (e.g., 20ms to cover all changes). Click Run. The waveform viewer will pop up. Add traces for A, B, Cin, S, and Cout by clicking on the wires or net labels in the schematic (each click on a net will plot its voltage). Then use **View → Plot Settings → Add Plot Pane** to stack the waveforms separately for clarity ([
            LTspice Wizardry: Crafting Full Adder for Digital Circuits!
        ](https://www.digikey.com/en/maker/tutorials/2024/ltspice-wizardry-crafting-a-full-adder-for-digital-circuits#:~:text=Step,pane%20and%20Add%20Plot%20Pane)). You should see timing diagrams of the inputs and outputs. Compare the output waveforms of S and Cout against the expected values from the truth table for each input combination over time. For instance, whenever A=1, B=1, Cin=0 in the waveform, check that at that time S went low and Cout went high, etc. **All 8 cases** should match the truth table exactly ([
            LTspice Wizardry: Crafting Full Adder for Digital Circuits!
        ](https://www.digikey.com/en/maker/tutorials/2024/ltspice-wizardry-crafting-a-full-adder-for-digital-circuits#:~:text=Step,results%20with%20the%20truth%20table)). 

If the outputs don’t match, this indicates a mistake in wiring or logic. Common errors include wrong connections of gates (e.g., feeding Cin into the wrong XOR input), or forgetting an OR gate for one of the carry terms. Fix any issues and re-run until the simulation results align perfectly with the theory. This validation step is crucial in digital design – it ensures your implementation is correct before you build bigger circuits from it.

### Cascading Full Adders to Form a 4-Bit Adder  
Now that our one-bit full adder is working, we can **cascade multiple full adders** to handle multi-bit binary addition. Cascading means connecting the carry-out of the least significant bit adder to the carry-in of the next adder, and so on, forming what’s called a **ripple-carry adder**. In general, to add two N-bit numbers, we use N full adders in series ([Half Adder and Full Adder Circuit with Truth Tables](https://www.elprocus.com/half-adder-and-full-adder/#:~:text=as%20C,one%20adder%20to%20the%20next)). (Each full adder is responsible for one bit position; the carry “ripples” to the next adder.) Here, we’ll build a 4-bit adder using four of our full adder units.

**4-Bit Adder Setup:** If you created a symbol for the full adder, simply place four instances of that symbol in a new LTSpice schematic. Label them FA0, FA1, FA2, FA3 for bit0 (least significant bit, LSB) through bit3 (most significant bit, MSB). Connect input A0, B0, and an initial Cin (often this will be 0 if you are just adding two 4-bit numbers with no incoming carry) into FA0. Connect FA0’s Cout to FA1’s Cin; FA1’s Cout to FA2’s Cin; FA2’s Cout to FA3’s Cin. Also connect the operand bits A1,B1 into FA1, A2,B2 into FA2, A3,B3 into FA3. All full adders share the same ground reference. The outputs from each adder (S0, S1, S2, S3) will form the 4-bit sum result. FA3’s Cout will be the **final carry-out** of the 4-bit adder (call it C4 or Cout_4). This final carry represents an overflow bit (the 5th bit of the sum) ([notes1-2.dvi](https://www.classe.cornell.edu/~ib38/teaching/p360/lectures/wk09/l25/notes2.pdf#:~:text=As%20stated%20above%2C%20the%20carry,a%20b%20Cout%20Cin)). 

In a schematic, you might draw the four adders left-to-right, with A3,B3 as the most significant input bits going into the rightmost adder. Tie Cin of the first adder (FA0) to ground (0) if no external carry-in is desired. You can also create 4-bit input “buses” for A and B for neatness, but as a beginner, it’s fine to draw individual wires or label the bits A0...A3, B0...B3. The key is the chain of carry connections: **Cout of bit i goes into Cin of bit i+1**.

This structure is a **4-bit ripple-carry adder**. Its operation is straightforward: FA0 adds the LSBs (A0+B0+Cin0) producing S0 and carry C1; then FA1 adds A1+B1+C1 producing S1 and C2, and so on. The carries ripple through, and S0...S3 form the sum output. (If you’ve learned about binary addition by hand, this is exactly the same process, just implemented with circuits for each bit.)

### Testing the 4-Bit Adder  
Testing a multi-bit adder is similar in spirit to the 1-bit case, but with more combinations. A 4-bit adder has 8 inputs (A0–A3, B0–B3, plus perhaps an initial Cin and the final Cout as output), so exhaustive testing would involve 2^8 = 256 combinations of (A, B, Cin). That’s a lot, but we can sample representative cases to gain confidence: 

- **Basic cases:** Test the addition of two small numbers without carry, e.g. 0001₂ (1) + 0010₂ (2) = 0011₂ (3). Also try adding zero: A=0000 + B=some value should output B.  
- **Carry generation:** Test cases where carries are produced and ripple through. For example, 0101₂ (5) + 0011₂ (3) = 1000₂ (8). Here, adding the lower bits produces a carry that affects the higher bits. Verify that the result is correct (5 + 3 = 8) and that the Cout (overflow) is 0.  
- **Carry propagation chain:** A good test is adding 1 to 0111₂ (7). 0111 + 0001 should result in 1000 (8) with a carry-out. In the ripple adder, the carry will propagate through all bits. Check that S = 1000 and final Cout = 0 (since 8 fits in 4 bits with no overflow beyond 4 bits).  
- **All 1s (overflow case):** 1111₂ (15) + 0001₂ (1) = 1 0000₂ (16), which in 4-bit outputs would show 0000 with a final Cout of 1 (overflow). This tests the maximum carry-out scenario.  
- **Random cases:** Try a few random values (e.g., A=0100₂ (4), B=1010₂ (10) should yield 1110₂ (14)). Each time, interpret the binary result and confirm it matches the expected arithmetic sum.

In LTSpice, you can simulate these by setting up voltage sources for each input bit. However, managing 8 independent pulse sources to cycle through many combinations can be complex. A simpler approach for a few specific tests is to set DC values for A0–A3 and B0–B3 (using voltage sources of value 0 or 5 accordingly) and run a short simulation (or even a .op operating point analysis) to see the output. Change the source values for different test cases. If you want to automate more, you could use a **piecewise linear (PWL)** source or a scripted stimuli, but that may be beyond a beginner scope. For now, doing a few manual configurations is fine. 

Verify the outputs by observing the node voltages for S0–S3 and the final Cout. They should correspond to the correct sum bits. If you used our full adder symbol, you inherently trust the 1-bit adder design (since it was verified earlier). So any error in the 4-bit results likely means a wiring mistake in connecting the adders (for example, forgetting to connect a carry between stages, or mixing up bit order). Double-check connections if a result is wrong. 

When all tests pass, congratulations – you have a working 4-bit binary adder! 🎉 This 4-bit adder can add two 4-bit binary numbers and is the basis for an ALU’s addition operation in many CPUs. If you were to extend this to an 8-bit adder, you’d simply chain eight full adders in the same way (the principle scales linearly ([Half Adder and Full Adder Circuit with Truth Tables](https://www.elprocus.com/half-adder-and-full-adder/#:~:text=as%20C,one%20adder%20to%20the%20next))】.

## High-Level Summary and Further Reading

### Summary of the Design Process  
Designing a full adder involves a series of clear steps: first, understanding the problem (adding three bits) and enumerating the expected behavior with a truth table. We then simplified the logic using K-maps/Boolean algebra to obtain efficient Boolean formulas for the outputs (Sum and Carry-out). Using those formulas, we built a gate-level schematic (XOR, AND, OR gates) and verified its correctness via simulation in LTSpice. After ensuring the 1-bit adder works for all cases, we scaled up by chaining four full adders to create a 4-bit adder (ripple-carry adder), again testing it with representative binary addition cases. We also created a custom symbol in LTSpice to facilitate hierarchical design, making it easier to reuse our full adder in larger circuits. Throughout the process, careful verification was key – comparing simulation outputs against the truth table and expected sums. This step-by-step approach is a reliable method for designing and understanding digital circuits like adders.

**Key takeaways:** A full adder’s sum is effectively an XOR of all inputs, and its carry-out represents a majority function (carry if two or more inputs are 1). In implementation, minimal gate usage is achieved by sharing sub-expressions (like A⊕B). Hierarchical design (using symbols or subcircuits) helps manage complexity for multi-bit adders. By mastering the full adder, you’ve also learned the foundation for building arithmetic logic units (ALUs) and more complex binary adders (like subtractors, adders with overflow detection, etc.). This forms a cornerstone for understanding computer microarchitecture at the logic level.


