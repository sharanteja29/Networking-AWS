# My Detailed Notes: Network Models, OSI Model, TCP/IP, and Data Delivery

> **My goal:** I want to understand how data travels from my device to a server, how different devices communicate, and how network models help organise that process. These notes follow the transcript and include extra explanations and technical clarifications.

---

## 1. Why Do We Need Network Models?

When I watch YouTube, my phone or laptop sends requests through my local network, router, Internet Service Provider (ISP), and the Internet to YouTube's servers. The server processes the request and sends data back.

The devices involved may come from different manufacturers and run different operating systems. My phone might run Android or iOS, my laptop might run Windows or Linux, and servers may run different Linux distributions. They can still communicate because they follow common networking standards and protocols.

A **network model** is a conceptual way of organising network communication into layers. Each layer has specific responsibilities and interacts with the layers above and below it.

### Why are layers useful?

- **Separation of responsibilities:** Each layer focuses on a particular part of communication.
- **Interoperability:** Devices from different vendors can communicate when they implement compatible standards and protocols.
- **Independent development:** A technology at one layer can often be improved without redesigning every other layer.
- **Troubleshooting:** I can narrow a problem down to physical connectivity, IP routing, transport, or an application.
- **Flexibility:** Different technologies can work together when their interfaces and protocols are compatible.

For example, upgrading an Ethernet link to a faster supported speed does not normally require rewriting a web browser.

**Important:** A network model is a way to describe and organise networking. It is not a physical device, and the Internet does not literally contain separate boxes for every layer.

---

## 2. Who Develops Networking Standards?

Networking standards and protocols are developed and maintained by different organisations. Two important examples are:

- **IEEE (Institute of Electrical and Electronics Engineers):** Develops standards such as Ethernet (IEEE 802.3) and Wi-Fi standards in the IEEE 802.11 family.
- **IETF (Internet Engineering Task Force):** Develops and publishes many Internet protocol specifications, including those related to IP, TCP, UDP, and HTTP.

Other standards organisations also contribute. No single company defines every aspect of networking.

---

## 3. OSI Model and TCP/IP Model

Two models commonly used to explain network communication are:

1. **OSI model:** Seven layers; a conceptual reference model.
2. **TCP/IP model:** Usually described as four layers; closely related to the protocol suite used by the Internet.

The OSI model helps me reason about the responsibilities involved in communication. The TCP/IP model groups those responsibilities in a way that more closely reflects real Internet protocols.

### OSI layers from top to bottom

| Layer | Name | Main responsibility | Examples |
|---:|---|---|---|
| 7 | Application | Network services used by applications | HTTP, DNS, SMTP |
| 6 | Presentation | Data representation, encoding, compression and encryption concepts | Character encoding, data formats |
| 5 | Session | Establishing, managing and ending communication sessions | Session-control concepts |
| 4 | Transport | Process-to-process communication, ports and reliability where provided | TCP, UDP |
| 3 | Network | Logical addressing and forwarding between networks | IP, routers |
| 2 | Data Link | Local-link delivery, framing and MAC addressing | Ethernet, Wi-Fi link layer, switches |
| 1 | Physical | Transmitting raw bits as signals over a medium | Copper, fibre, radio signals |

### Mnemonics to remember the layers

Top to bottom (Layer 7 to Layer 1):

**A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing

- Application
- Presentation
- Session
- Transport
- Network
- Data Link
- Physical

Bottom to top (Layer 1 to Layer 7):

**P**lease **D**o **N**ot **T**ell **S**tupid **P**eople **A**nything

- Physical
- Data Link
- Network
- Transport
- Session
- Presentation
- Application

I can use whichever mnemonic is easier to remember.

---

## 4. Understanding Each OSI Layer

### Layer 7 — Application Layer

The application layer provides network services that applications use. Examples:

- A browser uses HTTP or HTTPS to request web resources.
- An email client may use SMTP to send email.
- A device may use DNS to look up a domain name.

**Example:** When I open a website, the browser creates an HTTP request for a page, image, or other resource.

### Layer 6 — Presentation Layer

The presentation layer describes how data is represented so the receiving system can interpret it.

