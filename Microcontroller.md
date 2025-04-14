A small computer on a single integrated circuit. Microcontrollers make it practical to create small sensing and actuating devices without the need of connecting a full computer for that purpose.

Microcontrollers are usually used for automatically controlled devices. Some of these uses include sensonsr in cars, data collection systems, recome controls, appliances, implantable medical devices.

Microcontrollers operate a slower speeds that cpus in modern computers with the Arduino ONE working a 20MHz, and some mcu even working as slow as 4 kHz. The amount of ram is also reduced. 

# Programs in MCUs

Programs in mcus are different from programs in regular computers in the following ways:

1. No runtime for you program, which means that every feature that you need from a kernel needs to be implemented if it is not supported by the chip.
2. Battery management: Cycles count for energy consumption.
3. Debugging is harder.
4. mcus need to handle external signals that also need to be mocked for testing purposes.