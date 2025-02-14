# ECE 281 ICE 3: Ripple-Carry Adder with Top Level Design

This is a **template** repository.


[ICE 3 instructions](https://usafa-ece.github.io/ece281-book/ICE/ICE3.html)

Targeted toward Digilent Basys3. Make sure to install the [board files](https://github.com/Xilinx/XilinxBoardStore/tree/2018.2/boards/Digilent/basys3).

Tested on Vivado 2024.2
<img width="960" alt="{FC38CC8C-26A9-441C-8FF3-C5DFAD8CF154}" src="https://github.com/user-attachments/assets/bd1f726b-f7fb-41b8-b94b-27e4d7d3e474" />

---

## Documentation: 
C3C Kyle Litman helped me understand how to do the entity diagram. He helped me understand how the port mapping 
translates to the entity diagram.  

<img width="676" alt="{1FA31F8E-82BF-4B8C-89B8-D5E007CB5B46}" src="https://github.com/user-attachments/assets/ea721279-4c3f-4cd6-8596-3523fd0675ab" />



![alt text]({FC38CC8C-26A9-441C-8FF3-C5DFAD8CF154}-1.png)

## GitHub Actions Testbench

The workflow uses the [setup-ghdl-ci](https://github.com/ghdl/setup-ghdl-ci) GitHub action
to run a *nightly* build of [GHDL](https://ghdl.github.io/ghdl/).

First, the workflow uses GHDL to **analyze** all `.vhd` files in `src/`.

Then it **elaborates** the entity defined by `$TB_ENTITY`

Finally, the workflow **runs** the simulation. If successful then it will quietly exit with a `0` code.
If any of the `assert` statements fail then GHDL will cease the simulation and exit with non-zero code; this will also cause the workflow to fail.
Assert statements of other severity levels will be reported, but not fail the workflow.