Concepts associated with this layer include:
- Data-format conversion and encoding.
- Character encoding, such as UTF-8.
- Compression and decompression.
- Encryption and decryption in the conceptual OSI view.

**Clarification:** In real TCP/IP networks, these functions do not always occur in one separate presentation layer. They may be handled by application libraries, data formats, or security protocols. TLS is often discussed in this layer conceptually, but it is not necessarily a literal standalone OSI Layer 6 component.

### Layer 5 — Session Layer

The session layer represents the management of communication sessions between applications, including starting, maintaining, coordinating, and ending a dialogue.

Session-related concepts may include:
- Establishing a logical dialogue.
- Managing the state of a conversation.
- Coordinating exchanges and recovery points in systems that support them.

**Important correction:** Authentication and authorisation are not exclusively functions of the OSI session layer. They can be implemented at multiple layers and in application protocols. For example, a website may authenticate me through an application-level login flow.

### Layer 4 — Transport Layer

The transport layer provides communication between application processes running on different hosts.

Important concepts:
- **Ports:** Help identify source and destination application processes.
- **Segmentation:** Dividing application data into smaller transport units when needed.
- **Reassembly:** Reconstructing data at the receiving end when the protocol supports it.
- **Reliability:** TCP provides ordered, reliable byte-stream delivery using acknowledgements and retransmissions.
- **Flow and congestion control:** TCP has mechanisms to manage receiver capacity and network congestion.
- **UDP:** Provides datagrams without TCP's built-in reliability, ordering, or connection setup.

Examples include TCP and UDP.

A port number helps the operating system deliver received transport data to the appropriate process or socket.

Examples:
- HTTPS commonly uses TCP port `443`.
- SMTP commonly uses TCP port `25` for server-to-server mail transfer; other ports are used for message submission.

**Clarification:** HTTPS does not always mean TCP. HTTP/3 uses QUIC over UDP, commonly on port `443`.

### Layer 3 — Network Layer

The network layer handles logical addressing and forwarding between different networks.

Important concepts include:
- IP addresses.
- IP packets.
- Routing.
- Choosing a next hop based on routing information.

For example, my laptop may have a private IP address such as `192.168.1.10`, while a remote server has a different IP address. IP addressing allows packets to be addressed across interconnected networks.

Routers mainly make forwarding decisions using Layer 3 information.

**Important:** Routing does not guarantee that the absolute fastest or shortest path is chosen. Routers forward according to routing tables, routing protocols, policies, and metrics.

### Layer 2 — Data Link Layer

The data link layer handles delivery over a local network link.

Important concepts:
- **Frames:** Data units used by link-layer technologies such as Ethernet.
- **MAC addresses:** Addresses used for delivery on many local network links.
- **Framing:** Packaging a network-layer packet inside a link-layer frame.
- **Error detection:** Ethernet commonly uses a frame check sequence to detect certain transmission errors.
- **Media access:** Rules for sharing a wired or wireless medium.

A switch commonly forwards Ethernet frames based on its MAC address table.

When an IP packet travels through multiple routed Ethernet links, the Layer 2 frame can be replaced at each routed hop. The IP packet is carried inside a new frame appropriate for the next link.

### Layer 1 — Physical Layer

The physical layer represents the transmission of raw bits as physical signals.

Examples:
- Copper Ethernet cable.
- Fibre-optic cable.
- Radio waves used by Wi-Fi.

The physical layer concerns signal characteristics, connectors, transmission rates, and other physical signalling details.

If a cable is unplugged, a radio signal is too weak, or a port is damaged, the issue may be at the physical layer.

---

## 5. The TCP/IP Model

The TCP/IP model is commonly described using four layers.

| TCP/IP layer | Main responsibility | Approximate OSI mapping | Examples |
|---|---|---|---|
| Application | Protocols and data used by network applications | OSI Layers 5–7 | HTTP, DNS, SMTP, SSH |
| Transport | Process-to-process communication using ports | OSI Layer 4 | TCP, UDP |
| Internet | IP addressing and routing between networks | OSI Layer 3 | IPv4, IPv6, ICMP |
| Link / Network Access | Local-link delivery and physical transmission | OSI Layers 1–2 | Ethernet, Wi-Fi |

