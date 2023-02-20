# CANSentry: Securing CAN-Based Cyber-Physical Systems against Denial and Spoofing Attacks
## Introduction
**CAN** was designed without encryption and authentication.

**CAN** protocol is broadcast by nature. A malicious message injected by a compromised ECU will be treated as legitimate message and broadcasted over network.

Wireless communication capabilites have been added to **CAN** nodes which enlarges the attack vector for remote attacks.

Solutions such as message authentication and intrusion detection systems have been proposed, but *suffer from efficiency issues* aka. they significantly impact CAN's transmission speed.

Introduces **CANSentry** which addresses problems with protocos broadcast nature without demanding modifications to the **CAN** standard or the ECUs

## Background and Related Work
#### CAN Specification
**CAN** network consists of interconnected nodes. 

Each node is controlled by ECU.

Each node connects to bus through a *controller* and a *tranceiver*.
* Controller is a standalone circuit or an ECU module
* Tranceiver converts between logic sate and physical bits.

**Frame Prioritization:**\
Frame prioritization is realized by **CAN** ID.
Frame starts with ID. When multiple transmit at one time the lowest ID represents priority and wins the arbitration.\
Dominant - '0'\
Recessive - '1'\
When Dom. and Rec. are sent at the same time the dominate bit will dominate the bus. 

**CAN Error Handling:**\
**CAN** nodes automatically detect and resolve transmission errors without 3rd party intervention.\
5 types of errors in **CAN**: bit, ACK, stuff, form, and CRC errors.\
Each ECU keeps track of transmission and receiving errors:
- transmit error counter (TEC)
- receive error counter (REC)

When a node encounters persistent transmission errors its switches to **bus-off** state resulting in isolation from the **CAN** bus. 

#### Existing CAN Attacks
**Bus Denial**

