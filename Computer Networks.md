# Computer Networks

---

## 📌 Index

- [What is a Computer Network?](#what-is-a-computer-network)
- [Types of Computer Networks](#types-of-computer-networks)
- [Network Topologies](#network-topologies)
- [Network Protocols](#network-protocols)
- [OSI Model](#osi-model)
  - [Data Flows in the OSI Model](#data-flows-in-the-osi-model)
- [TCP/IP Model](#tcpip-model)
  - [Layers of TCP/IP Model](#layers-of-tcpip-model)
  - [Working of TCP/IP Model](#working-of-tcpip-model)
- [IP Address](#ip-address)
  - [Types of IP Addresses](#types-of-ip-addresses)
  - [Public vs Private IP Addresses](#public-vs-private-ip-addresses)
  - [Special IP Addresses](#special-ip-addresses)
- [IP Addressing](#ip-addressing)
  - [IPv4 Address Structure](#ipv4-address-structure)
  - [Classful IP Addressing](#classful-ip-addressing)
  - [Subnet Mask](#subnet-mask)
  - [Subnetting](#subnetting)
  - [Static vs Dynamic IP Addressing](#static-vs-dynamic-ip-addressing)
  - [DHCP (Dynamic Host Configuration Protocol)](#dhcp-dynamic-host-configuration-protocol)
- [Network Devices](#network-devices)
  - [Hubs](#hubs)
  - [Switches](#switches)
  - [Routers](#routers)
- [DNS (Domain Name System)](#dns-domain-name-system)
- [TCP and UDP](#tcp-and-udp)
- [Routing](#routing)
- [Switching](#switching)
- [Network Address Translation (NAT)](#network-address-translation-nat)
- [Firewall](#firewall)

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

The OSI(Open Systems Interconnection) Model is a conceptual framework created by the International Organization for Standardization (ISO) to describe how data is transmitted across a network using a structured seven-layer architecture.

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
The **Application Layer** sits at the top of the OSI stack and serves as the direct interface between the software user and the network. It produces the data that will be sent and displays the information received from other layers.

- **User Interface:** Acts as a "window" for network-based applications (like web browsers or email clients) to access network services.
- **Core Protocols:** Utilizes high-level protocols such as **HTTP/S** (Web), **SMTP** (Email), **FTP** (File Transfer), and **DNS** (Domain Name Resolution).
- **Network Virtual Terminal (NVT):** Enables users to log into and interact with remote hosts as if they were physically present at the terminal.
- **File Transfer, Access, and Management (FTAM):** Provides the framework for users to retrieve, manage, and manipulate files stored on remote computers.
- **Directory Services:** Offers distributed database access to manage global information regarding various network objects and services.

### Layer 6: The Presentation Layer
Often called the **Translation Layer**, the Presentation Layer ensures that data is formatted, secured, and compressed so that the receiving application can correctly interpret it.

- **Translation:** It extracts data from the Application Layer and converts it into a standardized format for network transmission, bridging differences in data representation between different systems.
- **Standards & Formats:** Handles the encoding of media using standards such as JPEG, MPEG, and GIF.
- **Encryption/Decryption:** Provides security by converting "plain text" into "ciphertext" (encryption) and back again (decryption) using key values. This process is typically handled by protocols like **TLS/SSL**.
- **Compression:** Reduces the total number of bits required for transmission, which increases network efficiency and speed.

### Layer 5: The Session Layer
The **Session Layer** acts as the "dialogue manager," governing the opening, closing, and security of communication channels between two devices.

- **Session Lifecycle:** Manages the establishment, maintenance, and termination of connections between applications.
- **Authentication & Security:** Ensures that the communicating parties are verified and the connection is secure.
- **Synchronization:** Inserts checkpoints into the data stream. This allows a transfer to resume from the last saved point if a failure occurs, rather than restarting from the beginning.
- **Dialog Control:** Directs whether communication is half-duplex (alternating) or full-duplex (simultaneous).
- **Practical Example:** In a web-based messenger, the Session Layer maintains the active link between your browser and the server, ensuring your specific chat remains open and synchronized while handling background encryption and data conversion.

### Layer 4: The Transport Layer
The Transport Layer ensures the end-to-end delivery of entire messages. It acts as a liaison, providing services to the Application layer while utilizing the infrastructure of the Network layer to ensure data reaches the correct application on the destination host.

- **Data Unit:** Data is broken down into Segments.
- **Service Point Addressing:** Uses Port Numbers (e.g., Port 80 for web traffic) to ensure data is delivered to the specific process or application intended, not just the device.
- **Segmentation & Reassembly:** Splits large messages into smaller segments for transmission and reassembles them in the correct order at the destination.
- **Protocols:** Common protocols include **TCP** (reliable), **UDP** (fast).
- **Connection-Oriented (TCP):** Requires a "handshake" to establish a connection; ensures reliability via error checking and acknowledgements.
- **Connectionless (UDP):** Sends data immediately without a formal connection; faster but offers no guarantee of delivery.

### Layer 3: The Network Layer
The **Network Layer** manages data transmission between hosts across different networks by handling logical addressing and path finding.

- **Data Unit:** Data segments are encapsulated into Packets.
- **Logical Addressing:** Assigns unique **IP addresses** (sender and receiver) to the packet header to identify devices globally.
- **Routing:** Determines the most efficient physical path from the source to the destination across interconnected networks.
- **Hardware:** Primarily implemented via **Routers and Switches**.
- **Inter-networking:** Facilitates communication between disparate networks by directing traffic to the correct destination.

### Layer 2: The Data Link Layer (DLL)
The **Data Link Layer** serves as the bridge between the physical hardware and the logical network, ensuring reliable node-to-node delivery of data. Its primary goal is to ensure that data transfer is error-free across the physical medium.

**1. Data Packaging (Framing):** At this layer, data packets received from the Network layer are divided into manageable units called Frames. This is done by adding specific "start" and "stop" bits so the receiver can recognize where one unit of data ends and the next begins.

**2. Addressing and Hardware:** The DLL uses **MAC addresses** (Physical Addressing) to identify hosts. It encapsulates the sender's and receiver's MAC addresses into the frame header. Common devices operating here are **Switches and Bridges**.

**3. Sublayers:**

- **Logical Link Control (LLC):** Manages flow and error control while acting as an interface for upper-layer protocols.
- **Media Access Control (MAC):** Determines how devices physically access the transmission medium and handles hardware addressing.

**4. Error Control:** It detects and retransmits damaged or lost frames to maintain data integrity.

**5. Flow Control:** It synchronizes the data rate between a fast sender and a slower receiver to prevent data "bottlenecks" or loss.

**6. Access Control:** When multiple devices share the same communication channel, the MAC sublayer dictates which device has the right to transmit at any given time to avoid collisions.

### Layer 1: The Physical Layer
The **Physical Layer** is the foundation of the OSI model, acting as the bridge for actual physical connections between devices. Its primary mission is the transmission of raw, unstructured bitstreams over a physical medium from one node to the next.

- **Core Responsibility:** It manages the hardware-level transmission of individual bits. When receiving data, it translates incoming physical signals back into digital 0s and 1s to be processed by the Data Link layer.
- **Essential Hardware:** Common devices operating at this level include Hubs, Repeaters, Modems, and Cables.
- **Bit Synchronization:** It ensures the sender and receiver are "in sync" by providing a clock signal that controls the timing of bit transmission.
- **Bit Rate Control:** It dictates the transmission speed, defined as the number of bits sent per second.
- **Physical Topologies:** It defines the structural layout of the network, such as Bus, Star, or Mesh configurations.
- **Transmission Mode:** It determines the direction of data flow, utilizing modes like Simplex (one-way), Half-Duplex (two-way, one at a time), or Full-Duplex (simultaneous two-way).

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

**TCP (Transmission Control Protocol):** TCP is used when reliability and accuracy are important. It ensures that data is delivered exactly as sent.

- TCP detects errors in the data using checksums to ensure integrity.
- If any data is lost or corrupted during transmission, TCP automatically resends it.
- Data is broken into packets, and TCP ensures these packets arrive in the correct sequence.
- TCP establishes a connection between sender and receiver before sending data, maintaining a stable session throughout the communication.
- Used for loading web pages, downloading files, sending emails, or any application where data must be complete and accurate.

**UDP (User Datagram Protocol):** UDP is used when speed is more important than perfect accuracy. It is faster but does not guarantee reliable delivery.

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
- **Application Layer:** The user's software (like a web browser or email client) creates the data and passes it to the next layer.
- **Transport Layer:** The data is broken into segments, and TCP or UDP adds control information to ensure reliable delivery or fast transmission.
- **Internet Layer:** Each segment is encapsulated into packets with IP addresses so it can be routed across networks to the destination device.
- **Network Access (Link) Layer:** The packets are converted into frames suitable for the physical network (Ethernet, Wi-Fi) and transmitted over cables or wireless signals.

#### When Receiving Data (At the Destination)
- **Network Access Layer:** The frames are received from the physical medium and checked for errors.
- **Internet Layer:** Frames are unpacked to extract packets and use the IP address to ensure it reaches the correct device.
- **Transport Layer:** Segments are reassembled into the original message, and any missing or corrupted data is corrected (if TCP is used).
- **Application Layer:** The complete data is delivered to the user application (like the browser displaying a webpage or the email client showing a message).

> **🎯 Interview Tip:** "The TCP/IP model is a 4-layer practical networking framework standardized by RFC 1122. It consists of Application (handles user-facing protocols like HTTP, DNS), Transport (provides reliable delivery via TCP or fast delivery via UDP using port numbers), Internet (handles logical addressing and routing using IP), and Network Access (manages physical transmission, framing, and MAC addressing). It is simpler than the OSI model and is the actual protocol suite used on the internet."

## IP Address

An IP (Internet Protocol) address is a unique numerical label assigned to every device connected to a network. It serves two main purposes: **identifying the host/device** and **providing the location** of the device in the network so data can be routed to it.

- Every device on the internet or a local network has an IP address.
- It works like a postal address — it tells the network where to deliver data.
- IP addresses are assigned by the ISP (Internet Service Provider) or the local network's DHCP server.

### Types of IP Addresses

**1. IPv4 (Internet Protocol Version 4)**

- Uses a **32-bit** address format, written as four decimal numbers separated by dots (dotted-decimal notation).
- Each number (octet) ranges from **0 to 255**.
- Supports approximately **4.3 billion** unique addresses.

**Examples:**
| IP Address | Description |
|---|---|
| `192.168.1.1` | Common home router default gateway |
| `192.168.0.105` | A device on a home/office LAN |
| `10.0.0.1` | Private network gateway |
| `172.16.0.10` | Private network device |
| `8.8.8.8` | Google's public DNS server |
| `142.250.190.46` | A public IP (e.g., google.com) |

**2. IPv6 (Internet Protocol Version 6)**

- Uses a **128-bit** address format, written as eight groups of four hexadecimal digits separated by colons.
- Created to solve the IPv4 address exhaustion problem.
- Supports approximately **340 undecillion** (3.4 × 10³⁸) unique addresses.

**Examples:**
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

**Private IP Address Ranges (IPv4):**
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

> **🎯 Interview Tip:** "An IP address is a unique numerical identifier assigned to each device on a network for identification and location addressing. IPv4 uses 32-bit addresses with ~4.3 billion combinations, while IPv6 uses 128-bit addresses to solve exhaustion. IPs are classified as public (internet-routable, assigned by ISP) or private (local network only, assigned by DHCP). Special addresses include 127.0.0.1 for loopback and 255.255.255.255 for broadcast."

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
- **Network Part:** Identifies which network the device belongs to.
- **Host Part:** Identifies the specific device within that network.

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

**CIDR Notation:** A shorthand way to write the subnet mask by appending `/n` where `n` is the number of network bits.

| Subnet Mask | CIDR | Usable Hosts |
|---|---|---|
| `255.0.0.0` | `/8` | 16,777,214 |
| `255.255.0.0` | `/16` | 65,534 |
| `255.255.255.0` | `/24` | 254 |
| `255.255.255.128` | `/25` | 126 |
| `255.255.255.192` | `/26` | 62 |

### Subnetting

Dividing the network `192.168.1.0/24` into **4 subnets**:

| Subnet | Network Address | Usable Range | Broadcast | Mask |
|---|---|---|---|---|
| Subnet 1 | `192.168.1.0` | `192.168.1.1` – `192.168.1.62` | `192.168.1.63` | `/26` |
| Subnet 2 | `192.168.1.64` | `192.168.1.65` – `192.168.1.126` | `192.168.1.127` | `/26` |
| Subnet 3 | `192.168.1.128` | `192.168.1.129` – `192.168.1.190` | `192.168.1.191` | `/26` |
| Subnet 4 | `192.168.1.192` | `192.168.1.193` – `192.168.1.254` | `192.168.1.255` | `/26` |

> **🎯 Interview Tip:** "IP addressing is the system of structuring and organizing IP addresses. An IPv4 address has 32 bits split into 4 octets, with a network portion and a host portion determined by the subnet mask. Classful addressing divides IPs into Classes A–E based on the first octet range. Subnet masks separate network and host bits — CIDR notation represents this as a prefix length like /24. Subnetting divides a larger network into smaller subnetworks by borrowing host bits, improving address utilization and reducing broadcast domains."

### Static vs Dynamic IP Addressing

IP addresses can be assigned to devices in two ways:

**Static IP Addressing:** The IP address is manually configured on the device by an administrator. It never changes unless manually updated.
- Used for servers, printers, routers, and devices that need a fixed, predictable address.
- Requires manual management — does not scale well for large networks.

**Dynamic IP Addressing:** The IP address is automatically assigned by a DHCP server. It can change each time the device connects to the network.
- Used for regular devices like laptops, phones, and desktops.
- Scalable and requires no manual configuration per device.

| Feature | Static | Dynamic |
|---|---|---|
| **Assignment** | Manual | Automatic (DHCP) |
| **Changes** | Never (unless reconfigured) | Can change on renewal |
| **Best for** | Servers, network infrastructure | End-user devices |
| **Management** | High effort | Low effort |

### DHCP (Dynamic Host Configuration Protocol)

DHCP is a network management protocol that automatically assigns IP addresses and other network configuration parameters to devices on a network, enabling them to communicate without manual setup.

- Operates on **UDP ports 67 (server)** and **68 (client)**.
- Assigns IP addresses from a defined pool (scope) for a limited time period called a **lease**.
- Along with IP addresses, DHCP also provides: Subnet mask, Default gateway, DNS server addresses, and Lease duration.
- **DHCP Process (DORA):**
  1. **Discover:** The client broadcasts a DHCPDISCOVER message to find available DHCP servers.
  2. **Offer:** The server responds with a DHCPOFFER containing an available IP and configuration.
  3. **Request:** The client sends a DHCPREQUEST accepting the offered configuration.
  4. **Acknowledge:** The server confirms with a DHCPACK, assigning the IP for the lease duration.
- **Lease Renewal:** The client attempts renewal at 50% (T1) and 87.5% (T2) of the lease time.
- **DHCP Relay Agent:** Forwards DHCP messages across subnets when the server is not on the same network.

> **🎯 Interview Tip:** "DHCP automatically assigns IP addresses using the DORA process — Discover, Offer, Request, Acknowledge. It operates on UDP ports 67/68, assigns addresses from a pool with a time-limited lease, and also provides subnet mask, default gateway, and DNS server information. Lease renewal happens at 50% and 87.5% of the lease duration."

---

## Network Devices

Network devices are physical or virtual hardware that facilitate communication, data transfer, and connectivity between devices within a network or across multiple networks.

### Hubs

A Hub is a basic networking device that connects multiple devices in a network and broadcasts incoming data to all connected ports, regardless of the intended destination.

- Operates at **Layer 1 (Physical Layer)** of the OSI model.
- Receives data on one port and floods it to all other ports — every connected device receives the data.
- Does not filter or direct traffic — it has no intelligence to determine which device should receive the data.
- Creates a single collision domain, meaning only one device can transmit at a time; simultaneous transmissions cause collisions.
- **Types:**
  - **Passive Hub:** Simply connects devices and passes signals without amplification.
  - **Active Hub:** Amplifies and regenerates signals before forwarding them.
  - **Intelligent Hub:** Includes management features like monitoring and diagnostics.
- Largely replaced by switches in modern networks due to inefficiency and collision issues.

> **🎯 Interview Tip:** "A hub is a Layer 1 device that broadcasts incoming data to all connected ports without any filtering or intelligence. It creates a single collision domain, leading to network congestion. It has been largely replaced by switches which forward data only to the intended destination port."

### Switches

A Switch is a network device that connects multiple devices and intelligently forwards data only to the specific device it is intended for, based on MAC addresses.

- Operates at **Layer 2 (Data Link Layer)** of the OSI model. Layer 3 switches can also perform routing.
- Maintains a **MAC address table** that maps each connected device's MAC address to its corresponding port.
- When a frame arrives, the switch reads the destination MAC address and forwards it only to the correct port — not to all ports.
- Each port on a switch is its own collision domain, which eliminates collisions and improves performance.
- Supports **full-duplex** communication, allowing simultaneous sending and receiving of data.
- **Types:**
  - **Unmanaged Switch:** Plug-and-play with no configuration; suitable for small networks.
  - **Managed Switch:** Offers configuration options like VLANs, QoS, port mirroring, and SNMP monitoring.
  - **Layer 3 Switch:** Combines switching and routing capabilities, can forward packets based on IP addresses.

> **🎯 Interview Tip:** "A switch is a Layer 2 device that uses a MAC address table to forward frames only to the intended destination port, unlike a hub which broadcasts to all ports. Each port is a separate collision domain, eliminating collisions. Managed switches support VLANs and QoS, while Layer 3 switches add routing capabilities."

### Routers

A Router is a network device that forwards data packets between different networks by determining the best path to the destination using routing tables and protocols.

- Operates at **Layer 3 (Network Layer)** of the OSI model.
- Connects multiple networks (e.g., a home LAN to the internet) and routes traffic between them.
- Uses **IP addresses** to determine the destination and selects the optimal path using routing tables.
- Each interface on a router creates a separate **broadcast domain**, isolating broadcast traffic between networks.
- Supports **NAT (Network Address Translation)**, allowing multiple devices on a private network to share a single public IP.
- **Routing Methods:**
  - **Static Routing:** Routes are manually configured by the administrator; suitable for small, stable networks.
  - **Dynamic Routing:** Routes are automatically learned and updated using protocols like RIP, OSPF, and BGP.
- Provides basic firewall and security features by filtering traffic between networks.

> **🎯 Interview Tip:** "A router is a Layer 3 device that forwards packets between different networks using IP addresses and routing tables. It creates separate broadcast domains per interface, supports NAT for IP translation, and uses static or dynamic routing protocols (RIP, OSPF, BGP) to determine the best path for data delivery."

---

## DNS (Domain Name System)

DNS is a hierarchical, distributed naming system that translates human-readable domain names into IP addresses that computers use to identify each other on the network.

- Acts as the "phonebook of the internet" — converts domain names (e.g., google.com) to IP addresses (e.g., 142.250.190.46).
- Without DNS, users would need to memorize numerical IP addresses to visit websites.
- Uses a **hierarchical structure** with multiple levels:
  - **Root DNS Servers:** The top of the hierarchy; directs queries to the appropriate TLD server.
  - **TLD (Top-Level Domain) Servers:** Manages domains under a specific extension (.com, .org, .net, .in).
  - **Authoritative DNS Servers:** Holds the actual DNS records for a specific domain and returns the final IP address.
  - **Recursive Resolver:** The intermediary that receives the user's query and fetches the answer by querying the hierarchy.
- **DNS Record Types:**
  - **A Record:** Maps a domain to an IPv4 address.
  - **AAAA Record:** Maps a domain to an IPv6 address.
  - **CNAME Record:** Maps a domain to another domain name (alias).
  - **MX Record:** Specifies the mail server for a domain.
  - **NS Record:** Specifies the authoritative name servers for a domain.
- **DNS Resolution Process:**
  1. User types a domain name in the browser.
  2. The browser checks its local cache → OS cache → router cache.
  3. If not found, the query goes to the Recursive Resolver (usually provided by ISP).
  4. The resolver queries Root Server → TLD Server → Authoritative Server.
  5. The authoritative server returns the IP address.
  6. The resolver caches the result and sends the IP back to the browser.
  7. The browser connects to the server using the resolved IP address.
- Uses primarily **UDP port 53** for queries (TCP port 53 for zone transfers and large responses).

> **🎯 Interview Tip:** "DNS is a hierarchical distributed system that resolves domain names to IP addresses. The resolution process flows from the recursive resolver through Root, TLD, and Authoritative servers. Common record types include A (IPv4), AAAA (IPv6), CNAME (alias), and MX (mail). DNS primarily uses UDP port 53 for fast query resolution and caches results at multiple levels to reduce lookup time."

---

## TCP and UDP

TCP and UDP are the two core transport layer protocols that govern how data is sent between devices over a network.

### TCP (Transmission Control Protocol)

TCP is a **connection-oriented** protocol that ensures reliable, ordered, and error-checked delivery of data.

<table align="center" style="border-collapse: collapse; text-align: center;">
  <tr><th colspan="3">TCP 3-Way Handshake</th></tr>
  <tr><td><b>Client</b></td><td></td><td><b>Server</b></td></tr>
  <tr><td>SYN ──────────►</td><td></td><td>Receives SYN</td></tr>
  <tr><td>Receives SYN-ACK</td><td></td><td>◄────────── SYN-ACK</td></tr>
  <tr><td>ACK ──────────►</td><td></td><td>Receives ACK</td></tr>
  <tr><td colspan="3">✅ Connection Established</td></tr>
  <tr><td>DATA ⇄ DATA</td><td></td><td>DATA ⇄ DATA</td></tr>
  <tr><td colspan="3"><b>4-Way Termination</b></td></tr>
  <tr><td>FIN ──────────►</td><td></td><td>Receives FIN</td></tr>
  <tr><td>Receives ACK</td><td></td><td>◄────────── ACK</td></tr>
  <tr><td>Receives FIN</td><td></td><td>◄────────── FIN</td></tr>
  <tr><td>ACK ──────────►</td><td></td><td>Receives ACK</td></tr>
  <tr><td colspan="3">🔴 Connection Closed</td></tr>
</table>

- Establishes a connection before data transfer using a **3-way handshake:**
  1. **SYN:** Client sends a synchronization request to the server.
  2. **SYN-ACK:** Server acknowledges and sends back its own synchronization.
  3. **ACK:** Client confirms, and the connection is established.
- Guarantees data arrives **in order** and **without loss** — retransmits any missing or corrupted segments.
- Uses **sequence numbers** to track and reorder segments at the destination.
- Implements **flow control** (sliding window) to prevent overwhelming the receiver.
- Implements **congestion control** to adapt transmission rate based on network conditions.
- Connection is terminated using a **4-way handshake** (FIN → ACK → FIN → ACK).
- **Port examples:** HTTP (80), HTTPS (443), FTP (21), SMTP (25), SSH (22).
- **Use cases:** Web browsing, email, file transfer, remote access — any application where data must be complete and accurate.

### UDP (User Datagram Protocol)

UDP is a **connectionless** protocol that sends data without establishing a connection, prioritizing speed over reliability.

<table align="center" style="border-collapse: collapse; text-align: center;">
  <tr><th colspan="3">UDP Communication</th></tr>
  <tr><td><b>Sender</b></td><td></td><td><b>Receiver</b></td></tr>
  <tr><td colspan="3">❌ No Handshake</td></tr>
  <tr><td>Data 1 ──────────►</td><td></td><td>✅ Received</td></tr>
  <tr><td>Data 2 ──────────►</td><td></td><td>❌ Lost</td></tr>
  <tr><td>Data 3 ──────────►</td><td></td><td>✅ Received</td></tr>
  <tr><td>Data 4 ──────────►</td><td></td><td>✅ Received (out of order)</td></tr>
  <tr><td colspan="3">❌ No Retransmission · No Ordering · No ACK</td></tr>
</table>

- No handshake — data is sent immediately without waiting for a connection to be established.
- No guarantee of delivery, ordering, or duplicate protection.
- No retransmission of lost packets.
- Minimal overhead — only an 8-byte header (vs. 20-byte TCP header), making it faster and lighter.
- **Port examples:** DNS (53), DHCP (67/68), TFTP (69), SNMP (161), RTP (for media streaming).
- **Use cases:** Live video/audio streaming, online gaming, VoIP, DNS queries — any application where speed matters more than perfect delivery.

### TCP vs UDP

| Feature | TCP | UDP |
|---|---|---|
| **Connection** | Connection-oriented (3-way handshake) | Connectionless |
| **Reliability** | Guaranteed delivery with retransmission | No guarantee |
| **Ordering** | Maintains sequence order | No ordering |
| **Speed** | Slower (overhead from checks) | Faster (minimal overhead) |
| **Header size** | 20 bytes | 8 bytes |
| **Flow control** | Yes (sliding window) | No |
| **Error checking** | Checksum + retransmission | Checksum only (no retransmission) |
| **Use cases** | Web, email, file transfer | Streaming, gaming, VoIP, DNS |

> **🎯 Interview Tip:** "TCP is connection-oriented, uses a 3-way handshake (SYN, SYN-ACK, ACK) to establish a connection, and guarantees reliable, ordered delivery with retransmission and flow control. UDP is connectionless, sends data immediately without a handshake, and provides no delivery guarantee — making it faster with less overhead. TCP is used for web, email, and file transfers where accuracy matters. UDP is used for streaming, gaming, and DNS where speed is prioritized over reliability."

---

## Routing

Routing is the process of selecting the best path for data packets to travel from a source to a destination across one or more interconnected networks.

- Performed by **routers** operating at Layer 3 (Network Layer) of the OSI model.
- Routers use **routing tables** to store information about network destinations and the best paths to reach them.
- Each entry in the routing table contains the destination network, subnet mask, next hop, and the outgoing interface.
- **Types of Routing:**
  - **Static Routing:** Routes are manually configured by the network administrator. Suitable for small, predictable networks. Does not adapt to topology changes automatically.
  - **Dynamic Routing:** Routes are automatically learned and updated using routing protocols. Adapts to network changes in real time.
  - **Default Routing:** A single default route is configured to forward all packets to a specific next hop when no other route matches. Commonly used in stub networks with only one exit point.
- **Dynamic Routing Protocols:**
  - **RIP (Routing Information Protocol):** Uses hop count as the metric (max 15 hops). Simple but limited to small networks.
  - **OSPF (Open Shortest Path First):** Uses link-state algorithm and cost as the metric. Scalable and widely used in enterprise networks.
  - **BGP (Border Gateway Protocol):** The protocol that routes data between autonomous systems on the internet. Uses path attributes for decision-making.
  - **EIGRP (Enhanced Interior Gateway Routing Protocol):** Cisco proprietary; uses composite metrics (bandwidth, delay, load, reliability).
- **Routing Metrics:** Factors used to determine the best path — hop count, bandwidth, delay, cost, and reliability.

> **🎯 Interview Tip:** "Routing is the Layer 3 process of selecting the optimal path for packets across networks using routing tables. Static routing is manually configured, while dynamic routing uses protocols like RIP (hop count), OSPF (link-state, cost-based), and BGP (inter-AS routing on the internet) to automatically discover and update routes. Routing decisions are based on metrics such as hop count, bandwidth, and delay."

---

## Switching

Switching is the process of forwarding data frames within a local network (LAN) from one device to another based on MAC addresses, operating at Layer 2 of the OSI model.

- Performed by **switches** that maintain a MAC address table to map device MAC addresses to specific ports.
- When a frame arrives, the switch reads the destination MAC address and forwards it to the correct port.
- **MAC Address Learning:** When a frame arrives on a port, the switch records the source MAC address and the port it came from in its MAC address table.
- **Types of Switching:**
  - **Store-and-Forward:** The switch receives the entire frame, checks for errors (CRC), and then forwards it. Most reliable but adds latency.
  - **Cut-Through:** The switch reads only the destination MAC address and begins forwarding immediately without error checking. Fastest but may forward corrupt frames.
  - **Fragment-Free:** A compromise — reads the first 64 bytes (minimum frame size) to check for collision fragments before forwarding.
- **VLANs (Virtual LANs):** Switches can logically segment a network into separate broadcast domains using VLANs, improving security and reducing unnecessary broadcast traffic.
- **Spanning Tree Protocol (STP):** Prevents switching loops in networks with redundant paths by logically blocking redundant links and keeping only one active path.
- **Difference from Routing:** Switching operates at Layer 2 using MAC addresses within a single network, while routing operates at Layer 3 using IP addresses across different networks.

> **🎯 Interview Tip:** "Switching is a Layer 2 process that forwards frames within a LAN based on MAC addresses using a MAC address table. Switches learn MAC addresses dynamically and support three forwarding methods — Store-and-Forward (error-checked, reliable), Cut-Through (fast, no error check), and Fragment-Free (checks first 64 bytes). VLANs segment broadcast domains logically, and STP prevents switching loops in redundant topologies."

---

## Network Address Translation (NAT)

NAT is a technique used by routers to translate private (internal) IP addresses to a public (external) IP address and vice versa, allowing multiple devices on a local network to access the internet using a single public IP.

- Operates at **Layer 3 (Network Layer)** and is typically implemented on routers or firewalls.
- Solves the IPv4 address exhaustion problem by allowing many devices to share one public IP.
- Provides a layer of security by hiding internal network structure and private IP addresses from the external network.
- **Types of NAT:**
  - **Static NAT:** Maps one private IP to one public IP permanently. Used for servers that need to be accessible from the internet.
  - **Dynamic NAT:** Maps a private IP to a public IP from a pool of available addresses. The mapping is temporary and assigned on a first-come, first-served basis.
  - **PAT (Port Address Translation) / NAT Overload:** Maps multiple private IPs to a single public IP by differentiating connections using unique port numbers. This is the most common form used in home and office networks.
- **How NAT Works:**
  1. A device on the private network sends a packet to an external destination.
  2. The router replaces the source private IP with its public IP (and assigns a unique port number in PAT).
  3. The packet travels to the destination using the public IP.
  4. The response comes back to the router's public IP.
  5. The router uses its NAT translation table to map the response back to the correct private IP and forwards it to the original device.
- **NAT Table:** Maintains a mapping between internal (private IP + port) and external (public IP + port) addresses for active connections.
- **Limitations:**
  - Can break end-to-end connectivity required by some protocols and applications.
  - Adds processing overhead on the router.
  - Complicates peer-to-peer connections and certain VPN configurations.

> **🎯 Interview Tip:** "NAT translates private IP addresses to public IPs at the router, allowing multiple devices to share a single public IP for internet access. Static NAT provides one-to-one permanent mapping, Dynamic NAT uses a pool of public IPs, and PAT (the most common type) maps multiple private IPs to one public IP using unique port numbers. NAT conserves IPv4 addresses and adds security by hiding internal network structure, but can introduce overhead and break end-to-end connectivity."

---

## Firewall

A Firewall is a network security device or software that monitors and controls incoming and outgoing network traffic based on predefined security rules, acting as a barrier between a trusted internal network and untrusted external networks.

- Operates at multiple OSI layers depending on the type — from **Layer 3 (Network)** to **Layer 7 (Application)**.
- Examines each packet of data and decides whether to allow or block it based on a set of security rules (access control lists).
- Acts as the first line of defense against unauthorized access, cyberattacks, and malicious traffic.
- Can be implemented as **hardware** (dedicated appliance), **software** (installed on a device), or **cloud-based** (firewall-as-a-service).
- **Types of Firewalls:**
  - **Packet-Filtering Firewall:** Operates at Layer 3/4. Inspects individual packets based on source/destination IP, port number, and protocol. Simple and fast but does not examine packet contents or track connection state.
  - **Stateful Inspection Firewall:** Tracks the state of active connections and makes decisions based on the context of the traffic (not just individual packets). More secure than packet-filtering.
  - **Proxy Firewall (Application-Level Gateway):** Operates at Layer 7. Acts as an intermediary between the client and server, inspecting the full content of the traffic. Provides deep inspection but adds latency.
  - **Next-Generation Firewall (NGFW):** Combines traditional firewall features with advanced capabilities like deep packet inspection (DPI), intrusion prevention system (IPS), application awareness, and threat intelligence.
  - **Network Address Translation (NAT) Firewall:** Hides internal IP addresses by translating them to a single public IP, preventing external devices from directly accessing internal hosts.
- **Firewall Rules:** Defined as ordered rules that specify:
  - **Action:** Allow or Deny
  - **Source:** IP address or network range
  - **Destination:** IP address or network range
  - **Port:** Specific port number or range
  - **Protocol:** TCP, UDP, ICMP, etc.
  - Rules are evaluated top-to-bottom; the first matching rule is applied.
- **Inbound vs Outbound Filtering:**
  - **Inbound:** Controls traffic entering the network from external sources.
  - **Outbound:** Controls traffic leaving the network to external destinations.
- **DMZ (Demilitarized Zone):** A separate network segment placed between the internal network and the internet, used to host public-facing services (web servers, email servers) while keeping the internal network protected.
- **Limitations:**
  - Cannot protect against threats that bypass the firewall (e.g., insider attacks, infected USB drives).
  - Encrypted traffic may not be inspectable without SSL/TLS decryption capabilities.
  - Misconfigured rules can create security gaps or block legitimate traffic.

> **🎯 Interview Tip:** "A firewall is a network security system that monitors and filters traffic based on predefined rules. Packet-filtering firewalls inspect headers at Layer 3/4, stateful firewalls track connection state for context-aware decisions, proxy firewalls operate at Layer 7 for deep content inspection, and NGFWs combine all of these with IPS and application awareness. Rules are evaluated top-to-bottom with allow/deny actions based on source, destination, port, and protocol. A DMZ is used to isolate public-facing services from the internal network."

