**This V1.1 version is not working.  The transistor is flipped on each channel and the DRV103's I got seem to be counterfeit.  Plan is to eventually swap both DRV103's to 556 timers and to a logic ic for flexible input control to reduce cost, eliminate the DRV issues, and simplify the whole project.**


# 2 Coil Economizer PCB
 This 2 Coil DRV103 Economizer PCB is not tested yet. It has at least 1 issue as when its soldered to + triggered the coil output is at 100% with the trigger wire floating. 

It was designed for contactor economizing, for 8-28v, and around 10 amps for each coil. This delivers full power for a short time to pull in the relay or contactor then switches over to a pulse output to conserve power, lower heat, etc. for the coil.
 ![V1 1 Top Populated](https://github.com/user-attachments/assets/db7c3354-906e-40de-8777-89bf283af7bd)

![V1 1 Top Bare](https://github.com/user-attachments/assets/aa17c632-6fea-4b23-9de4-7139a40128d3)


The frequency, duty cycle, and delay info is printed on the bottom of the pc board for reference.
![V1 1 Bottom](https://github.com/user-attachments/assets/837e7dc9-fd32-474a-b27d-c0c59181fe35)


Frequency is set to 25kHz by default.  Its recommended to keep it at 25kHz but can be adjusted from 25kHz down to 20kHz by cutting the 20/25kHz jumpers if required. The 20kHZ mod jumper (follow the silkscreen line to it) must also be soldered to adjust the voltage divider stack to work with the different pwm frequency load requirements of 20kHz for the DRV103 IC.

PWM Duty cycle is set to 21.8% by default, 3 jumpers are shorted on each coil circuit.  This is using voltage to set the duty cycle in the DRV103, a simulation of the circuit is here, https://everycircuit.com/circuit/4973018295828480  These can be cut if necessary.  If more than 21.8% is required more solder jumpers can be soldered.  Which gets cut or soldered doesn't matter as long as its in the silkscreened group. 
Number of jumpers shorted: 0 = 14.3%, 1 = 17%, 2 = 19.75%, 3 = 21.8%, 4 = 23.9%, 5 = 26%, 6 = 28%.  Looking at the top, the left 3 are shorted with a trace across them.

The DRV103 has an adjustable full on time then switches to pwm to hold the coil.  By default all 4 solder jumpers are shorted for a 550ms on time.  These jumpers can be cut to allow less full on time if required. Which gets cut or soldered doesn't matter as long as its in the silkscreened group.
Number of jumpers shorted: 0 = 110ms, 1 = 220ms, 2 = 330ms, 3 = 440ms, 4 = 550ms.

There is a trigger +/- jumper for each coil that needs to be soldered center pad to + or -.  Soldered to + it will turn on the coil with a + signal connected to Coil x trigger.  Soldered to -, it will turn on when the coil trigger is connected to -.  https://everycircuit.com/circuit/4812355044900864 is a simulation of the circuit.

There is an excel file with the calculated values of different DRV103 settings in the references folder.  
![Dimensions](https://github.com/user-attachments/assets/86a2aa7d-8ea3-4a44-9465-5b74aae55c33)



The oval slots are oversized for both 5mm and 5.08mm connectors.  This includes Phoenix Contact 1017509, 1751228, 1776260-8, etc. TE 521384-8, Faston tabs, and direct solder.  If direct solder is chosen the "teeth" at the bottom can be used as a strain relief with shrink tubing over them. They are 8mm wide at the bottom.  Small or single wires may require a second layer of shrink tubing.
![image](https://github.com/user-attachments/assets/44bd7d23-846b-430f-82da-d224c1807276)




Testing of the contactors should be done without high voltage connected.  A voltage of 10v or less should be considered for testing to verify the contactors will not accidently open from a low 12v battery. Watching for continuity the coil can be energized and running in pwm mode and hit down on a padded table (simulating a hard bump) with the high voltage terminals up.  There should be no break in continuity and should not open.

Pricey items are the tantalum capacitors that are recommended in the Ti DRV103 datasheet for higher power useage and a few extended JLC components with uncommon resistances.  The DRV103 ICs will likely need to be preordered from JLCPCB or populated later.  

These boards were about $30usd each from JLCPCB at a qty of 5 boards at the time of design.  
Designed in KiCAD 7 
Production files were made using Fabrication Toolkit, https://github.com/bennymeg/Fabrication-Toolkit to correct BOMs, rotations, etc. for JLCPCB.
https://yaqwsx.github.io/jlcparts/#/ was used to find available JLC components.


