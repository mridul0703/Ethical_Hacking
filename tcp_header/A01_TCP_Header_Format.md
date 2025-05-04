# A01. TCP Header Format

The Transmission Control Protocol (TCP) is a connection-oriented protocol used for reliable data transmission in computer networks. It plays a crucial role in ensuring accurate data delivery and error-checking, making it foundational to Internet communication.

> 🔍 *Understanding the TCP header is key to analyzing network traffic and designing secure network protocols.*

---

## 📑 Structure of the TCP Header

The TCP header is **20 bytes** long by default and contains crucial information about data transmission. It is structured into fields that manage the flow of data between sender and receiver. Each field serves a specific purpose in the transmission and handling of data packets.

### 🏗️ TCP Header Fields:

| Field               | Size (Bytes) | Description                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------|
| **Source Port**      | 2            | The sending port number.                                                     |
| **Destination Port** | 2            | The receiving port number.                                                   |
| **Sequence Number**  | 4            | Identifies the order of bytes sent in the stream.                           |
| **Acknowledgment Number** | 4        | Indicates the next expected byte from the other side (only in ACK packets).  |
| **Data Offset**      | 1            | Indicates the size of the TCP header.                                        |
| **Reserved**         | 3            | Reserved for future use, typically set to zero.                             |
| **Flags**            | 1            | Control flags (SYN, ACK, FIN, etc.).                                         |
| **Window Size**      | 2            | Specifies the size of the sender’s receive window.                          |
| **Checksum**         | 2            | Used for error-checking the header and data.                                 |
| **Urgent Pointer**   | 2            | Indicates the urgent data byte position (only when URG flag is set).        |
| **Options**          | 0–40         | Optional fields for various functions like maximum segment size (MSS), timestamps, etc. |
| **Padding**          | Variable     | Adds padding for 32-bit alignment.                                           |

---

## 🔹 Source Port and Destination Port

### Source Port:
- **Size**: 16 bits
- This field represents the **sending port** number. The source port helps the receiver know where to send the response or acknowledgment.

### Destination Port:
- **Size**: 16 bits
- This field represents the **receiving port** number. The destination port helps identify the application or service to which the data belongs (e.g., HTTP on port 80, FTP on port 21).

---

## 🔢 Sequence Number and Acknowledgment Number

### Sequence Number:
- **Size**: 32 bits
- The **sequence number** is used to keep track of the number of bytes sent in a TCP session. It marks the first byte of the segment. This number helps ensure that data is received in the correct order and is a critical component of **flow control**.

### Acknowledgment Number:
- **Size**: 32 bits
- The **acknowledgment number** indicates the sequence number of the next byte the receiver expects to receive. It only appears in packets that acknowledge data (i.e., when the ACK flag is set).

> ⚠️ *For example, if the receiver expects byte number 5001, it will send back 5001 as the acknowledgment number.*

---

## ⚙️ Flags (SYN, ACK, FIN, etc.)

The **Flags field** is crucial for controlling the **state** of the connection. It is composed of 9 bits, but only a few of them are typically used in practice. These flags are used for **connection establishment**, **data transmission**, and **termination**.

### Flag Types:
- **URG (Urgent)**: This flag is set when the Urgent Pointer field is valid and there is urgent data to process.
- **ACK (Acknowledgment)**: This flag is set when the Acknowledgment Number field is valid. It acknowledges receipt of data.
- **PSH (Push)**: Indicates to the receiving system that the data should be forwarded to the application immediately.
- **RST (Reset)**: Resets the connection and aborts the session.
- **SYN (Synchronize)**: Initiates a TCP connection. The SYN flag is used during the **three-way handshake** to synchronize sequence numbers between the sender and receiver.
- **FIN (Finish)**: Indicates that the sender has finished sending data. The FIN flag is used during the **connection termination** process.
- **ECE (ECN Echo)**: Used for Explicit Congestion Notification (ECN) to signal congestion to the sender.
- **CWR (Congestion Window Reduced)**: Indicates that the congestion window has been reduced due to congestion notification.
- **NS (Nonce Sum)**: Used for security purposes to prevent certain types of attacks.

### Example of a SYN Packet:
- SYN Flag: 1
- ACK Flag: 0
- FIN Flag: 0

---

## 🖼️ Window Size, Checksum, Urgent Pointer

### Window Size:
- **Size**: 16 bits
- The **window size** represents the number of bytes that can be sent before receiving an acknowledgment. This is an essential part of **flow control** and helps prevent network congestion.

### Checksum:
- **Size**: 16 bits
- The **checksum** is used for **error checking**. It verifies the integrity of the header and the data to ensure that no errors occurred during transmission. If the checksum doesn’t match the calculated value, the data is considered corrupt.

### Urgent Pointer:
- **Size**: 16 bits
- The **urgent pointer** field points to the last byte of urgent data in the segment. This is used when the **URG flag** is set to indicate that certain data must be processed immediately. If the URG flag is not set, the urgent pointer is not used.

---

## 📊 Example TCP Header (in hexadecimal):
```
45 00 00 3c 1a 46 40 00 40 06 b1 e6 c0 a8 00 68
c0 a8 00 01 00 50 00 50 12 00 00 00 00 00 00 00
```

This represents a **TCP packet** from **192.168.0.104** (source IP) to **192.168.0.1** (destination IP) on ports **80** (HTTP) and **80** (HTTP), with other fields such as sequence number, acknowledgment number, flags, and checksum.

---

## 📘 Summary of TCP Header Fields

| Field                     | Size (Bytes) | Description                                             |
|---------------------------|--------------|---------------------------------------------------------|
| Source Port               | 2            | Port number of the sender                               |
| Destination Port          | 2            | Port number of the receiver                             |
| Sequence Number           | 4            | Sequence number for tracking data                       |
| Acknowledgment Number     | 4            | Number of the next expected byte                        |
| Data Offset               | 1            | Specifies the length of the TCP header                  |
| Reserved                  | 3            | Reserved bits for future use                            |
| Flags                     | 1            | Control flags (SYN, ACK, FIN, etc.)                     |
| Window Size               | 2            | Receiver's available window size                        |
| Checksum                  | 2            | Error-checking field                                    |
| Urgent Pointer            | 2            | Points to the urgent data (if the URG flag is set)      |
| Options and Padding       | 0-40         | Optional fields and padding for 32-bit alignment        |

---

> 📘 *The TCP header format is foundational for understanding how reliable communication is established and maintained in networking protocols.*


