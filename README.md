# 5-Stage-Current-starved-Ring-Oscillator
A 5 stage ring oscillator built in current starved topology to generate clock pulses required to drive a switch capacitor used as a substitute of resistors in a high order filter .

•	A voltage-controlled oscillator (VCO) is an electronic oscillator whose output frequency is proportional to the input voltage.

•	A range of waveforms with different frequencies can be obtained by varying the voltage applied at the input terminal. 

•	A voltage-controlled oscillator (VCO) is an electronic oscillator whose output frequency is proportional to the input voltage.

•	A range of waveforms with different frequencies can be obtained by varying the voltage applied at the input terminal. 
•	This project aims to design and implement a VCO at the IC level for generating clock pulses to drive a switched capacitor circuit, which can be used to replace a resistor in a filter circuit. 

•	Switched capacitor circuits are analog circuits that use switches and capacitors, rather than resistors, to perform signal processing functions such as filtering, amplification, and data conversion.

•	By switching a capacitor back and forth at a certain frequency, it emulates a resistor with an equivalent resistance inversely proportional to the sampling frequency where Req = 1/(FC)   ; F: sampling frequency , C:capacitance.

•	Therefore, to make a switched capacitor circuit behave like a resistor, it must be driven by two non-overlapping clock pulses of the same frequency.
•	Hence, to generate the clock, it is necessary to design a VCO.

•	A ring oscillator with three buffer inverters is used to improve the output..

•	A PMOS transistor acting as a current source is used in place of VCC in the ring oscillator.

•	The PMOS current source can be controlled by adjusting the gate voltage Vg.

•	This helps control the charging time of the parasitic capacitances of the MOSFETs used in the ring oscillator.

•	To reduce the high output frequency to a desired range, a master-slave D flip-flop is used. The complement of the output Q' is connected to the D input, and the output of the ring oscillator (after buffering) is used as the clock input to the flip-flop.

•	This flip-flop divides the clock frequency by half and generates waveform with 50% duty cycle. 

•	No external capacitors are used in the circuit. The oscillation is achieved using the inherent parasitic capacitances of the MOSFETs present in the ring oscillator. 

•	Initially, a T flip-flop was used instead of a master-slave D flip-flop. However, it did not work properly because the output of the ring oscillator was not providing clean, well-defined clock edges required for reliable edge-triggered operation. As a result, the T flip-flop produced unstable or incorrect frequency division.

•	We also tried to control the discharging time of the parasitic capacitors using an NMOS current source instead of ground in the ring oscillator. However, this approach failed due to unstable behavior, as it entered the cutoff region under certain conditions.

•	In another approach, the circuit was implemented without a D flip-flop and instead used external capacitors. Although oscillations were obtained, the duty cycle was significantly greater than 50%. Since our objective was to achieve a duty cycle close to 50%, this approach was not suitable, leading us to use a D flip-flop for frequency division and duty cycle correction.

CIRCUIT DESIGN FOR RING OSCILLATOR WITH BUFFER
<img width="940" height="351" alt="image" src="https://github.com/user-attachments/assets/569c632e-b6e9-4085-8825-1a47d1bd35b2" />


CIRCUIT DESIGN OF MASTER SLAVE D-FLIP FLOP:
<img width="858" height="395" alt="image" src="https://github.com/user-attachments/assets/e672a9b8-d34d-49c5-a687-01316ada6f3f" />

 
Circuit and output waveform of VCO using external capacitors (without D flip-flop), showing a duty cycle greater than 50%.
<img width="602" height="206" alt="Picture1" src="https://github.com/user-attachments/assets/b46963a3-d439-44d5-9da6-f7c838eb9cd5" />



 


