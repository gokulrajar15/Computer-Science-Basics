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

## Types of Computer Networks
- **PAN (Personal Area Network)**: Connects devices within a small area (e.g., Bluetooth).
- **LAN (Local Area Network)**: Connects devices within a limited area using Ethernet (e.g., home, office).
- **WLAN (Wireless Local Area Network)**: A LAN that uses wireless communication (e.g., Wi-Fi).
- **CAN (Campus Area Network)**: Connects multiple LANs within a limited area (e.g., university).
- **MAN (Metropolitan Area Network)**: Connects LANs across a city or region.
- **WAN (Wide Area Network)**: Connects LANs across large geographical areas (e.g., the internet).
- **VPN (Virtual Private Network)**: Creates a secure connection over the internet to a private network.


## Network Topologies
- **Bus**: All devices share a single communication line.
- **Star**: All devices connect to a central hub.
- **Ring**: Each device connects to two others, forming a circle.
- **Mesh**: Every device connects to every other device.
- **Tree**: A hierarchical structure with a root and branches.

## Network Protocols
- **HTTP/HTTPS**: For web communication.
- **FTP**: For file transfer.
- **SMTP**: For email transmission.
- **TCP/IP**: For reliable data transmission.
- **UDP**: For faster, connectionless communication.


## OSI Model

OSI (Open Systems Interconnection) model is a conceptual framework that standardizes the functions of a telecommunication or computing system into seven layers:

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