Some textbooks use a five-layer Internet model by separating physical and data-link functions. The four-layer TCP/IP model combines them into the Link or Network Access layer.

### How OSI and TCP/IP relate

The models are not identical. OSI has seven conceptual layers, while the common TCP/IP model has four. The mapping is approximate because real protocols do not always fit neatly into one OSI layer.

I should use the OSI model to understand responsibilities and the TCP/IP model to understand how Internet protocols are commonly grouped.

---

## 6. Practical Example: Opening YouTube in a Browser

Suppose I open a browser and visit YouTube.

1. **Application:** The browser needs web content. It uses HTTP semantics, usually protected by TLS when using HTTPS, to request the required resource.
2. **Transport:** The data is sent using a transport protocol. Commonly this is TCP, but HTTP/3 uses QUIC over UDP. Port numbers help identify the destination service; HTTPS commonly uses port `443`.
3. **Internet / Network:** IP adds logical source and destination addresses so packets can be forwarded across networks.
4. **Link:** My device sends the IP packet inside a link-layer frame to the next hop, such as my home router over Wi-Fi or Ethernet.
5. **Physical transmission:** The frame is transmitted as signals over radio, copper, or fibre, depending on the connection.

At the server, the receiving system processes the data in the reverse direction. Each relevant layer interprets and removes its own protocol information and passes the remaining data upward. The server's response follows an appropriate return path.

**Important:** The path may include many routers, switches, wireless links, and service-provider networks. The exact route can change, and the return path does not have to be identical to the forward path.

---

## 7. Encapsulation and Decapsulation

These are fundamental networking concepts.

### What is encapsulation?

**Encapsulation** happens when data moves down the networking stack on the sending device. Each layer adds the protocol information it needs.

```text
Application data
       |
       v
Transport header + application data
       = TCP segment / UDP datagram
       |
       v
IP header + transport unit
       = IP packet
       |
       v
Link header + IP packet + link trailer (where used)
       = Link-layer frame
       |
       v
Bits/signals transmitted over the medium
```

For example:
1. The application produces data.
2. TCP may add source and destination ports and other TCP control information.
3. IP adds source and destination IP addresses.
4. Ethernet or Wi-Fi link-layer processing packages the packet into a frame appropriate for the local link.
5. The physical layer transmits the encoded bits as signals.

### What is decapsulation?

**Decapsulation** happens at the receiving side as data moves up the stack.

```text
Received signals
       |
       v
Bits interpreted by the link layer
       |
       v
Frame header/trailer processed
       |
       v
IP packet processed
       |
       v
TCP segment / UDP datagram processed
       |
       v
Application data delivered to the correct process
```

Each layer processes the information relevant to its protocol and passes the payload to the next layer.

### What happens at a router?

A router normally processes the incoming link-layer framing, examines the IP packet, makes a forwarding decision, and sends the packet in a new link-layer frame on the outgoing interface.

The Layer 2 header and trailer generally change at each routed link. The IP packet is forwarded, though certain IP fields such as TTL or Hop Limit are updated. NAT or other network functions may also modify packet headers.

---

## 8. Protocol Data Units (PDUs)

A **Protocol Data Unit (PDU)** is the unit of data handled at a particular layer.

| Layer / context | Common PDU name | What it contains |
|---|---|---|
| Application | Data or message | Application-specific information |
| Transport with TCP | Segment | TCP header and application payload |
| Transport with UDP | Datagram | UDP header and application payload |
| Internet / Network | Packet | IP header and transport payload |
| Data Link | Frame | Link header, packet payload, and often a trailer |
| Physical | Bits / signals | Encoded representation transmitted over the medium |

### What is a payload?

A **payload** is the part carried inside a protocol unit, excluding that unit's own control information.

For example:
- A TCP segment carries application data as its payload.
- An IP packet carries a TCP segment or UDP datagram as its payload.
- An Ethernet frame carries an IP packet as its payload.

The exact structure depends on the protocol and encapsulation in use.

