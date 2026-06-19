# Computer Networks

---

## 📌 Index

- [What is a Computer Network?](#what-is-a-computer-network)
- [Types of Computer Networks](#types-of-computer-networks)
- [Network Topologies](#network-topologies)
- [Network Protocols](#network-protocols)
- [OSI Model](#osi-model)
- [TCP/IP Model](#tcpip-model)
- [Network Devices](#network-devices)
- [Network Security](#network-security)
- [Common Network Issues](#common-network-issues)

## What is a Computer Network?
Computer network is a collection of interconnected devices that communicate with each other to exchange data and resources. It enables efficient communication and supports services like email, file sharing, and internet access.

> **🎯 Interview Tip:** "A computer network is a system of interconnected devices that communicate using defined protocols to share data and resources. It enables services like file sharing, email, and internet access by establishing connections through wired or wireless mediums."

## Types of Computer Networks
- **PAN (Personal Area Network)**: Connects devices within a small area (e.g., Bluetooth).
- **LAN (Local Area Network)**: Connects devices within a limited area using Ethernet (e.g., home, office).
- **WLAN (Wireless Local Area Network)**: A LAN that uses wireless communication (e.g., Wi-Fi).
- **CAN (Campus Area Network)**: Connects multiple LANs within a limited area (e.g., university).
- **MAN (Metropolitan Area Network)**: Connects LANs across a city or region.
- **WAN (Wide Area Network)**: Connects LANs across large geographical areas (e.g., the internet).
- **VPN (Virtual Private Network)**: Creates a secure connection over the internet to a private network.


> **🎯 Interview Tip:** "Computer networks are classified by their geographical scope — PAN for personal devices, LAN for local areas, MAN for cities, and WAN for large geographical regions. VPNs create secure tunnels over public networks, and WLANs extend LANs wirelessly."

## Network Topologies
- **Bus**: All devices share a single communication line.
- **Star**: All devices connect to a central hub.
- **Ring**: Each device connects to two others, forming a circle.
- **Mesh**: Every device connects to every other device.
- **Tree**: A hierarchical structure with a root and branches.

> **🎯 Interview Tip:** "Network topology defines the physical or logical arrangement of devices. Bus uses a single shared line, Star connects all nodes to a central hub, Ring forms a circular chain, Mesh provides full interconnection for redundancy, and Tree is a hierarchical combination of Star topologies."

## Network Protocols
- **HTTP/HTTPS**: For web communication.
- **FTP**: For file transfer.
- **SMTP**: For email transmission.
- **TCP/IP**: For reliable data transmission.
- **UDP**: For faster, connectionless communication.


> **🎯 Interview Tip:** "Network protocols are standardized rules that govern data communication. HTTP/HTTPS handles web traffic, FTP manages file transfers, SMTP is for email delivery, TCP ensures reliable ordered delivery with error correction, and UDP provides faster connectionless transmission without guaranteed delivery."

## OSI Model

The OSI Model is a conceptual framework created by the International Organization for Standardization (ISO) to describe how data is transmitted across a network using a structured seven-layer architecture.

<table align="center" style="border-collapse: collapse; text-align: center;">
  <tr>
    <th>Layer</th>
    <th>Name</th>
    <th>Function</th>
    <th>Protocols/Examples</th>
  </tr>
  <tr>
    <td>7</td>
    <td><b>Application</b></td>
    <td>User interface & network services</td>
    <td>HTTP, FTP, SMTP, DNS</td>
  </tr>
  <tr><td colspan="4">⬇️ ⬆️</td></tr>
  <tr>
    <td>6</td>
    <td><b>Presentation</b></td>
    <td>Data translation, encryption & compression</td>
    <td>SSL/TLS, JPEG, ASCII</td>
  </tr>
  <tr><td colspan="4">⬇️ ⬆️</td></tr>
  <tr>
    <td>5</td>
    <td><b>Session</b></td>
    <td>Establishes, manages & terminates sessions</td>
    <td>NetBIOS, RPC</td>
  </tr>
  <tr><td colspan="4">⬇️ ⬆️</td></tr>
  <tr>
    <td>4</td>
    <td><b>Transport</b></td>
    <td>Reliable data transfer & error recovery</td>
    <td>TCP, UDP</td>
  </tr>
  <tr><td colspan="4">⬇️ ⬆️</td></tr>
  <tr>
    <td>3</td>
    <td><b>Network</b></td>
    <td>Routing & logical addressing</td>
    <td>IP, ICMP, Routers</td>
  </tr>
  <tr><td colspan="4">⬇️ ⬆️</td></tr>
  <tr>
    <td>2</td>
    <td><b>Data Link</b></td>
    <td>Framing, MAC addressing & error detection</td>
    <td>Ethernet, Wi-Fi, Switches</td>
  </tr>
  <tr><td colspan="4">⬇️ ⬆️</td></tr>
  <tr>
    <td>1</td>
    <td><b>Physical</b></td>
    <td>Transmits raw bits over physical medium</td>
    <td>Cables, Hubs, Signals</td>
  </tr>
</table>

<p align="center"><i>Data flows ⬇️ down from Layer 7 → 1 (sender) and ⬆️ up from Layer 1 → 7 (receiver)</i></p>

## Data Flows in the OSI Model

When data is transferred from one device to another, it traverses all 7 layers of the OSI model. The data first travels **downward** through each layer on the sender's side (encapsulation), and then travels **upward** through each layer on the receiver's side (decapsulation).

![OSI Model Data Flow](assets/computer_networks/OSI-Model.gif)

### Layer 7: The Application Layer
The ****Application Layer**** sits at the top of the OSI stack and serves as the direct interface between the software user and the network. It produces the data that will be sent and displays the information received from other layers.

- ****User Interface:**** Acts as a "window" for network-based applications (like web browsers or email clients) to access network services.
- ****Core Protocols:**** Utilizes high-level protocols such as ****HTTP/S**** (Web), ****SMTP**** (Email), ****FTP**** (File Transfer), and ****DNS**** (Domain Name Resolution).
- ****Network Virtual Terminal (NVT):**** Enables users to log into and interact with remote hosts as if they were physically present at the terminal.
- ****File Transfer, Access, and Management (FTAM):**** Provides the framework for users to retrieve, manage, and manipulate files stored on remote computers.
- ****Directory Services:**** Offers distributed database access to manage global information regarding various network objects and services.

### Layer 6: The Presentation Layer
Often called the ****Translation Layer****, the Presentation Layer ensures that data is formatted, secured, and compressed so that the receiving application can correctly interpret it.

- ****Translation:**** It extracts data from the Application Layer and converts it into a standardized format for network transmission, bridging differences in data representation between different systems.
- ****Standards & Formats:**** Handles the encoding of media using standards such as JPEG, MPEG, and GIF.
- ****Encryption/Decryption:**** Provides security by converting "plain text" into "ciphertext" (encryption) and back again (decryption) using key values. This process is typically handled by protocols like ****TLS/SSL****.
- ****Compression:**** Reduces the total number of bits required for transmission, which increases network efficiency and speed.

### Layer 5: The Session Layer
The ****Session Layer**** acts as the "dialogue manager," governing the opening, closing, and security of communication channels between two devices.

- ****Session Lifecycle:**** Manages the establishment, maintenance, and termination of connections between applications.
- ****Authentication & Security:**** Ensures that the communicating parties are verified and the connection is secure.
- ****Synchronization:**** Inserts checkpoints into the data stream. This allows a transfer to resume from the last saved point if a failure occurs, rather than restarting from the beginning.
- ****Dialog Control:**** Directs whether communication is half-duplex (alternating) or full-duplex (simultaneous).
- ****Practical Example:**** In a web-based messenger, the Session Layer maintains the active link between your browser and the server, ensuring your specific chat remains open and synchronized while handling background encryption and data conversion.

### Layer 4: The Transport Layer
The Transport Layer ensures the end-to-end delivery of entire messages. It acts as a liaison, providing services to the Application layer while utilizing the infrastructure of the Network layer to ensure data reaches the correct application on the destination host.

- ****Data Unit:**** Data is broken down into Segments.
- ****Service Point Addressing:**** Uses Port Numbers (e.g., Port 80 for web traffic) to ensure data is delivered to the specific process or application intended, not just the device.
- ****Segmentation & Reassembly:**** Splits large messages into smaller segments for transmission and reassembles them in the correct order at the destination.
- ****Protocols:**** Common protocols include ****TCP**** (reliable), ****UDP**** (fast).
- ****Connection-Oriented (TCP):**** Requires a "handshake" to establish a connection; ensures reliability via error checking and acknowledgements.
- ****Connectionless (UDP):**** Sends data immediately without a formal connection; faster but offers no guarantee of delivery.

### Layer 3: The Network Layer
The ****Network Layer**** manages data transmission between hosts across different networks by handling logical addressing and path finding.

- ****Data Unit:**** Data segments are encapsulated into Packets.
- ****Logical Addressing:**** Assigns unique ****IP addresses**** (sender and receiver) to the packet header to identify devices globally.
- ****Routing:**** Determines the most efficient physical path from the source to the destination across interconnected networks.
- ****Hardware:**** Primarily implemented via ****Routers and Switches****.
- ****Inter-networking:**** Facilitates communication between disparate networks by directing traffic to the correct destination.

### Layer 2: The Data Link Layer (DLL)
The ****Data Link Layer**** serves as the bridge between the physical hardware and the logical network, ensuring reliable node-to-node delivery of data. Its primary goal is to ensure that data transfer is error-free across the physical medium.

****1. Data Packaging (Framing):**** At this layer, data packets received from the Network layer are divided into manageable units called Frames. This is done by adding specific "start" and "stop" bits so the receiver can recognize where one unit of data ends and the next begins.

****2. Addressing and Hardware:**** The DLL uses ****MAC addresses**** (Physical Addressing) to identify hosts. It encapsulates the sender's and receiver's MAC addresses into the frame header. Common devices operating here are ****Switches and Bridges****.

****3. Sublayers:****

- ****Logical Link Control (LLC):**** Manages flow and error control while acting as an interface for upper-layer protocols.
- ****Media Access Control (MAC):**** Determines how devices physically access the transmission medium and handles hardware addressing.

****4. Error Control:**** It detects and retransmits damaged or lost frames to maintain data integrity.

****5. Flow Control:**** It synchronizes the data rate between a fast sender and a slower receiver to prevent data "bottlenecks" or loss.

****6. Access Control:**** When multiple devices share the same communication channel, the MAC sublayer dictates which device has the right to transmit at any given time to avoid collisions.

### Layer 1: The Physical Layer
The ****Physical Layer**** is the foundation of the OSI model, acting as the bridge for actual physical connections between devices. Its primary mission is the transmission of raw, unstructured bitstreams over a physical medium from one node to the next.

- ****Core Responsibility:**** It manages the hardware-level transmission of individual bits. When receiving data, it translates incoming physical signals back into digital 0s and 1s to be processed by the Data Link layer.
- ****Essential Hardware:**** Common devices operating at this level include Hubs, Repeaters, Modems, and Cables.
- ****Bit Synchronization:**** It ensures the sender and receiver are "in sync" by providing a clock signal that controls the timing of bit transmission.
- ****Bit Rate Control:**** It dictates the transmission speed, defined as the number of bits sent per second.
- ****Physical Topologies:**** It defines the structural layout of the network, such as Bus, Star, or Mesh configurations.
- ****Transmission Mode:**** It determines the direction of data flow, utilizing modes like Simplex (one-way), Half-Duplex (two-way, one at a time), or Full-Duplex (simultaneous two-way).

> **🎯 Interview Tip:** "The OSI model is a 7-layer conceptual framework by ISO that standardizes network communication. Data flows down from Application to Physical layer on the sender side (encapsulation), adding headers at each layer, and flows up on the receiver side (decapsulation), stripping headers. The layers are — Application (user interface), Presentation (data formatting and encryption), Session (connection management), Transport (segmentation and reliable delivery via TCP/UDP), Network (logical addressing and routing via IP), Data Link (framing and MAC addressing), and Physical (raw bit transmission over the medium)."

## TCP/IP Model

The TCP/IP model is a layered networking framework that explains how data is communicated between devices over a network using standardized protocols to ensure reliable and efficient transmission.

- Defined as a four-layer architecture consisting of Application, Transport, Internet, and Network Access layers.
- Standardized by RFC 1122, which specifies its structure and behavior.
- Simpler and more practical than the seven-layer OSI model.
- Serves as the core framework of the modern Internet and networking systems.

<table align="center" style="border-collapse: collapse; text-align: center;">
  <tr>
    <th>Layer</th>
    <th>Name</th>
    <th>Function</th>
    <th>Protocols/Examples</th>
  </tr>
  <tr>
    <td>4</td>
    <td><b>Application</b></td>
    <td>User apps & data formatting</td>
    <td>HTTP, FTP, SMTP, DNS</td>
  </tr>
  <tr><td colspan="4">⬇️ ⬆️</td></tr>
  <tr>
    <td>3</td>
    <td><b>Transport</b></td>
    <td>Reliable/fast delivery & segmentation</td>
    <td>TCP, UDP</td>
  </tr>
  <tr><td colspan="4">⬇️ ⬆️</td></tr>
  <tr>
    <td>2</td>
    <td><b>Internet</b></td>
    <td>Addressing, routing & packet handling</td>
    <td>IP, ICMP, ARP</td>
  </tr>
  <tr><td colspan="4">⬇️ ⬆️</td></tr>
  <tr>
    <td>1</td>
    <td><b>Network Access</b></td>
    <td>Physical transmission & framing</td>
    <td>Ethernet, Wi-Fi, ARP</td>
  </tr>
</table>

<p align="center"><i>Data flows ⬇️ down from Layer 4 → 1 (sender) and ⬆️ up from Layer 1 → 4 (receiver)</i></p>

### Layers of TCP/IP Model

### 1. Application Layer
This is the top layer of the TCP/IP model, where applications like web browsers, email clients, and file-sharing tools interact with the network.

- Acts as a bridge between user applications and lower network layers.
- Supports protocols such as HTTP, FTP, SMTP, and DNS.
- Handles data formatting so information is correctly understood by both sender and receiver.
- Provides encryption for secure communication.
- Manages sessions to track ongoing connections.

### 2. Transport Layer
Ensures reliable and efficient delivery of data between devices, managing segmentation, ordering, and retransmission as needed.

- Breaks large messages into packets and reassembles them at the destination.
- TCP checks for errors, resends lost data, and ensures correct order.
- UDP provides low-latency, connectionless delivery without error checking.
- Prevents the receiver from being overwhelmed by regulating data flow.
- Uses port numbers to allow multiple applications to share the network simultaneously.

****TCP (Transmission Control Protocol):**** TCP is used when reliability and accuracy are important. It ensures that data is delivered exactly as sent.

- TCP detects errors in the data using checksums to ensure integrity.
- If any data is lost or corrupted during transmission, TCP automatically resends it.
- Data is broken into packets, and TCP ensures these packets arrive in the correct sequence.
- TCP establishes a connection between sender and receiver before sending data, maintaining a stable session throughout the communication.
- Used for loading web pages, downloading files, sending emails, or any application where data must be complete and accurate.

****UDP (User Datagram Protocol):**** UDP is used when speed is more important than perfect accuracy. It is faster but does not guarantee reliable delivery.

- UDP detects errors via checksums but does not verify or recover from them.
- Lost or damaged data is not resent.
- Packets may arrive out of order, and the protocol does not fix it.
- Because it avoids extra checks and connections, UDP is faster and uses fewer resources.
- Used for live video streaming, online gaming, VoIP calls, or real-time applications where speed matters more than reliability.

### 3. Internet Layer
Responsible for addressing, packaging, and routing data packets so they can travel across networks and reach the correct destination device. It ensures that data can move between different networks efficiently.

- Assigns IP addresses to identify source and destination devices.
- Determines the best path for data to travel across networks.
- Breaks large packets into smaller ones for transmission and reassembles them at the destination.
- Primarily uses IP (Internet Protocol), along with supporting protocols like ICMP for error reporting and ARP for address resolution.

### 4. Network Access (Link Layer)
Responsible for physically transmitting data over network hardware, including cables, switches, and wireless connections. It handles how data is formatted for the network medium and ensures it reaches the next device on the path.

- Sends and receives raw bits over physical media like Ethernet cables, fiber optics, or Wi-Fi.
- Organizes data into frames for proper transmission and recognition by devices.
- Detects transmission errors using checksums or CRC.
- Uses hardware addresses to identify devices within the same network segment.
- Determines how multiple devices share the same physical medium, avoiding collisions.

### Working of TCP/IP Model

#### When Sending Data (From Sender to Receiver)
- ****Application Layer:**** The user's software (like a web browser or email client) creates the data and passes it to the next layer.
- ****Transport Layer:**** The data is broken into segments, and TCP or UDP adds control information to ensure reliable delivery or fast transmission.
- ****Internet Layer:**** Each segment is encapsulated into packets with IP addresses so it can be routed across networks to the destination device.
- ****Network Access (Link) Layer:**** The packets are converted into frames suitable for the physical network (Ethernet, Wi-Fi) and transmitted over cables or wireless signals.

#### When Receiving Data (At the Destination)
- ****Network Access Layer:**** The frames are received from the physical medium and checked for errors.
- ****Internet Layer:**** Frames are unpacked to extract packets and use the IP address to ensure it reaches the correct device.
- ****Transport Layer:**** Segments are reassembled into the original message, and any missing or corrupted data is corrected (if TCP is used).
- ****Application Layer:**** The complete data is delivered to the user application (like the browser displaying a webpage or the email client showing a message).

> **🎯 Interview Tip:** "The TCP/IP model is a 4-layer practical networking framework standardized by RFC 1122. It consists of Application (handles user-facing protocols like HTTP, DNS), Transport (provides reliable delivery via TCP or fast delivery via UDP using port numbers), Internet (handles logical addressing and routing using IP), and Network Access (manages physical transmission, framing, and MAC addressing). It is simpler than the OSI model and is the actual protocol suite used on the internet."

## IP Address

An IP (Internet Protocol) address is a unique numerical label assigned to every device connected to a network. It serves two main purposes: **identifying the host/device** and **providing the location** of the device in the network so data can be routed to it.

- Every device on the internet or a local network has an IP address.
- It works like a postal address — it tells the network where to deliver data.
- IP addresses are assigned by the ISP (Internet Service Provider) or the local network's DHCP server.

### Types of IP Addresses

****1. IPv4 (Internet Protocol Version 4)****

- Uses a **32-bit** address format, written as four decimal numbers separated by dots (dotted-decimal notation).
- Each number (octet) ranges from **0 to 255**.
- Supports approximately **4.3 billion** unique addresses.

****Examples:****
| IP Address | Description |
|---|---|
| `192.168.1.1` | Common home router default gateway |
| `192.168.0.105` | A device on a home/office LAN |
| `10.0.0.1` | Private network gateway |
| `172.16.0.10` | Private network device |
| `8.8.8.8` | Google's public DNS server |
| `142.250.190.46` | A public IP (e.g., google.com) |

****2. IPv6 (Internet Protocol Version 6)****

- Uses a **128-bit** address format, written as eight groups of four hexadecimal digits separated by colons.
- Created to solve the IPv4 address exhaustion problem.
- Supports approximately **340 undecillion** (3.4 × 10³⁸) unique addresses.

****Examples:****
| IP Address | Description |
|---|---|
| `2001:0db8:85a3:0000:0000:8a2e:0370:7334` | Full IPv6 address |
| `2001:db8:85a3::8a2e:370:7334` | Shortened form (leading zeros & consecutive zero groups omitted) |
| `::1` | Loopback address (equivalent to `127.0.0.1` in IPv4) |
| `fe80::1` | Link-local address |
| `2404:6800:4009:826::200e` | A public IPv6 (e.g., google.com) |

### Public vs Private IP Addresses

| Feature | Public IP | Private IP |
|---|---|---|
| **Scope** | Globally unique, routable on the internet | Used within a local network only |
| **Assigned by** | ISP | Router / DHCP server |
| **Example** | `203.0.113.50` | `192.168.1.25` |
| **Visibility** | Visible to the entire internet | Hidden behind a router (NAT) |

****Private IP Address Ranges (IPv4):****
| Class | Range | Example |
|---|---|---|
| Class A | `10.0.0.0` – `10.255.255.255` | `10.0.0.5` |
| Class B | `172.16.0.0` – `172.31.255.255` | `172.20.5.100` |
| Class C | `192.168.0.0` – `192.168.255.255` | `192.168.1.50` |

### Special IP Addresses

| Address | Purpose |
|---|---|
| `127.0.0.1` | Loopback / localhost — refers to the device itself |
| `0.0.0.0` | Default route / unspecified address |
| `255.255.255.255` | Broadcast — sends data to all devices in the network |
| `169.254.x.x` | APIPA — auto-assigned when DHCP fails |

### Static vs Dynamic IP Addresses

| Feature | Static IP | Dynamic IP |
|---|---|---|
| **Assignment** | Manually configured, never changes | Automatically assigned by DHCP, can change |
| **Use case** | Servers, printers, network devices | Regular devices (phones, laptops) |
| **Example** | A web server always at `203.0.113.10` | Your laptop getting `192.168.1.42` today and `192.168.1.38` tomorrow |

> **🎯 Interview Tip:** "An IP address is a unique numerical identifier assigned to each device on a network for identification and location addressing. IPv4 uses 32-bit addresses with ~4.3 billion combinations, while IPv6 uses 128-bit addresses to solve exhaustion. IPs are classified as public (internet-routable, assigned by ISP) or private (local network only, assigned by DHCP). Static IPs are manually configured and permanent, while dynamic IPs are auto-assigned and can change. Special addresses include 127.0.0.1 for loopback and 255.255.255.255 for broadcast."

---

## IP Addressing

IP Addressing is the system of assigning and organizing IP addresses within a network. It defines how addresses are structured, classified, and divided into network and host portions.

### IPv4 Address Structure

An IPv4 address is made up of **32 bits**, divided into **4 octets** (8 bits each):

```
  Example: 192.168.1.10

  Decimal:    192    .   168    .    1     .    10
  Binary:  11000000 . 10101000 . 00000001 . 00001010
           |octet 1|  |octet 2|  |octet 3|  |octet 4|
```

Each IP address has two parts:
- ****Network Part:**** Identifies which network the device belongs to.
- ****Host Part:**** Identifies the specific device within that network.

### Classful IP Addressing

| Class | First Octet Range | Default Subnet Mask | Network.Host Format | Example | Usage |
|---|---|---|---|---|---|
| **A** | 1 – 126 | `255.0.0.0` | N.H.H.H | `10.0.0.1` | Large networks (16 million hosts) |
| **B** | 128 – 191 | `255.255.0.0` | N.N.H.H | `172.16.5.1` | Medium networks (65,000 hosts) |
| **C** | 192 – 223 | `255.255.255.0` | N.N.N.H | `192.168.1.1` | Small networks (254 hosts) |
| **D** | 224 – 239 | — | — | `224.0.0.1` | Multicasting |
| **E** | 240 – 255 | — | — | `240.0.0.1` | Reserved / Experimental |

> **Note:** `127.x.x.x` is reserved for loopback and is not included in any class.

### Subnet Mask

A subnet mask determines which portion of an IP address is the **network** part and which is the **host** part.

```
  IP Address:    192.168.1.10
  Subnet Mask:   255.255.255.0

  Network Part:  192.168.1.x     (where mask is 255)
  Host Part:     x.x.x.10        (where mask is 0)

  → This device is on network 192.168.1.0 and its host ID is 10.
```

****CIDR Notation:**** A shorthand way to write the subnet mask by appending `/n` where `n` is the number of network bits.

| Subnet Mask | CIDR | Usable Hosts |
|---|---|---|
| `255.0.0.0` | `/8` | 16,777,214 |
| `255.255.0.0` | `/16` | 65,534 |
| `255.255.255.0` | `/24` | 254 |
| `255.255.255.128` | `/25` | 126 |
| `255.255.255.192` | `/26` | 62 |

### Subnetting Example

Dividing the network `192.168.1.0/24` into **4 subnets**:

| Subnet | Network Address | Usable Range | Broadcast | Mask |
|---|---|---|---|---|
| Subnet 1 | `192.168.1.0` | `192.168.1.1` – `192.168.1.62` | `192.168.1.63` | `/26` |
| Subnet 2 | `192.168.1.64` | `192.168.1.65` – `192.168.1.126` | `192.168.1.127` | `/26` |
| Subnet 3 | `192.168.1.128` | `192.168.1.129` – `192.168.1.190` | `192.168.1.191` | `/26` |
| Subnet 4 | `192.168.1.192` | `192.168.1.193` – `192.168.1.254` | `192.168.1.255` | `/26` |

> **🎯 Interview Tip:** "IP addressing is the system of structuring and organizing IP addresses. An IPv4 address has 32 bits split into 4 octets, with a network portion and a host portion determined by the subnet mask. Classful addressing divides IPs into Classes A–E based on the first octet range. Subnet masks separate network and host bits — CIDR notation represents this as a prefix length like /24. Subnetting divides a larger network into smaller subnetworks by borrowing host bits for the network portion, improving address utilization and reducing broadcast domains."

