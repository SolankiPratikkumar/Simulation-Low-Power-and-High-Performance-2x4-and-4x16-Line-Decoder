
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

# SIMULATIONS

* In this phase, we conduct rigorous BSIM4-based SPICE simulations at the schematic level to the newly proposed mixed-logic decoders with conventional CMOS counterparts. 
Employing a 45 nm PTM LP predictive technology model for low-power applications ensures a realistic representation, incorporating high-k/metal gate and stress effects.
* To maintain fairness in the evaluation, all decoders utilize unit-size transistors with consistent dimensions (Ln = Lp = 45 nm, Wn = Wp = 120 nm).
* The analysis covers aspects like transistor count, power dissipation, delay characteristics, and signal integrity, providing a nuanced understanding of the proposed designs in 
comparison to traditional CMOS implementations.

##  Simulation Setup

* To comprehensively evaluate the performance of the proposed mixed-logic decoders against traditional CMOS counterparts, a series of rigorous simulations are conducted.
* The simulations cover a range of frequencies (0.5, 1.0, 2.0 GHz) and voltages (0.8, 1.0, 1.2 V), totaling nine scenarios. Each simulation is iterated five times, introducing variations in temperature (-50, -25, 0, 25, and 50 ◦C), with the average power/delay calculated and reported for each case.
* Balanced inverters (Ln = Lp = 32 nm, Wn = 120 nm, Wp = 240 nm) buffer all inputs, and a standardized output loading is applied with a capacitance of 0.2 fF, as illustrated in Fig. 7. The inputs are subjected to proper bit sequences, ensuring coverage of all feasible transitions a decoder can execute.
* For instance, a 2–4 decoder with 2 inputs can generate 4 different binary combinations (22 = 4), resulting in 16 possible transitions.

#  Schematics  

## 2x4 CMOS DECODER

![9](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/6fc733d9-34b2-4eb9-b39e-487e5b35f42a)

## 2x4 CMOS INVERTER DECODER

![10](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/6ae7a5f0-d58a-4188-8b3d-c4102edafcad)

## 4x16 CMOS DECODER:

![11](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/c488e496-3784-43ff-bc5c-4092176d57ef)
![12](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/d7e802cf-0e2f-4ba7-8feb-ba566d81804b)

## 4x16 CMOS INVERTER DECODER:

![13](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/da2236a6-69eb-4ce5-b40e-989043a07642)
![14](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/ad98ae97-7323-4fa9-9a24-7b4b60ed09f5)

## 4X16 LPI DECODER:

![15](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/0559f722-4938-4777-a97f-851672e6c514)
![16](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/1b543fbe-6c24-4ce0-b7d6-4375e0547baa)

## 2X4 HP DECODER:

![17](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/444a6e53-1348-4a42-9876-b178d47e6376)

## 2X4 HPI DECODER:

![18](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/0f84ed19-ff1e-4679-8fd9-ee2cca414a2e)

## 4x16 HP DECODER:

![19](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/d8842035-ad8f-4166-968d-c0f7e7a3f601)
![20](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/4dd96ca7-f88d-4b31-a1a5-fb06b71a190f)

# Output Waveforms:

## 2x4 CMOS DECODER:

![21](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/ca0fdfd3-4fc9-44f1-adf5-2b22bfd90dab)

## 2x4 CMOS INVERTED DECODER:

![22](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/a0d5a622-36e6-4b03-b95e-f325246009f2)

## 2x4 LOW POWER DECODER:

![23](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/cbeb6a9a-0920-45fd-bc0b-0d494d7869eb)

## 2X4 LOW POWER INVERTED DECODER:

![24](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/051e81b6-f6bd-41b5-99b8-9afe09c91c82)

## 2X4 HIGH PERFORMANCE DECODER:

![25](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/cd8c0f50-4052-4c88-adb5-fee0c58abf4e)

## 2X4 HIGH PERFORMANCE INVERTED DECODER:

![26](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/f5fce8ba-df24-4316-b26b-d93e66ae1264)

## 4x16 CMOS DECODER:

![27](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/932228dc-c3ea-428e-82cf-68677c1f9dbd)
![28](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/b0c91870-697e-461c-8ad7-9e1e66254a53)
![29](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/28e102a3-3eab-4750-86f7-b7a7de61817a)
![30](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/9955ac14-dc6a-450a-99e7-4abc59f51203)

## 4x16 CMOS INVERTER DECODER:

