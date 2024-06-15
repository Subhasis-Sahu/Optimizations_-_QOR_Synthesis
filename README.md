# Optimizations and Quality of Results in Synthesis
<details>

<summary> Day 9 - Optimizations in Synthesis</summary>

Optimization Goals for Synthesis :

* To meet Timing
* To meet Area
* To meet Power


The above 3 goals are always contradictory to each other i.e trying to optimize one,will degrade the other characteristics.

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/d843072c-f607-447a-b992-597c7f93278c)

#### Combinational Logic Optimization :

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/07d6808b-eb23-4875-8497-bf33d73fecbc)

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/d539e428-b953-4e3b-b9d5-9a43de640ed8)

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/8a77499c-c577-4338-aee8-16166fdb1eee)

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/2c0a54c7-ddcc-42d2-9829-a9df1ec31ebd)

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/761a0dae-c60f-461a-8b6e-e6eb455f3418)

Between Balanced and Preferential Implementation, Constraints are the deciding factor on which implementation will be inferred by Synthesis Tool. In Example given below, if `e` is a late arriving signal and has huge external delay and it can withstand least gate delay between `e` & `y`, then preferential implementation will be inferred by DC tool instead of Balanced Implementation to meet the **`constraints`**.

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/5c2aa732-5116-4156-a294-4cfdd42fae17)


#### Sequential Logic Optimization :

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/87b0c26c-498a-42c5-83db-5f87f17f1997)

#### Sequential Constant Propagation :

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/e8b9a9ea-d193-497a-8dd1-ee053436ef8b)

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/282efeac-8d39-42ac-a9e3-9352e298024b)

When the value of `Q` changes (from `1->0 & 0->1`) based on the assertion of `reset` or `set` signals, even if the `D` input of Flop is tied to a constant input (`1'b0` or `1'b1`), it would not be considered as a 
sequential constant  and the sequential logic would be retained as is and not be optimized away.

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/ecd06941-dffc-416b-8a5c-832dce4b8370)

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/5c35db05-18e0-418c-9966-82d50dc5ece8)

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/b08dd480-ace5-4549-8185-782ad9237acb)

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/f53ec1de-dd0b-42a9-8021-8922c28a8402)

#### Optimizations of Unloaded Outputs : 

Logic generated to produce outputs which are not getting used will be further optimized away, to improve PPA.

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/6f24ab51-ae68-46b3-a6b1-9f4ab5970afc)

#### Controlling Sequential Optimizations by setting few boolean variables as true or false :

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/4a2bb46a-d008-4f2b-a224-eba27e6858b8)

#### Special Optimizations :


##### Register Retiming :

**Understanding Register Retiming** :

* Register retiming is a sequential optimization technique that moves registers through the combinational logic gates of a design to optimize timing and area. Other optimization techniques, such as those implemented in the compile_ultra command or compile command, optimize the combinational logic by performing Boolean optimization and mapping to cells in the technology library. These techniques leave unchanged the location and number of any registers present in the design. Register retiming adds an opportunity for improving circuit timing.
* When we describe circuits at the RT-level prior to logic synthesis, it is usually very difficult and time-consuming, if not impossible, to find the optimal register locations and code them into the HDL description. With register retiming, the locations of the flip-flops in a sequential design can be automatically adjusted to equalize as nearly as possible the delays of the stages. This capability is particularly useful when some stages of a design exceed the timing goal while other stages fall short. If no path exceeds the timing goal, register retiming can be used to reduce the number of flip-flops, where possible.
* Purely combinational designs can also be retimed by introducing pipelining into the design. In this case, we first specify the desired number of pipeline stages and the preferred flip-flop from the target library. The appropriate number of registers are added at the outputs of the design. Then the registers are moved through the combinational logic to retime the design for optimal clock period and area. Register retiming leaves the behavior of the circuit at the primary inputs and primary outputs unchanged (unless we choose special options that do not preserve the reset state of the design or add pipeline stages). Therefore we do not need to change any simulation test benches developed for the original RTL design.
* Retiming does, however, change the location, contents, and names of registers in the design. A verification strategy that uses internal register inputs and outputs as reference points will no longer work. Retiming can also change the function of hierarchical cells inside a design and add clock, clear, set, and enable pins to the interfaces of the hierarchical cells.

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/288c414a-3f81-42b8-9281-011e6ddeb982)

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/0d5170fe-b2a8-4994-97d4-12ce206caab3)


#### Boundary Optmization :

How to control boundary optimization?

    set_boundary_optimization <design> <true|false>
    for ex : set_boundary_optimization module_sub false
    

![image](https://github.com/Subhasis-Sahu/Optimizations_-_QOR_Synthesis/assets/165357439/ed0dfa09-5fb1-4c3c-b642-0d2efe6d4a83)

























