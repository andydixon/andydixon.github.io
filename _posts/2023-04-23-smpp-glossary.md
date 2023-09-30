---
id: 3928
title: 'SMPP Glossary'
date: '2023-04-23T13:29:07+01:00'
author: Andy
layout: post
guid: 'https://www.andydixon.com/?p=3928'
permalink: /smpp-glossary/
categories:
    - Tech
---

The Short Message Peer-to-Peer (SMPP) protocol is a telecommunications industry protocol for exchanging SMS messages between Short Message Service Centers (SMSCs) and/or External Short Messaging Entities (ESMEs). It is a level-7 TCP/IP protocol that allows fast and efficient delivery of SMS messages. Here’s a glossary of some common SMPP commands:

1. bind\_transmitter (0x00000002): Initiate a bind operation with an SMSC as a transmitter.
2. bind\_transmitter\_resp (0x80000002): Response to the bind\_transmitter command.
3. bind\_receiver (0x00000001): Initiate a bind operation with an SMSC as a receiver.
4. bind\_receiver\_resp (0x80000001): Response to the bind\_receiver command.
5. bind\_transceiver (0x00000009): Initiate a bind operation with an SMSC as both a transmitter and receiver.
6. bind\_transceiver\_resp (0x80000009): Response to the bind\_transceiver command.
7. unbind (0x00000006): Close an active SMPP session.
8. unbind\_resp (0x80000006): Response to the unbind command.
9. submit\_sm (0x00000004): Submit a short message to an SMSC for onward delivery.
10. submit\_sm\_resp (0x80000004): Response to the submit\_sm command.
11. deliver\_sm (0x00000005): Deliver a short message to an ESME for onward delivery.
12. deliver\_sm\_resp (0x80000005): Response to the deliver\_sm command.
13. data\_sm (0x00000103): Exchange data between an ESME and an SMSC.
14. data\_sm\_resp (0x80000103): Response to the data\_sm command.
15. query\_sm (0x00000003): Query the status of a previously submitted short message.
16. query\_sm\_resp (0x80000003): Response to the query\_sm command.
17. cancel\_sm (0x00000007): Cancel a previously submitted short message.
18. cancel\_sm\_resp (0x80000007): Response to the cancel\_sm command.
19. replace\_sm (0x00000008): Replace the contents of a previously submitted short message.
20. replace\_sm\_resp (0x80000008): Response to the replace\_sm command.
21. enquire\_link (0x00000015): Check the status of an active SMPP session.
22. enquire\_link\_resp (0x80000015): Response to the enquire\_link command.
23. alert\_notification (0x00000102): Notify an ESME of an event.
24. generic\_nack (0x80000000): Indicate an error or an inability to process an unrecognized or unsupported SMPP command.

Note that the command IDs are provided in hexadecimal format – which can be used with wireshark – eg smpp.command\_id=0x002 for filtering down to only bind\_transmitter PDUs.

1. bind\_transmitter: 
    - system\_id: Identifies the ESME system requesting to bind.
    - password: The password used to authenticate the ESME system.
    - system\_type: Indicates the ESME’s type or role.
    - interface\_version: The SMPP version supported by the ESME.
    - addr\_ton: The Type of Number of the ESME’s address range.
    - addr\_npi: The Numbering Plan Indicator of the ESME’s address range.
    - address\_range: The ESME’s address range.
2. bind\_receiver: 
    - (Same parameters as bind\_transmitter)
3. bind\_transceiver: 
    - (Same parameters as bind\_transmitter)
4. unbind: 
    - No additional parameters required.
5. submit\_sm: 
    - service\_type: Indicates the SMS service type.
    - source\_addr\_ton: The Type of Number of the sender’s address.
    - source\_addr\_npi: The Numbering Plan Indicator of the sender’s address.
    - source\_addr: The sender’s address.
    - dest\_addr\_ton: The Type of Number of the recipient’s address.
    - dest\_addr\_npi: The Numbering Plan Indicator of the recipient’s address.
    - destination\_addr: The recipient’s address.
    - esm\_class: Indicates the message mode and type.
    - protocol\_id: Protocol identifier.
    - priority\_flag: Sets the priority of the message.
    - schedule\_delivery\_time: Scheduled time for message delivery.
    - validity\_period: Validity period of the message.
    - registered\_delivery: Indicates if a delivery receipt is required.
    - replace\_if\_present\_flag: Replace an existing message with the same ID.
    - data\_coding: Defines the encoding scheme of the message.
    - sm\_default\_msg\_id: Indicates a pre-defined message.
    - sm\_length: The length of the short message.
    - short\_message: The short message text.
6. deliver\_sm: 
    - (Same parameters as submit\_sm, except for replace\_if\_present\_flag and sm\_default\_msg\_id)
7. data\_sm: 
    - (Same parameters as submit\_sm, except for protocol\_id, priority\_flag, schedule\_delivery\_time, validity\_period, and sm\_default\_msg\_id)
8. query\_sm: 
    - message\_id: The message identifier assigned by the SMSC.
    - source\_addr\_ton: The Type of Number of the sender’s address.
    - source\_addr\_npi: The Numbering Plan Indicator of the sender’s address.
    - source\_addr: The sender’s address.
9. cancel\_sm: 
    - service\_type: Indicates the SMS service type.
    - message\_id: The message identifier assigned by the SMSC.
    - source\_addr\_ton: The Type of Number of the sender’s address.
    - source\_addr\_npi: The Numbering Plan Indicator of the sender’s address.
    - source\_addr: The sender’s address.
    - dest\_addr\_ton: The Type of Number of the recipient’s address.
    - dest\_addr\_npi: The Numbering Plan Indicator of the recipient’s address.
    - destination\_addr: The recipient’s address.
10. replace\_sm: 
    - message\_id: The message identifier assigned by the SMSC.
    - source\_addr\_ton: The Type of Number of the sender’s address.
    - source\_addr\_npi: The Numbering Plan Indicator of the sender’s address.
    - source\_addr: The sender’s address.
    - schedule\_delivery\_time: Scheduled time for message delivery.
    - validity\_period: Validity period of the message.
    - registered\_delivery: Indicates if a delivery receipt is required.
    - sm\_default\_msg\_id: Indicates a pre-defined message.
    - sm\_length: The length of the short message.
    - short\_message: The short message text.

11. enquire\_link:

- No additional parameters required.

12. alert\_notification:

- source\_addr\_ton: The Type of Number of the sender’s address.
- source\_addr\_npi: The Numbering Plan Indicator of the sender’s address.
- source\_addr: The sender’s address.
- esme\_addr\_ton: The Type of Number of the ESME’s address.
- esme\_addr\_npi: The Numbering Plan Indicator of the ESME’s address.
- esme\_addr: The ESME’s address.

Please note that for each command, there is a corresponding response PDU. The response PDUs typically contain a command\_status field indicating the result of the original command (0 for success, or an error code for failure), and in some cases, additional information related to the request.

For example, bind\_transmitter\_resp, bind\_receiver\_resp, and bind\_transceiver\_resp PDUs include an additional system\_id parameter, which is a copy of the system\_id value provided in the original bind command.

The submit\_sm\_resp and data\_sm\_resp PDUs include a message\_id parameter, which is the message identifier assigned by the SMSC for the submitted short message.

Other response PDUs, like deliver\_sm\_resp, query\_sm\_resp, cancel\_sm\_resp, and replace\_sm\_resp, do not require additional parameters beyond the command\_status field.