![31](https://github.com/SolankiPratikkumar/Simulation-Low-Power-andxHigh-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/e70b8739-d740-4d02-9f50-8d20a8305a9d)
![32](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/4b960b44-6592-4121-9a70-1c33a9bc128f)
![33](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/d509d6d7-20ce-4652-9bb5-152b9521e5a9)
![34](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/38e4fd91-1148-4713-9de7-d755901ab635)

## 4x16 LOW POWER DECODER:

![35](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/434601cd-5aca-4715-9f2b-a131cff3890b)
![36](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/3c5ab827-26e9-4f69-8354-47ee9b738847)
![37](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/85afdd05-26f4-46a6-a8bb-bc58610ce0ab)
![38](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/15a2a4c5-78d5-4895-a730-82eed3f6a32a)
![39](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/0b8eb00f-76c5-4c4a-9776-d880825e77ef)

## 4x16 LOW POWER CALCULATION DECODER:

![40](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/bdc9fd82-4845-4ca0-952b-33478c534643)
![42](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/342a2c11-e6d0-4bd2-b983-5997a2dda0da)
![43](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/11edf4e6-8b21-4ce0-ad6a-3bd50cc9eb1d)
![44](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/543fc706-6c3a-4f91-837d-cf529b2d90b8)
![45](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/99273f6d-bde6-40fa-8d7c-ea03a96413fc)

## 4x16 HIGH PERFORMANCE DECODER:

![46](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/2138d0b0-01fb-408f-a757-638ce2d490ef)
![47](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/0435aa18-5035-4b97-b032-7becaf0a4ac8)
![48](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/2face457-0c52-4fbf-ad87-bf80032cac23)
![49](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/796fc7e3-5d7c-4318-abcb-60c4363dd6bf)
![50](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/0e6d8df0-bb76-4d7f-8f48-ea6280a9ef32)

# 4x16 HIGH PERFORMANCE INVERSE DECODER:

![51](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/238731e1-94ba-42f8-bf99-8b98c2b7ccab)
![52](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/83f1447a-d580-4dc4-80d0-c3ec7b88a49e)
![53](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/215a9a59-2aec-478e-ac5b-176698004d2a)
![54](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/2f0136d1-42b5-4244-a78e-d785760f0fac)
![55](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/2c076354-5721-43de-8f28-8a61852b5d70)

# Observation Table:

**Propagation Delay**

![56](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/accb324a-4a0e-45a7-b091-b09a7f06cc38)
![57](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/cbb0586c-162d-4070-83eb-c8bf919ac8c7)
![58](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/87dd661f-2895-4132-b7fe-405535c06e24)
![59](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/56a6fbbe-3934-4014-bb33-158088f33ecd)

**Power Dissipation** 

![60](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/72f6f303-7133-4d04-adbd-702ec3779003)
![61](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/d01acdcf-8ae9-4411-90fd-c3e02fd8ab32)
![62](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/f64ba9b4-0b08-4b02-bb3c-8f1d62759767)
![63](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/d245a979-0765-47a4-8313-5191c938a608)
![64](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/e7224f1b-8b0b-452d-81c8-4db2a322309f)

**Power Delay Product**

![65](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/d320f5c2-87d4-415a-85cf-fbb4fbbb5a94)
![66](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/c7e51bdf-c807-4ccb-9469-1ec10c290c3e)
![67](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/1b86229a-4413-4bd1-be69-ad292f41a012)
![68](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/c40727fc-0336-4fb0-9e94-32fcd2ad502b)
![69](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/f18053d5-14de-49f7-b87d-c475c509f035)

# Conclusion:

## Delay

![70](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/a2d9880d-8c65-4337-9172-13d7890b0cc6)
![71](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/6c5baff0-7d22-46f5-a70a-e5dc0fa9adf6)

## Power Dissipation

![72](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/f86504b6-3f51-4d97-be8e-71e69641feaf)
![73](https://github.com/SolankiPratikkumar/Simulation-Low-Power-and-High-Performance-2x4-and-4x16-Line-Decoder/assets/140999250/aad603b1-dcbd-44db-a434-e6f514849f81)

# Word of Thanks

I sincerely Thanks to Prof.Madhav Rao for Teaching and Helping me to complete this Course smoothly

# Reference

* https://ieeeprojectsmadurai.com/IEEE%202019%20VLSI%20BASEPAPERS/Design%20of%20Low%20Power,%20High%20Performance%202-4.pdf
* CMOS VLSI Design: A Circuits and Systems Perspective by Weste/Harris (Author)

# Acknowledgement of Group

* Nitesh Sharma, M.Tech IIITB Colleague
* Akhil Ganesh Asati, M.Tech IIITB Colleague
* Vaibhav Tiwari, M.Tech IIITB Colleague
