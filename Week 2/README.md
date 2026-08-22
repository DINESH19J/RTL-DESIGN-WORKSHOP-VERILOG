WEEK2 EXPLANATION AND SCREEN SHOTS OF RESULTS

D Flip-Flop with Asynchronous Reset Simulation
<img width="1358" height="768" alt="flops gtkwave" src="https://github.com/user-attachments/assets/d74723d3-d840-447b-836d-41a5f2c65e9f" />

This waveform demonstrates the functional verification of a D Flip-Flop with an Asynchronous Reset (dff_asyncres) using GTKWave.
When async_reset is high (1), the output q is immediately forced to 0 independently of the clock signal (clk). It does not wait for a rising clock edge to clear the state.

Gate-Level Synthesis: D Flip-Flop with Asynchronous Reset
<img width="1360" height="768" alt="flipflop synthesis" src="https://github.com/user-attachments/assets/ca91c730-f764-4eb3-9e1d-6356d70cd5de" />

Combinational Logic Optimization: Constant Propagation
<img width="1360" height="768" alt="opt check1 - Copy" src="https://github.com/user-attachments/assets/fc73bd03-ec6a-498d-a906-cb521ef30e47" />

This netlist shows Yosys being smart—it pruned away all the unnecessary mux and branch logic in the code, realizing it simplifies to a basic AND operation. As a result, it optimized the circuit down to just a single, clean 2-input AND gate

Synthesis of Combinational Optimization
<img width="1360" height="768" alt="opt check1" src="https://github.com/user-attachments/assets/2d98a684-e56d-4979-b8b8-83024bd7e831" />

Yosys evaluated the module's boolean equations, realized the conditional math boils down to a simple a AND b, and stripped away all the extra hardware overhead. Instead of building a complex multiplexer network, it synthesized the code into a single, clean 2-input AND gate

Synthesis of Constant Optimization
<img width="1360" height="766" alt="optcheck2" src="https://github.com/user-attachments/assets/80ddc287-66ba-4227-a42c-3fc7aa2c07fb" />

Multiple Input Optimization
<img width="1360" height="768" alt="opt check 3" src="https://github.com/user-attachments/assets/4b5fb595-4954-4988-a88c-9c7281bceb97" />

Yosys analyzed the multi-level conditional structure and flattened the boolean expression down to a AND b AND c. By eliminating redundant intermediate logic, it directly mapped the module to a single 3-input AND gate

|| SEQUENTIAL LOGICS ||

Sequential Optimization Simulation
<img width="1359" height="725" alt="gtkwave for sequntial logics of const1" src="https://github.com/user-attachments/assets/eb501b00-2426-45d0-aeaa-38bbdf1ef1fd" />

This GTKWave simulation shows the behavior of a D flip-flop assigned a constant high data input (D = 1). On the rising clock edge following the deassertion of reset, the output q latches to 1 and remains permanently high regardless of subsequent clock cycles.

Sequential Logic Synthesis
<img width="1360" height="694" alt="dffconst1 synthesis" src="https://github.com/user-attachments/assets/a2c19bfa-ef58-4e15-b8e1-acbf2bb0e196" />

