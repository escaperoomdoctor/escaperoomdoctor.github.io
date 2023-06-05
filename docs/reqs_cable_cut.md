# Cables parameter estimation


## Theory 

If you're not interested in the theory you can skip this chapter and go directly to the _Summary_ chapter, otherwise lets begin...
We recommend to use safety voltage for most escape room devices and the following calculation will base on 12V (as for another voltages - the concept will be similar).
Assuming the target device should have not less than 5% of 12V (it's about 11.5V), the maximum voltage drop on the cable should be 12V-11.5V=0.5V (this is our criteria).
Assuming the target device has maximum power consumption «Pmax» Watt, so the maximum current should be estimated as Imax=Pmax/12. If device has Imax parameter specified we can use it directly.

So, we have: maximum cable voltage drop dU=0.5V, maximum current is Imax, or calculating it from Imax=Pmax/12. In accordance with the Ohm's law maximum cable resistance must be R = dU / Imax = 0.5 / Imax. From the other hand, cable resistance can be calculated by the next formula: R = 2 * p * L / S, where is p – specific resistance (it is always equal to 0.018 for copper), L – cable trace length, S – cable cut in square millimiters (mm2) – target value, and then we multiply everything by 2, because the cable consists of two wires and the current flows on both of them). Using the both of formulas above, we get:  
0.5/Imax = R = 0.036 * L / S, and the results are:  
S = 0.072 * L * Imax,  or  
S = 0.006 * L * Pmax;  
these formulas show the same (just depending on the source parameter Imax or Pmax).  


## Samples 

**P1**. We have 15 meters of LED-strip, cable length L=5 meters from the power supply. Assuming the power of LED strip 14.4 W/m, 15 meters has a consumptions 14.4 * 15 = 216W. Minimal cable cut can be estimated: S = 0.006 * 5  * 216; this is about 6mm2. If we take, for example, a cable with cut 3mm2, we would have a voltage drop about 1V instead of 0.5V, and the LEDs will have only 11V of 12V. This will force a little cable heat and LEDs will have a less brightness;  
**P2**. We have an electromagnetic lock for 500kg hold, cable length, for example, L=5 meters from the power supply, Imax=0.5A. Minimal cable cut can be estimated: S = 0.072 * 15  * 0.5; this about 0.5mm2.  


## Summary

QUEEN system was designed such way, the control system (CS) containing power supplies, can be setup close to the escape room to reduce cable length, and game master can control the room via local area network (LAN) like Ethernet.
Therefore the cable length is usually within 5-10 meters from the CS. Due to this, we made a table with estimated cables cut.
It allows to select a required cable parameters for most cases without complex engineering calculations and qualification:  

| Device                         | Cable recommendation                                           |
|--------------------------------|----------------------------------------------------------------|
| audio speaker                  | 2x4.0                                                          |
| CCTV microphone                | 3x1.5                                                          |
| CCTV camera                    | specific cable like IVUE CPV-40AHD, is usually supplied in box |
| electromagnetic lock           | 2x1.5                                                          |
| led strip 5m                   | 2x1.5                                                          |
| RGB led strip 5m               | 4x1.5                                                          |
| reeds, buttons, limit switches | 2x0.75                                                         |
| active sensors, RFID           | 3x1.5                                                          |
| 12VDC/5VDC power supply        | 2x1.5                                                          |
| 220/110VAC power supply        | 3x1.5                                                          |
| Ethernet/RS485                 | FTP/UTP                                                        |





