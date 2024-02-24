
# Cadence Virtuoso Simulation of Low Power and High Performance 2x4 and 4x16 Line‐Decoder


# Introduction

* Static CMOS circuits are widely used for the majority of logic gates in integrated circuits. They comprise complementary N-type metal-oxide-semiconductor (NMOS) pulldown and P-type metal-oxide semiconductor (PMOS) pullup networks, offering good performance, resistance to noise, and 
tolerance to device variation. Consequently, complementary metal-oxide-semiconductor (CMOS) logic is known for its robustness against voltage scaling and transistor sizing, ensuring reliable 
operation at low voltages and small transistor sizes.
* The design simplicity of CMOS logic, where input signals are connected only to transistor gates, facilitates cell-based logic synthesis and design. 
Pass transistor logic (PTL) emerged in the 1990s as an alternative to CMOS logic, aiming to enhance speed, power efficiency, and area utilization.
* The key distinction lies in applying inputs to both the gates and the source/drain diffusion terminals of transistors.
* Pass transistor circuits can be implemented using individual NMOS/PMOS pass transistors or parallel pairs of NMOS and PMOS, known as transmission gates. 
* Line decoders, fundamental circuits widely employed in the peripheral circuitry of memory arrays (e.g., SRAM), serve as the focus of this brief.
* This paper introduces a mixed-logic methodology for their implementation, striving for improved performance compared to single-style design.


*  TABLE I: TRUTH TABLE OF THE 2–4 DECODER

![1](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/cfe7f49d-82e0-49f8-8eca-d1d18218db40)


* TRUTH TABLE OF THE INVERTING 2–4 DECODER

![2](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/b38b6043-8d79-44db-a132-6cc93ed3feaa)

* Implementation is discussed in detail, opting for a mixed-logic approach to enhance performance compared to conventional designs. The structure of the remaining sections is as follows: Section II 
provides a brief overview of examined decoder circuits implemented with conventional CMOS logic.
* Section III introduces the new mixed-logic designs. Section IV conducts a comparative simulation study among the proposed and conventional decoders, with a detailed discussion on the derived 
results. Section V provides the summary and final conclusions of the work presented.

# OVERVIEW OF LINE DECODER CIRCUITS

* In digital systems, binary codes represent discrete quantities of information. An n-bit binary code can depict up to 2^n distinct data elements. A decoder is a combinational circuit that converts binary information from n input lines to a maximum of 2^n unique output lines, or fewer if the n-bit coded 
information has unused combinations.
* The circuits under examination are n-to-m line decoders, generating the m = 2^n minterms of n input variables.

## A. 2–4 Line Decoder

A 2–4 line decoder generates the 4 minterms (D0−3) of 2 input variables (A and B). Its logic operation is summarized in Table I. Depending on the input combination, one of the 4 outputs is 
selected and set to 1, while the others are set to 0. An inverting 2–4 decoder generates complementary minterms (I0−3), setting the selected output to 0 and the rest to 1, as shown in Table II.
* In conventional CMOS design, NAND and NOR gates are preferred for efficiency. A 2–4 decoder can be implemented with 2 inverters and 4 NOR gates (Fig. 1a), whereas an inverting decoder requires 2 inverters and 4 NAND gates (Fig. 1b), both totaling 20 transistors.
  
![3](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/9a53d2a7-44f0-4e45-ba74-f2ab0c8825dc)


## B. 4–16 Line Decoder With 2–4 Predecoders

* A 4–16 line decoder generates the 16 minterms (D0−15) of 4 input variables (A, B, C, and D), and an inverting 4–16 line decoder generates the complementary minterms (I0−15). These circuits can be implemented using a predecoding technique, where blocks of n address bits are predecoded into 1-of-2n predecoded lines serving as inputs to the final stage decoder. Therefore, a 4–16 decoder can be implemented with 2 2–4 inverting decoders and 16 2-input NOR gates (Fig. 2a).
* An inverting one can be implemented with 2 2–4 decoders and 16 2-input NAND gates (Fig. 2b). In CMOS logic,these designs require 8 inverters and 24 2-input gates, totaling 104 transistors each.

![4](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/71316259-4934-4e14-8f59-8c5fe052e6f3)

* Note: This brief overview sets the foundation for a detailed exploration of low-power, highperformance 2–4 and 4–16 mixed-logic line decoders.

# NEW MIXED-LOGIC DESIGNS

* Transmission Gate Logic (TGL) proves to be a proficient choice for implementing AND/OR gates [5], making it a viable option for application in line decoders. Fig. 3(a) and (b) illustrate 2-input TGL AND/OR gates, notable for being full-swinging but not restoring for all input combinations.
* In the realm of Pass Transistor Logic (PTL), two predominant circuit styles are identified. The first utilizes nMOS-only pass transistor circuits, as seen in CPL [3]. The second incorporates both nMOS and pMOS pass transistors, exemplified by DPL [4] and DVL [6].
* This work focuses on the DVL style, preserving the full swing operation of DPL while achieving a reduced transistor count [10]. Fig. 3(c) and (d) display 2-input DVL AND/OR gates, characterized by their full-swinging yet nonrestoring behavior. Assuming complementary inputs are available, both TGL and DVL gates require only 3 transistors. 
* In decoders, which are high fan-out circuits, TGL and DVL gates can contribute to reduced transistor counts when a few inverters can be shared by multiple gates. It's important to note the asymmetric nature of these gates; they lack balanced input loads. In TGL gates, input X controls the gate terminals of all 3 transistors, while input Y propagates to the output node through the transmission gate.
* In DVL gates, input X controls 2 transistor gate terminals, while input Y controls 1 gate terminal and propagates through a pass transistor to the output. The terms X and Y are referred to as the control signal and propagate signal of the gate, respectively.
* It's crucial to consider the choice of the propagate signal. Using a complementary input as the propagate signal is not recommended due to the added inverter increasing delay significantly.
* Therefore, for the inhibition (A'B) or implication (A' + B) functions, choosing the inverted variable as the control signal is more efficient. For the AND (AB) or OR (A + B) functions, either choice is equally efficient.
* Lastly, when implementing the NAND (A' + B') or NOR (A'B') functions, either choice results in a complementary propagate signal, by necessity.
  
