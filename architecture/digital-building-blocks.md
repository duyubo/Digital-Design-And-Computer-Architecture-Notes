# Digital Building Blocks

* [Arithmetic Circuits](#ac)
    * [Adders and Substractions](#as)
    * [Comparator](#com)
    * [Shifter and Rotators](#shre)
    * [ALU](#alu)
    * [Multiplication](#mul)
    * [Division](#di)
* [Counters](#co)
* [Shift Registers](#sr)
* [Memory Arrays and Logic Arrays](#mala)
* [Number System](#ns)

This part reviews some elaborate combinational and sequential buillding blocks used in digital systems such as arithmetic circuits, counters, shift registers, memory arrays and logic arrays. 


## <span id = ac> Arithmetic Circuits </span>
### <span id = as> Adders and Substractions </span>
#### Adders: Carry Propagate Adder (CPA)
The bascis element for the adder is called full adder, where $A + B + C_{in} = C_{out}S$:
![Full Adder](url1/FullAdder.png) 
$S = A \oplus B \oplus C_{in}$ and $C_{out} = AB + AC_{in}+BC_{in}$
##### Ripple Carry Adder
![Ripple Carry Adder](url1/RippleCarryAdder.png) 
The addition is executed sequentially from input side to the output side and all the adders wait for the $C_{out}$ from their precedent as the $C_{in}$ of its input.
* Delay time: $t_{tripple} = Nt_{FA}$, where t_{FA} is the delay of a full adder.
* Advantage: Simple and cheap.
* Disadvantage: Too slow espically when the size is large.

##### Carry Look-Ahead Adder
Carry look-ahead adder tries to reduce the propagation time by dividing into blocks which can quickly determine the carry out of a block as soon as the carry in is known. For each block, it uses **generator** which means whether the column generates the bit 1 without the carry in and **propagator** means  wether it propagates the carry in bit.

$G_i$: generated signal from column i. $G_i = A_iB_i$.
$P_i$: if column i propogates the signal. $P_i = A_i + B_i$.

$C_i = A_iB_i + (A_i + B_i)C_{i-1} = G_i + P_iC_{i-1}\\G_{3:0} = G_3 + P_3(G_2 + P_2 (G_1 + P_1G_0))\\P_{3:0} = P_3P_2P_1P_0\\C_i=G_{i:j} + P_{i:j}C_j$ 

* Delay time:$t_{CLA} = t_{pg} + t_{pg\_block} + (\frac{N}{k}-1)t_{AND\_OR} + kt_{FA}$. Where $ t_{pg} $ is the delay of the individual gates to generate $G_i$ and $P_i$, $t_{pg\_block}$ is the delay to find the $P_{i:j}$ and $G_{i:j}$ for a k-bit block, and $t_{AND\_OR}$ is the delay from $C_{in}$ to $C_{out}$ through the final AND/OR logic of the k-bit CLA block. Finally, the critical path through the last block contains a short ripple-carry adder $t_{FA}$. The computation of $G_i$ and $P_i$ is to propagate the $C_{out}$ quickly to the next block, we still need the ripple-carry adder to calculate the output $S$.  

Here is an example of 32-bit carry look ahead adder, in (a) the adder is divided into 8 4-bit CLA block, in (b) is the diagram of each block:
![Carry Look Ahead Adder](url1/CarryLookaheadAdder.png) 

* Advantage: For N > 16 it is much faster.
* Disvantage: Still increases linearly but more expensive.

### <span id = com> Comparator </span>
###  <span id = shre> Shifter and Rotators </span>
### <span id = alu> ALU </span>
### <span id = mul> Multiplication </span>
### <span id = di> Division </span>
##  <span id = co> Counters </span>
## <span id = sr> Shift Registers </span>
## <span id = mala> Memory Arrays and Logic Arrays </span>
## <span id = ns> Number System </span>
