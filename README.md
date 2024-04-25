# 2 Coil Economizer PCB
 This 2 Coil DRV103 Economizer PCB is not tested yet. It was designed for contactor economizing, for 8-28v, and up to 3amps for each coil. This delivers full power for a short time to pull in the relay or contactor then switches over to a pulse output to conserve power, lower heat, etc. for the coil.
 
![Top W Components](https://github.com/jrbe/2-Coil-Economizer-PCB/assets/6788692/98a25e71-799f-4389-b64f-370ec5466bcd)

The frequency, duty cycle, and delay info is printed on the bottom of the pc board for reference.
![Bottom](https://github.com/jrbe/2-Coil-Economizer-PCB/assets/6788692/e96845b8-2c22-4636-9ee4-326cc1f39613)

Frequency is set to 25kHz by default.  Its recommended to keep it at 25kHz but can be adjusted from 25kHz down to 20kHz by cutting the 20/25kHz jumpers if required. The 20kHZ mod jumper (follow the silkscreen line to it) must also be soldered to adjust the voltage divider stack to work with the different pwm frequency load requirements of 20kHz.

PWM Duty cycle is set to 21.8% by default, 3 jumpers are shorted on each coil circuit.  This is using voltage to set the duty cycle in the DRV103, a simulation of the circuit is here, https://everycircuit.com/circuit/4973018295828480  These can be cut if necessary.  If more than 21.8% is required more solder jumpers can be soldered.  Which gets cut or soldered doesn't matter as long as its in the silkscreened group. 
# of jumpers shorted: 0 = 14.3%, 1 = 17%, 2 = 19.75%, 3 = 21.8%, 4 = 23.9%, 5 = 26%, 6 = 28%.  Looking at the top, the left 3 are shorted with a trace across them.

The DRV103 has an adjustable full on time then switches to pwm to hold the coil.  By default all 4 solder jumpers are shorted for a 550ms on time.  These jumpers can be cut to allow less full on time if required. Which gets cut or soldered doesn't matter as long as its in the silkscreened group.
# of jumpers shorted: 0 = 110ms, 1 = 220ms, 2 = 330ms, 3 = 440ms, 4 = 550ms.

There is a trigger +/- jumper for each coil that needs to be soldered center pad to + or -.  Soldered to + it will turn on the coil with a + signal connected to Coil x trigger.  Soldered to -, it will turn on when the coil trigger is connected to -.  https://everycircuit.com/circuit/4812355044900864 is a simulation of the circuit.

There is an excel file with the calculated values of different DRV103 settings in the references folder.  

![PCB Editor](https://github.com/jrbe/2-Coil-Economizer-PCB/assets/6788692/60f5f5f9-a017-4502-9318-11ef87b979f1)

The oval slots are oversized for both 5mm and 5.08mm connectors.  This includes Phoenix Contact 1017509, 1751228, 1776260-8, etc. TE 521384-8, Faston tabs, and direct solder.  If direct solder is chosen the "teeth" at the bottom can be used as a strain relief with shrink tubing over them. They are 8mm wide at the bottom.

Testing of the contactors should be done without high voltage connected.  A voltage of 10v or less should be considered for testing to verify the contactors will not accidently open from a low 12v battery. 

Pricey items are the tantalum capacitors that are recommended in the Ti DRV103 datasheet for 3A useage and a few extended JLC components with uncommon resistances.  The DRV103 ICs will likely need to be preordered from JLCPCB or populated later.  There is a large heatsink for these IC's making hand soldering challenging.  

These boards were about $14 each from JLCPCB at a qty of 5 boards at the time of design.  Designed in KiCAD 7 using Fabrication Toolkit, https://github.com/bennymeg/Fabrication-Toolkit to correct BOMs, rotations, etc. for JLCPCB.


