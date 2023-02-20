# Vehicle Security: A Survey of Security Issues and Vulnerabilities, Malware Attacks and Defenses

### Introduction:

* ECUs are cruicial to the modern cars functionality and comfort
* Physicaly access is one attack vector into CAN Bus
    - OBD + OBD-II dongles, CD Players, USB
* Wireless Access is ever-present and growing attack vector
    - Bluetooth, Wi-Fi, Cellular, LTE, and 5G
    - **Vehicles are not longer closed systems**
    -  Key fobs, Radio Signals, OTA ECU firmware updates, compromised phones,

### Intelligent Vehicle Architecture:

#### In-Vehicle Network Architecture
**Controller Area Network (CAN):**

Created in the 80's in order to provide fast and reliable communication between ECUs. It created durable and inexpensive communication between ECUs and simplified complicated electrical harnesses.

CAN is a BUS, aka. all devices connected on the bus recieve all can frames. They are identified with an **arbiration ID**

With CAN modern cars can fit many ECUs.

Not all ECUs use CAN protocol. Various electronic subsystems use various communication protocols.
* Time senstive engine control, etc. use **CAN**
* fewer safety subsystems, etc. use **LIN**
* In-Vehicle Infotainment (radio, navigation, Bluetooth) use **MOST** or **AE**
    - **AE** 100x faster than **CAN**

**CAN** adopts Carrier Sense Multiple Access / Collision Advoidance

**CAN** does not have addressing scheme like TCP/IP

When ECUs broadcast their CAN messages each message frame is allocated a unique identifier, known as CAN ID or arbitration ID, which defines the priority and the content of the message frame.

If two ECUs send CAN message at same time, highest priority ID Wins.

### CAN Frames:

 Four major types of CAN frames:\
**remote frame** - used to enable an ECU to request the data from specified ECU \
**overload frame** - used to inform that the source ECU cannot recieve the data\
**data frame** - used to carry the data from the transmitter ECU to the reciever ECU\
**error frame** - used to inform other ECUs regardging that happened error

#### Data Frame:

**SOF:** contains dominate bit and informs start of transmission to all ECUs.\
**Arbitration Field:** consists of 11 bit identifier and last bit as remote transmision request (RTR)--- characterizes priority and the type of the frame.\
**Control Field:** two reserved bits and four bits as data length code (DLC).\
**Data Field:** includes the actual data in a range 0-64 bytes.\
**Cyclic Redundancy Check:** 15 bits as CRC and 1 bit as CRC delimiter and performs the data error detection.
**ACK Field:** one bit as ACK part and one bit ACK delimiter.
**EOF:** 7 bits --- indicated the end of the CAN frame by a recessive bit flag.

|SOF(1)|IDENTIFIER(11)RTR(1)|IDE(1)RB(1)DLC(4)|DATA(0-64)|CRC(15)CRCDEL(1)|ACK(1)ACKDEL(1)|EOF(7)|
|------|--------------------|-----------------|----------|----------------|---------------|------|


### The Vulnerabilities of Intelligent Vehicles
1. **Direct Physical Access**
    - On-Board Diagnostics system (OBD, OBD-II) can provide direct access to the vehicle's ECUs and ints internal network busses
2. **Indirect Physical Access**
    - CD, USB, and connected devices
3. **Short Range Wireless Access**
    - Bluetooth, Remote keyless entry, Dedicated Short Range Com. (DSRC) and Wi-Fi
4. **Long Range Wireless Access**
    - GPS, Traffic Message Channel, Satellite Radio, Digital Radio
    - Phones connected to cars act as a means to long range wireless access

### Potential Ways for Malware to Infect the System
Several factors: Weaknesses in the design of the software, weakness in the hardware, weakness in the in-vehicle application, weakness in the in-vehicle network (CAN), The driver’s inability to protect document downloads into the vehicle when the driver accesses websites and downloads apps from external sources, external information may be laced with weaknesses that can enter a vehicle, for example, a software update bundle that can be infected with malware before it gets stacked onto a vehicle, weaknesses in the operating systems utilized on the vehicles. 

### Existing Defense Techniques Against Malware