---

## 9. Four Communication Delivery Types

The transcript introduces four ways to describe how traffic is delivered: unicast, broadcast, multicast, and anycast.

### 9.1 Unicast — One to One

Unicast communication is between one sender and one intended destination.

Examples:
- My laptop connects to a particular web server.
- I connect to a cloud virtual machine over SSH.
- A client exchanges data with a server.

Unicast is the common model for many ordinary client-server connections.

### 9.2 Broadcast — One to All on a Broadcast Domain

Broadcast traffic is sent to all relevant devices within a broadcast domain on a network technology that supports broadcast.

Examples:
- An IPv4 broadcast can be used for certain local-network discovery operations.
- DHCP clients may use broadcast during parts of address configuration when they do not yet know the DHCP server's address.

Broadcast does **not** mean that a message automatically reaches every device on the entire Internet. Routers generally do not forward ordinary Layer 2 broadcasts between networks.

### 9.3 Multicast — One to a Group

Multicast sends traffic to a group of interested receivers rather than individually addressing every receiver or sending to everyone.

Examples:
- Certain live-streaming and media-distribution systems.
- Routing protocols and other network services that use multicast.
- Group communication on networks that support it.

**Clarification:** A members-only YouTube stream is not necessarily an example of IP multicast. Access control to a stream and multicast delivery are different concepts. Public Internet video services commonly use unicast delivery, often with content delivery networks.

### 9.4 Anycast — One to the Appropriate One of Several Instances

With anycast, the same IP address is announced or served from multiple locations. Network routing directs a client to one of those instances, commonly one that is topologically close or preferable according to routing policy.

Example:
- A global DNS service may advertise the same service IP from multiple locations. A query can reach one of the nearby or otherwise preferred instances.

Anycast is useful for global DNS services, content delivery and edge services, and improving service reachability.

**Important:** “Nearest” usually means nearest according to network routing and policy, not necessarily the smallest physical distance. Anycast does not guarantee that every request goes to the geographically closest server.

### Comparison

| Delivery type | Basic idea | Typical scope / note |
|---|---|---|
| Unicast | One sender to one destination | Common for web and SSH connections |
| Broadcast | One sender to all devices in a broadcast domain | Not normally routed across the Internet |
| Multicast | One sender to a subscribed or interested group | Requires multicast-capable network support |
| Anycast | One service address used at multiple locations; routing selects an instance | Common in global DNS and edge services |

---

## 10. How DNS Fits into the Example

When I type a domain name such as `example.com`, my computer needs to discover the relevant IP address or other DNS record.

A simplified DNS lookup works like this:

1. My application asks the operating system to resolve the domain name.
2. The system may check local caches and configured name-resolution mechanisms.
3. If needed, a DNS resolver receives a query.
4. The resolver finds or retrieves the relevant DNS records.
5. The answer is returned and may be cached for a period determined partly by the record's TTL.
6. My application can then attempt to connect to the destination.

A domain name does not itself identify a physical machine. DNS can return different kinds of records and may return different addresses depending on configuration, location, and other factors.

### DNS and anycast

Some public DNS resolver services use anycast. A resolver IP address can be announced from many locations, and routing delivers a query to one instance.

For example, Cloudflare's public DNS resolver is commonly available at `1.1.1.1`. That address can be served from multiple locations; it does not represent one single physical server worldwide.

**Clarification:** Anycast and DNS are related in some deployments, but they are not the same thing. DNS is a name-resolution protocol; anycast is a network-addressing and routing technique.

---

## 11. Common Misunderstandings to Avoid

