# Optimizations and Quality of Results in Synthesis
<details>

<summary> Day 8 - Optimizations in Synthesis</summary>

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


















