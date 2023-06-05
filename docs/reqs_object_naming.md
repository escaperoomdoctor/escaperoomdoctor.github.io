# Escape room objects naming recommendations

The main purpose of this document is to create a unified mame system of escape room objects. This names will be used in a blueprints, wiring tables, schematics and so on.  

## ML – electromagnetic locks

- ML1.x - electromagnetic locks for the doors  
- ML2.x - electromagnetic locks for dropping things  
- ML3.x - electromagnetic locks for the caches  

## L – lighting

- L1.x - generic LED lamps  
- L2.x - LED strips  
- L3.x - LED RGB strips  
- L4.x - other lighting

## B – Buttons, other dry contact elements

- B1.x - service buttons  
- B2.x - game buttons, tumblers, limit switches

## T – Touchless sensors

- T1.x – reeds;  
- T2.x – RFID-sensors;  
- T3.x – resistance sensors: photoresistors (LDR), bend sensors, temperature sensors, and so on...  
- T4.1 – active sensors: barrier sensors, ray interrupt sensors, inductive sensors, pressure sensors, noise sensors, and son on...  

## G – Gadget

- Gx – gadget is not generic device, like moving or sistance sensor; also a set (group) of generic sensors withing one package can be implemented as a gadget.

## A - Audio

- Ax – audio amplifier;
- Ax.y – speakers for amplifier Ax  


## P – Props and decorations

- Px – decorations and props usually without electronics

## F – Furniture

- Fx – tables, chairs, closets, pedestals and so on...  

## Specific devices

- IRx – infrared receivers for remote control;  
- SGx – smoke generators;  
- TVx – TV screen;  
- Mx – motors, servo and step motors, моторы, actuators, vibromachines;  
- CAMx - camera for CCTV;  
- MICx - microphone for CCTV

## D – doors, hatches

- Dx – doors, hatches

## Rooms

Rooms usually marked as A, B, C, and so on. Game master room usually called as GM.

## Service equipment

- CS – queen control system for electronics control;  
- GMPC – game master PC or laptop;  
- CCTV - digital video recorders for Closed Circuit TeleVision

## Power bus

- 12VDC – 12V power supply;  
- 5VDC – 5V power supply;  
- VAC – 110/220V AC power supply

## Cable marking

Cables marking in most cases has the name of the target deice, but we use a special prefix '#', that defines a cable destination: P# - cable is used for power supply only, S# - cable is used for taking signal from the sensor and optionally for powering the sensors, I# - interface cable (audio, video, ethernet, usb, rs232, etc).
This prefix is useful because sometimes we trace several cables to the single device, for example, smoke generator SG1 is usually plugged over the power supply cable P#SG1 and control/signal cable S#SG1. For complex gadgets with a various electronics inside it is possible to specify cable type using the same prefix, gadget reference and exact cable destination point.
For example: P#G1:LOCK, S#G1:REED, I#G1:SOUND, and so on. In general, if we have only one cable to the device, for example power supply for theelectromagnetic lock ML1.1, it is allowed to simplify marking, like just ML1.1 label instead of P#ML1.1.
But it is recommended to specify a prefix in any case.  
