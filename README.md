# AHB2APB-BRIDGE-1-MASTER---1-SLAVE-PROJECT

Hi Everyone!!!

This is an project based on AMBA (Advanced Microcontroller Bus Architecture) Protocol.

The Advanced Microcontroller Bus Architecture (AMBA) is an open System-on-Chip bus protocol for high performance buses to communicate with low-power devices. In the AMBA High performance Bus (AHB) a system bus is used to connect a processor, a DSP, and high performance memory controllers whereas the AMBA Advanced Peripheral Bus (APB) is used to connect (Universal Asynchronous Receiver Transmitter) UART. It also contains a Bridge, which connects the AHB and APB buses. Bridges are standard bus-to-bus interfaces that allow IPs connected to different buses to communicate with each other in a standardized way. 

![image](https://github.com/user-attachments/assets/310b449f-597e-46b3-83ac-f7be29366b5d)
      
# AHB (AMBA High Performance Bus) 
 
AMBA AHB is a bus interface suitable for high-performance synthesizable designs. It defines the 
interface between components, such as masters, interconnects, and slaves.  
 
AMBA AHB implements the features required for high-performance, high clock frequency systems 
including:  
  • Burst transfers 
. • Single clock-edge operation 
. • Non-tristate implementation 
. • Wide data bus configurations, 64, 128, 256, 512, and 1024 bits. 
 
 The most common AHB slaves are internal memory devices, external memory interfaces, and 
high-bandwidth peripherals. Although low-bandwidth peripherals can be included as AHB slaves, 
for system performance reasons, they typically reside on the AMBA Advanced Peripheral Bus 
(APB). Bridging between the higher performance AHB and APB is done using an AHB slave, 
known as an APB bridge.


# AHB Master Interface 
 
A master provides address and control information to initiate read and write operations
![image](https://github.com/user-attachments/assets/818fa2e5-bded-46a5-a9c0-d1c199480769)


# AHB Slave Interface 
 
A slave responds to transfers initiated by masters in the system. The slave uses the HSELx select 
signal from the decoder to control when it responds to a bus transfer. 
 
 The slave signals back to the master: 
 • The completion or extension of the bus transfer. 
 • The success or failure of the bus transfer. 
![image](https://github.com/user-attachments/assets/c91c9d83-bd69-485b-8d49-52255936db39)


# APB (Advanced Peripheral Bus) 
 
The Advanced Peripheral Bus (APB) is part of the Advanced Microcontroller Bus Architecture 
(AMBA) protocol family. It defines a low-cost interface that is optimized for minimal power 
consumption and reduced interface complexity.  
 
The APB protocol is not pipelined, use it to connect to low-bandwidth peripherals that do not 
require the high performance of the AXI protocol.  
 
The APB protocol relates a signal transition to the rising edge of the clock, to simplify the 
integration of APB peripherals into any design flow. Every transfer takes at least two cycles.  
The APB can interface with: 
 
• AMBA Advanced High-performance Bus (AHB)  
• AMBA Advanced High-performance Bus Lite (AHB-Lite)  
• AMBA Advanced Extensible Interface (AXI)  
• AMBA Advanced Extensible Interface Lite (AXI4-Lite)  
 
You can use it to access the programmable control registers of peripheral devices. 


# Architecture 
 
The main sections of this module are: 
 • AHB slave bus interface  
 • APB transfer state machine, which is independent of the device memory map 
 • APB output signal generation. 

![image](https://github.com/user-attachments/assets/a194ad2a-5c50-4fa9-a79e-009f4fb49a1d)


To add new APB peripherals, or alter the system memory map, only the address decode sections 
need to be modified.  
 
The base addresses of each of the peripherals (timer, interrupt controller, and remap and pause 
controller) are defined in the AHB to APB bridge interface, which selects the peripheral according 
to its base address. The whole APB address range is also defined in the bridge.  
 
These base addresses can be implementation-specific. The peripherals standard specifies only the 
register offsets (from an unspecified base address), register bit meaning, and minimum supported 
function  
 
The APB data bus is split into two separate directions:  
 
• read (PRDATA), where data travels from the peripherals to the bridge 
• write (PWDATA), where data travels from the bridge to the peripherals.  
 
This simplifies driving the buses because turnaround time between the peripherals and bridge is 
avoided. In the default system, because the bridge is the only master on the bus, PWDATA is driven 
continuously. PRDATA is a multiplexed connection of all peripheral PRDATA outputs on the bus, 
and is only driven when the slaves are selected by the bridge during APB read transfers.  
 
It is possible to combine these two buses into a single bidirectional bus, but precautions must be 
taken to ensure that there is no bus clash between the bridge and the peripherals. 




# RTL SYNTHESIS 

![image](https://github.com/user-attachments/assets/e5167768-b51c-44aa-acb0-1dffda171576)


# STATE DIAGRAM 

![image](https://github.com/user-attachments/assets/9d1709c1-4eab-414d-ab36-923e55d21b81)


Hope you understood the project outline and some key features through this file!

