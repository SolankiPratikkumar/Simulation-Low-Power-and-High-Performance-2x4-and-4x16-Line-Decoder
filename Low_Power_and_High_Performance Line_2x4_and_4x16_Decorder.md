
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

![IR-sensor-Working](https://github.com/SolankiPratikkumar/IIITB_PRATIKKUMAR_ASIC/assets/140999250/f4c65e8b-b122-4a53-909c-bee121a5c4cf)

* Then that signal is passed through the potentiometer to meet the distant object up to 500cm and the obtained signal is kept as an input to the RISC-V core which will process the signal and provide output to the Buzzer and LED.
* So, by this process, we would get the detection of a moving object and our output target will be met

**Details IR Sensor Module Circuit Diagram**

![How-to-make-IR-Sensor-Module-Circuit-Diagram](https://github.com/SolankiPratikkumar/IIITB_PRATIKKUMAR_ASIC/assets/140999250/70e12018-2a69-44f8-ae4b-11d4439fee29)

* When the Photodiode receives reflected infrared light, its resistance significantly decreases, leading to a drop in voltage across the photodiode. This higher voltage is then directed to the Inverting input of the LM393/LM358 IC.
* Subsequently, the IC compares this voltage with the threshold voltage. In this scenario, the Inverting input voltage surpasses the Non-Inverting input voltage, causing the IC output to be Low. Consequently, the sensor output registers as Low
* On the other hand, if the Photodiode or IR receiver (IR-RX) fails to detect infrared light, the photodiode's resistance becomes very high. As a result, a lower voltage from the photodiode is supplied to the Inverting input of the IC. The LM393/LM358 IC then compares this voltage with the threshold voltage.
* In this situation, the Inverting input voltage is less than the Non-Inverting input voltage, leading to a High output from the IC. Hence, the sensor output is recognized as High.

![downloadirsensorrrrrr](https://github.com/SolankiPratikkumar/IIITB_PRATIKKUMAR_ASIC/assets/140999250/a65b808c-c264-4c35-b55a-f99d602d5d5c)

* The IR sensor is equipped with an integrated variable resistor, specifically a 10k preset. This component serves the purpose of configuring the operational range. By turning the preset knob, which is adjustable, the detection distance can be set within an effective range.
  
* Clockwise rotation of the preset knob extends the detection range, while counterclockwise rotation reduces it.
  

![IR-Sensor-Module-Sensitivity-set](https://github.com/SolankiPratikkumar/IIITB_PRATIKKUMAR_ASIC/assets/140999250/f7923c27-cb3f-4615-b1c9-81bce4acd238)

## GPIO PINS:

![Screenshot from 2023-12-09 15-08-44](https://github.com/SolankiPratikkumar/IIITB_PRATIKKUMAR_ASIC/assets/140999250/b2730883-9460-497e-9787-24667c4378bf)

* x30[0] is the input pin where the sensor value is received
* x30[1] is pin to provide output and it will blink output LED
* x30[2] is pin to provide output and it will sound output Buzzer
  