## Transmission Gate Logic (TGL) and Differential Pass Transistor Logic (DVL): An Overview

* In the realm of digital circuit design, Transmission Gate Logic (TGL) and Differential Pass Transistor Logic (DVL) stand out as promising alternatives with distinctive characteristics.
  
**TGL AND Gate:** 
* In the TGL AND gate, the functionality is defined by input X, which controls the gate terminals of all three transistors.
* Simultaneously, input Y serves to propagate the signal to the output node through the transmission gate. This arrangement allows for the execution of the AND operation, 
where both inputs must be active to produce an output.

**TGL OR Gate:** 
* Similarly, the TGL OR gate utilizes input X to regulate the gate terminals of all three transistors. Meanwhile, input Y facilitates signal propagation to the output node through the transmission gate. 
* The resulting logic operation is an OR function, enabling the generation of an output when at least one of the inputs is active.
  
**DVL AND Gate:** 
* Differential Pass Transistor Logic (DVL) introduces a different paradigm. In the DVL AND gate configuration, input X takes charge of two transistor gate terminals, while input Y manages one gate terminal.
* The signal then propagates through a pass transistor to reach the output. This design allows for the execution of the AND operation with a unique structure, offering advantages in terms of transistor count and signal propagation.
  
**DVL OR Gate:**
* Similarly, the DVL OR gate follows a similar structure, with input X controlling two transistor gate terminals and input Y managing one gate terminal. The signal propagates through a pass transistor to the output.
* This configuration enables the implementation of the OR operation with distinctive characteristics, emphasizing efficiency and reduced transistor count. 
Both TGL and DVL gates exhibit an asymmetrical nature, lacking balanced input loads. In TGL gates, the control signal (X) dominates the gate terminals of all transistors, while the propagate signal (Y) manages signal propagation through the transmission gate.
* In DVL gates, the control signal (X) dictates the gate terminals, and the propagate signal (Y) governs signal flow through a pass transistor to the output.
* It's imperative to note that when considering a complementary input as the propagate signal, caution is warranted due to increased delay from added inverters. Consequently, the choice of the inverted variable as the control signal is deemed more efficient for certain logical functions.
* The flexibility in choosing the most suitable design makes TGL and DVL valuable components in the pursuit of optimized digital circuitry.
  
![5](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/91dc936a-642d-42fe-b38f-defbd0aeeb32)

## 14-Transistor 2–4 Low-Power Topology

* Designing an efficient 2–4 line decoder involves the consideration of Transmission Gate Logic (TGL) or Differential Pass Transistor Logic (DVL) gates. Typically, such designs require a total of 16 transistors, comprising 12 for AND/OR gates and 4 for inverters.
* However, by strategically combining both types of AND gates within the same topology and optimizing signal arrangement, it becomes possible to eliminate one of the inverters. This innovative approach reduces the total transistor count to 14.
* For instance, assuming the goal is to eliminate the B inverter from the circuit, specific choices for implementing minterms with DVL and TGL gates allow the complete avoidance of the complementary B signal. This results in a 14-transistor topology (9 nMOS and 5 pMOS).
* A similar procedure can be applied to OR gates, leading to the creation of a 2–4 inverting line decoder with 14 transistors (5 nMOS and 9 pMOS). The elimination of inverters not only reduces the transistor count but also minimizes logical effort and overall switching activity,contributing to decreased power dissipation.
* The resulting topologies are denoted as "2–4LP" and "2–4LPI," signifying "low power" and "inverting," respectively. Schematics for these 
topologies are presented in Fig. 4(a) and (b)

![6](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/d17b6fd7-b45c-4442-b75c-60d45304e63c)

## 15-Transistor 2–4 High-Performance Topology

* Building upon the success of low-power topologies, this section introduces high-performance topologies to address the drawback related to worst-case delay. Particularly, in scenarios 
where complementary A serves as the propagate signal, D0 and I3 can be efficiently implemented using static CMOS gates, eliminating the need for complementary signals.
* This modification involves a CMOS NOR gate for D0 and a CMOS NAND gate for I3, resulting in new 15-transistor designs with a significant improvement in delay while only slightly icreasing power dissipation.
* These high-performance designs are named "2–4HP" (9 nMOS, 6 pMOS) and "2–4HPI" (6 nMOS, 9 pMOS). The schematics for 2–4HP and 2–4HPI are presented in Fig. 5(a) and (b),respectively. The integration of these high-performance topologies showcases a balance between enhanced speed and manageable power dissipation.

![7](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/4107cc98-43c0-4084-8f90-fca8ef613966)

## Integration in 4–16 Line Decoders

* Pass Transistor Logic (PTL) stands out for its ability to implement logic functions with fewer transistors and reduced logical effort compared to CMOS. However, the cascading of PTL circuits can lead to performance degradation due to limitations in driving capability.
* To address this challenge, a mixed-topology approach is introduced, alternating between PTL and CMOS logic to potentially achieve optimal results.

![8](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/c1e5a87b-1270-4bcd-9408-a65cc462e284)