So here's what's actually going on in this netlist: even though the code hardcodes the data input to a constant 1, Yosys can't just throw the flip-flop away. Since the circuit still has a reset button that can force the output low at any time, that memory element is strictly required to hold the state.
So Yosys keeps the actual hardware flip-flop (sky130_fd_sc_hd__dfrtp_1) intact, hooks its data pin directly to a constant high signal (1'1), and sticks a quick inverter in front of the reset pin just to flip the active-high reset signal from your code so it matches the library cell's active-low requirement.

Cascaded Sequential Optimization (dff_const3)
<img width="1355" height="768" alt="dff_const3" src="https://github.com/user-attachments/assets/a9d8f4e6-67f1-4c55-91a6-f452aba2d8a6" />

Unused Bit Optimization in Counter (counter_opt.v)
<img width="1360" height="768" alt="counter_opt v" src="https://github.com/user-attachments/assets/593b3795-6a91-41c4-bcad-a303469bd58f" />

Instead of building a full, heavy multi-bit adder tree with flip-flops for every single counter bit, Yosys realizes that most of the higher-order bits don't even affect the final output. It strips away all those unnecessary flop stages and reduces the entire counting logic down to just a single D flip-flop combined with an inverter . It essentially turns the design into a simple toggle flop for the LSB, throwing away all the dead logic to save a ton of power and chip area.

Counter Logic Optimization: Unused Bits vs. Full Output Comparison

<img width="1360" height="768" alt="before editing the counter" src="https://github.com/user-attachments/assets/9373ca4b-e9c4-4e55-99c5-b3bbbfc8a119" />

in this image When the code only checks the lowest bit (count[0]), Yosys realizes that count[1] and count[2] have zero effect on q. Instead of synthesizing a full 3-bit counter, it aggressively optimizes the circuit down to a single flip-flop and an inverter, treating it like a basic toggle flop and trashing the unused higher bits in next
<img width="809" height="619" alt="changed counterOpt" src="https://github.com/user-attachments/assets/be085348-8d4b-4b95-b2f9-362a75e0d251" />

When we update the code to check if the entire 3-bit vector equals 3'b100 (4 in decimal), Yosys can no longer throw any bits away.
Since all three counter bits are now required to evaluate the equality condition, Yosys synthesizes the full counter architecture:
3 Flip-Flops: It instantiates three standard cells to track count[0], count[1], and count[2].
Combinational Comparator Logic: It builds NOR, NAND, and XOR gate networks to decode when the counter hits 100 and drive the q output high.

after changing the synthesis of counter logic optimization
<img width="1360" height="768" alt="counter with 3ff" src="https://github.com/user-attachments/assets/8d8e87ea-493b-4e78-8205-fd48e6001771" />

Gate-Level Simulation: Ternary Operator MUX (tb_ternary_operator_mux)
<img width="1360" height="768" alt="ternary operator (GLS)" src="https://github.com/user-attachments/assets/a3ff61c4-da62-4806-8ec6-8afc177b4573" />

Logic Synthesis: Ternary Operator MUX (ternary_operator_mux)
<img width="1356" height="765" alt="ternary operator mux synthesis" src="https://github.com/user-attachments/assets/60026c8e-d4cf-442d-be20-4a36d251fab1" />


Post-Synthesis Gate-Level Simulation (GLS Verification)
<img width="1351" height="768" alt="gls output" src="https://github.com/user-attachments/assets/df385bf3-c2dd-4641-b12d-d763803a6969" />

Gate-Level Simulation (GLS)
Gate-Level Simulation is the process of running functional testbenches against the synthesized netlist—the actual logic gates and flip-flops generated by Yosys—rather than the high-level Verilog RTL code.

Pre-Synthesis Behavioral Bug (bad_mux)
<img width="1360" height="768" alt="badmux" src="https://github.com/user-attachments/assets/e35966fe-06d3-4e9b-b281-23cc0939da8c" />

This GTKWave trace captures the exact moment where an incomplete sensitivity list breaks the simulation logic before synthesis even happens.

Corrected MUX Simulation (good_mux)

<img width="1356" height="768" alt="badmux to goodmux" src="https://github.com/user-attachments/assets/94d31bd7-92c9-4880-835d-ed36af86f7b8" />

This GTKWave trace shows the fixed, expected behavior of a 2-to-1 multiplexer after updating the RTL sensitivity list to always @(*) or always @(sel or i0 or i1).

Now, the simulator re-evaluates the code whenever any input signal changes. As seen across the waveform:

RTL Fix: Sensitivity List Bug (bad_mux.v vs good_mux.v)
<img width="1357" height="768" alt="problem" src="https://github.com/user-attachments/assets/71bea9b6-d196-41c1-9d11-7b71ffa5c2ba" />

The Problem (bad_mux.v)
Incomplete Sensitivity List: always @(sel) tells the simulator to trigger the block only when sel changes value.

Simulation Behavior: If sel stays constant at 0 or 1, changes on i0 or i1 are completely ignored by the simulator, causing y to hold its old value like an unintended latch.

Synthesis Behavior: Yosys ignores incomplete sensitivity lists for combinational logic and synthesizes a standard 2-to-1 MUX. The hardware updates y whenever i0 or i1 changes, causing pre-synthesis simulation and real hardware to behave differently.

The Fix (good_mux.v)
Wildcard Sensitivity List: Change always @(sel) to always @(*).

Result: The * wildcard automatically adds all inputs (sel, i0, i1) to the sensitivity list. The simulator now re-evaluates the block whenever any input signal changes, perfectly matching the synthesized multiplexer hardware.


Unintended Latch Generation: Incomplete if Statement (incomp_if)
<img width="1356" height="768" alt="incomplete if" src="https://github.com/user-attachments/assets/4263b373-ea92-49ef-a98f-93aa7d1b8e9c" />

Uninitialized State (0 to ~300 ns): At start-up, y displays a solid red bar, indicating an undefined/unknown state (x). Because there is no else condition, the code fails to specify what value y should hold when the if condition evaluates to false, leaving y completely unassigned initially.
Latch Retention Behavior: Once y is driven high by meeting the if condition, it holds its previous value whenever the condition drops false. Instead of acting as pure combinational logic, the circuit inf

Inferred Latch Hardware Netlist (incomp_if)
<img width="1360" height="768" alt="synthesis of incomplete if" src="https://github.com/user-attachments/assets/01472e78-f322-4f51-8848-43fc700fdd53" />


Unintended Latch Generation: Incomplete case Statement (incomp_case)
<img width="1350" height="768" alt="incompcase wave" src="https://github.com/user-attachments/assets/f2490e4b-9316-43b4-9955-5185f54e0a3c" />

Just like an incomplete if statement, an unhandled case condition forces synthesis tools (such as Yosys) to infer an unwanted transparent latch ($_DLATCH_P_) to store the previous output value during missing cases.


Inferred Latch Netlist: Incomplete case Statement (incomp_case)
<img width="1360" height="739" alt="synthesis of incomp" src="https://github.com/user-attachments/assets/ec382b62-915b-4d05-be6f-1a2816788608" />

Combinational Decoding: The multiplexer along with the decoding logic  handles the defined selection cases (00, 01, 10).
State Retention Latch: The decoded signal feeds into data pin D of the $_DLATCH_N_ latch cell, while enable pin E controls when the output updates. When sel = 11 hits, the enable line goes inactive, freezing the output Q to preserve the previous state.


Corrected Waveform: Complete case Statement (comp_case)
<img width="1350" height="768" alt="wave for comp_case" src="https://github.com/user-attachments/assets/703ae44b-8b47-480f-8043-91d8ffe09e9a" />

Latch-Free Behavior: Every single combination of the 2-bit select signal maps to a valid output assignment, completely removing memory retention and ensuring pure combinational logic execution.

Latch-Free Synthesis: Complete case Statement (comp_case)
<img width="1360" height="768" alt="synthesis of complete case" src="https://github.com/user-attachments/assets/c8663135-804e-440b-b803-063b8e17d34c" />

Multiplexer Stage (sky130_fd_sc_hd__mux2i_1): An inverted 2-to-1 MUX handles the primary input selection between i0 and i1 based on bit 0 of sel.
Combinational Decoding (sky130_fd_sc_hd__nand2_1 & sky130_fd_sc_hd__o21ai_0): NAND and OR-AND-Invert logic gates decode the remaining select bits and evaluate input i2 / default branches.
Direct Output Path: The decoded signal drives output y directly through the gate tree without passing through any latch ($_DLATCH_) memory elements.


Inferred Latch Netlist: Partial Assignment in case Statement (partial_case_assign)
<img width="1357" height="768" alt="synthesis of partial_case" src="https://github.com/user-attachments/assets/40b22830-6a8e-4484-909d-f5b7f0dcb5a9" />

Simulation Verification: Parameterized for Loop / Generate MUX (tb_mux_generate)
<img width="1354" height="765" alt="simulation for mux generated" src="https://github.com/user-attachments/assets/13297ce6-bd4a-43b1-8512-39f0a57b8f12" />

This GTKWave trace confirms the pre-synthesis functional behavior of a parameterized 4-to-1 multiplexer implemented using a Verilog for loop (or generate construct).

Simulation Verification: Generative 1-to-8 Demultiplexer (tb_demux_generate)

<img width="1360" height="768" alt="dimulation for demux generative" src="https://github.com/user-attachments/assets/202f9dd6-7ac1-4644-a15c-61de17bdce78" />

Internal Bus Tracking (y_int[7:0]): The internal vector correctly updates its corresponding bit slice during each selection window, validating that the loop variable (k = 8) completely unrolls into an 8-output decoder/demux array without latching non-selected lines.

Simulation Verification: Ripple Carry Adder using generate Block (tb_rca)
<img width="1360" height="764" alt="rca simulation" src="https://github.com/user-attachments/assets/ea5c9f28-7d50-48df-9293-8bf6ec653090" />

This GTKWave trace captures the pre-synthesis functional simulation of an 8-bit Ripple Carry Adder (RCA) constructed by instantiating Full Adder modules inside a Verilog generate for loop.