1. **OSI is a conceptual reference model, not a literal map of physical devices.** A device can perform functions associated with several layers.
2. **TCP/IP has different textbook representations.** The four-layer model combines the physical and data-link functions into one link layer; a five-layer teaching model separates them.
3. **HTTPS does not always use TCP.** HTTP/1.1 and HTTP/2 commonly use TCP, while HTTP/3 uses QUIC over UDP.
4. **Ports identify transport-layer endpoints, not physical ports.** A TCP/UDP port number is different from an Ethernet socket on a switch.
5. **Routers do not necessarily choose the absolute fastest path.** They forward according to routing tables, metrics, and policy.
6. **Broadcast does not reach the entire Internet.** Ordinary Layer 2 broadcasts remain within a broadcast domain.
7. **Multicast is not simply a private or members-only stream.** It is a specific network delivery method.
8. **Anycast does not guarantee the geographically nearest server.** Routing topology and policy determine which instance is reached.
9. **Authentication is not exclusively an OSI session-layer responsibility.** It can happen at different layers and in application protocols.
10. **Encapsulation is more than adding arbitrary headers.** Each protocol adds structured information that receiving systems interpret according to that protocol's rules.

---

## 12. Troubleshooting Using Layers

When something does not work, I can use the layered approach to narrow down the problem.

| Symptom | Areas to investigate |
|---|---|
| No link or Wi-Fi connection | Physical layer, cable, radio signal, NIC, access point |
| Connected to Wi-Fi but no local connectivity | Link layer, IP configuration, subnet, DHCP |
| Local devices work but Internet access fails | Default gateway, routing, ISP connectivity, firewall |
| IP address works but domain name does not resolve | DNS configuration, resolver reachability, cached records |
| Domain resolves but connection fails | Routing, firewall rules, destination availability, port, transport protocol |
| TCP connection works but the website fails | TLS certificate/handshake, HTTP response, application/server logs |
| Website is slow | DNS latency, packet loss, congestion, CDN path, server load, application performance |

These are starting points, not absolute rules. A single symptom can have causes at several layers, so I should test hypotheses rather than assume the first suspected layer is responsible.

---

## 13. Revision Questions

I should try answering these without looking at the notes.

1. Why do different vendors need common networking standards?
2. What is a network model?
3. What does OSI stand for?
4. What are the seven OSI layers in order?
5. What are the four layers of the TCP/IP model?
6. How do the OSI and TCP/IP models differ?
7. Which layer is associated with MAC addresses and frames?
8. Which layer is responsible for IP addressing and routing?
9. What is the role of TCP and UDP?
10. Why do applications use port numbers?
11. What is encapsulation?
12. What is decapsulation?
13. What is a PDU?
14. What is the difference between a segment, packet, and frame?
15. What is a payload?
16. What is the difference between unicast and broadcast?
17. How is multicast different from anycast?
18. Why does broadcast traffic not normally cross routers?
19. How can anycast help a global DNS service?
20. Why is it inaccurate to say that the session layer alone handles authentication?
21. Why is HTTPS not always carried over TCP?
22. If a website works by IP address but not by domain name, what should I investigate first?
23. If a cable is unplugged, which layer should I check first?
24. Why can the Layer 2 frame change at every router hop while traffic is still travelling to the same IP destination?

---

## 14. Final Summary — What I Learned

- Network models organise communication into layers so different technologies can work together.
- The OSI model has seven layers: Application, Presentation, Session, Transport, Network, Data Link, and Physical.
- The common TCP/IP model has four layers: Application, Transport, Internet, and Link.
- IEEE develops standards such as Ethernet and Wi-Fi; the IETF develops many Internet protocol specifications.
- The transport layer supports process-to-process communication using ports. TCP provides reliable ordered byte-stream delivery, while UDP provides datagrams without TCP's built-in reliability.
- The Internet layer uses IP addressing and routing to move packets between networks.
- The link layer handles local-link framing and delivery; the physical layer transmits signals.
- Encapsulation adds protocol information as data moves down the sender's stack. Decapsulation processes it on the receiving side.
- Common PDU names include data, segment, datagram, packet, frame, and bits.
- Unicast is one-to-one, broadcast is one-to-all within a broadcast domain, multicast is one-to-group, and anycast routes a shared service address to one of multiple instances.
- DNS resolves domain names; anycast can help a DNS service operate from multiple locations.
- The layered model is useful for troubleshooting, but real systems can involve multiple layers at once.

**My main takeaway:** When I open a website, data is handled by application protocols, transport protocols, IP, and link technologies in a coordinated way. Each layer contributes its own information and responsibilities, allowing my device to communicate with a remote server across many different networks.
