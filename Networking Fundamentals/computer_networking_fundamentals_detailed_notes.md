# My Computer Networking Fundamentals Notes
## My Notes from the Networking Bootcamp

> **My goal:** I am using these notes to understand networking fundamentals from the ground up, especially for DevOps and cloud. I have kept the lesson's main order and examples, and added clarifications where a simplified explanation could otherwise confuse me later.

## Table of Contents
1. [Introduction: Networking for DevOps](#1-introduction-networking-for-devops)
2. [How to Learn the Bootcamp](#2-how-to-learn-the-bootcamp)
3. [Bootcamp Syllabus](#3-bootcamp-syllabus)
4. [History and Purpose of the Internet](#4-history-and-purpose-of-the-internet)
5. [Computer Networks, Hosts, and Networking](#5-computer-networks-hosts-and-networking)
6. [What Is the Internet?](#6-what-is-the-internet)
7. [Physical Infrastructure and Submarine Cables](#7-physical-infrastructure-and-submarine-cables)
8. [Internet vs. World Wide Web](#8-internet-vs-world-wide-web)
9. [Client–Server Architecture](#9-clientserver-architecture)
10. [Types of Networks: PAN, LAN, MAN, WAN](#10-types-of-networks-pan-lan-man-wan)
11. [Network Topology](#11-network-topology)
12. [Quick Comparison Tables](#12-quick-comparison-tables)
13. [Important Clarifications](#13-important-clarifications)
14. [Revision Questions](#14-revision-questions)
15. [Glossary](#15-glossary)

---

## 1. Introduction: Networking for DevOps

### What I want to understand

I want to understand how devices, applications, servers, and cloud resources communicate. This will help me troubleshoot real systems instead of memorising networking definitions.

I am learning networking because it is a core foundation for DevOps. DevOps involves practices and tools used to build, test, release, deploy, operate, and maintain software products.

### DevOps and cloud are related, but not identical

- **Cloud computing** concerns computing resources delivered through a provider or platform—for example, virtual machines, storage, databases, and managed services.
- **DevOps** focuses on improving how software is built, tested, released, deployed, monitored, and operated.
- Cloud is one part of many DevOps environments, but DevOps is not simply another name for cloud engineering.

Networking matters in DevOps because applications, servers, containers, cloud resources, monitoring systems, and users must communicate reliably and securely.

### Why networking fundamentals matter

A DevOps or software engineer may need to understand:
- How a request travels from a user's device to a server.
- How IP addresses identify network interfaces or endpoints.
- How routers move packets between networks.
- How ports help traffic reach the correct application.
- How firewalls control allowed and blocked traffic.
- How load balancers distribute requests.
- How private networks and subnets are arranged in cloud environments.
- How to diagnose connectivity failures.

I should understand the fundamentals before jumping into advanced subjects such as cloud architecture, AI, or system design. These areas build on foundations such as networking and operating systems.

---

## 2. How to Learn the Bootcamp

These are the learning habits I can use while studying this bootcamp.

I will follow three useful learning habits.

### 2.1 Take active notes

Use a physical notebook or a digital note-taking tool. Pause the video when needed and record:
- Key definitions.
- Important diagrams.
- Examples.
- Differences between similar concepts.
- A short summary of each chapter.

Writing notes is intended to make learning active rather than simply watching a video passively. Do not attempt to transcribe every sentence; capture the concepts and how they connect.

### 2.2 Learn in public

Share learning progress, notes, or short explanations on professional or social platforms. Possible formats include:
- A short progress update.
- A post explaining one networking concept.
- A chapter-wise article.
- A diagram with a practical example.
- A public repository containing notes and hands-on exercises.

This can help with consistency, communication skills, feedback, and demonstrating evidence of learning. Public posting is optional; a private learning log is a reasonable alternative if public sharing is uncomfortable.

### 2.3 Do not rush the foundations

Advanced topics become easier when the basics are understood well. Networking concepts are interconnected: later topics often depend on earlier ones.

A useful sequence is:
1. Understand the concept in plain language.
2. Draw or inspect a diagram.
3. Explain it in your own words.
4. Try a small practical example.
5. Revisit it while studying the next related topic.

Knowing terminology for an exam is not the same as understanding how a real network behaves.

---

## 3. Bootcamp Syllabus

The bootcamp is divided into eight broad chapters. This is my overview of what I will study.

### Chapter 1 — Networking Fundamentals
- What a computer network is.
- Why the Internet developed.
- Basic networking terminology.
- The Internet and the World Wide Web.
- Client–server architecture.
- Network types: PAN, LAN, MAN, and WAN.
- Network topologies: bus, ring, star, mesh, and tree.

### Chapter 2 — Network Models
- Why layered network models are used.
- The benefits of separating networking responsibilities into layers.
- The TCP/IP model.
- The OSI model.

### Chapter 3 — Networking Devices
- Different network devices.
- Their roles in communication.
- How devices relate to the layers of network models.
- How devices help connect networks.

### Chapter 4 — Network Layer
- How data is routed from one network or endpoint toward another.
- IP addressing and network-layer responsibilities.
- How a packet can cross multiple networks.

### Chapter 5 — Transport Layer
- End-to-end transport between applications.
- How transport protocols support communication.
- How traffic is directed to the relevant application using port numbers.

### Chapter 6 — Application Layer
- Protocols used by applications.
- HTTP and HTTPS/TLS concepts.
- SSH and other application-facing protocols.
- How applications request and exchange information.

### Chapter 7 — Managing Infrastructure
- Proxies.
- Load balancers.
- Securing and managing larger infrastructure.
- Connecting components into a practical architecture.

### Chapter 8 — Applied Networking for DevOps
- Hands-on application of the earlier concepts.
- Practical network setups.
- Applying networking knowledge to DevOps and cloud scenarios.
- Using cloud computing to practise when physical networking equipment is unavailable.

I noted that the first seven chapters are useful across many technical roles, including software development, testing, backend, frontend, cloud, networking, cybersecurity, and AI engineering. The final chapter focuses the concepts on DevOps and cloud use cases.

---

## 4. History and Purpose of the Internet

### 4.1 The problem that motivated early network research

I learned that early networking research was partly motivated by the need for resilient communication during the Cold War. One important goal was to allow connected computers to communicate without depending entirely on one central communication path.

If one link or node became unavailable, a network with alternative routes could potentially continue carrying traffic.

### 4.2 ARPANET

- **ARPANET** stands for Advanced Research Projects Agency Network.
- It was funded by the US Department of Defense's research agency.
- It began operating in 1969 and connected research institutions.
- It became an important precursor to today's Internet.

The original idea was not to create today's web of websites and social media. It was to enable computers at different institutions to communicate and share resources.

### 4.3 The first message

On 29 October 1969, a message was sent from UCLA toward the Stanford Research Institute system. The intended word was **“LOGIN”**, but the system failed after the first two characters, **“LO”**, were received.

This is a famous early milestone in the history of computer networking.

### 4.4 TCP/IP and a common set of rules

As networks grew, they needed shared rules so that different systems could communicate. In 1983, ARPANET adopted TCP/IP as its standard networking protocol suite.

- **TCP** stands for Transmission Control Protocol.
- **IP** stands for Internet Protocol.
- IP supports addressing and forwarding packets between networks.
- TCP provides reliable, ordered delivery of a byte stream between endpoints when a connection is functioning normally.

TCP/IP did not mean every device became identical. It meant that devices and networks could interoperate by following shared protocols.

---

## 5. Computer Networks, Hosts, and Networking

### 5.1 What is a computer network?

A **computer network** is a set of connected devices that can exchange data or share resources using communication links and agreed protocols.

Resources may include:
- Files and data.
- Printers.
- Applications.
- Storage.
- Internet connectivity.
- Services running on other computers.

A network may use wired links, wireless links, or a combination of both.

### 5.2 What is a node or host?

A **node** is a device or connection point in a network. A **host** generally means an end system that sends or receives network communication, such as:
- A desktop computer.
- A laptop.
- A mobile phone.
- A server.
- A virtual machine.

A host is often described as a device with an IP address. More precisely, an IP address is assigned to a network interface, and not every node is necessarily an IP host. A device can have multiple interfaces or addresses.

### 5.3 What is networking?

**Networking** is the process and set of techniques that enable devices to communicate and exchange data or share resources.

A useful distinction:
- **Computer network:** the connected system or infrastructure.
- **Networking:** the communication and configuration processes that make the system work.

### Example

Suppose a laptop sends a document to a network printer:
1. The laptop creates data to send.
2. The operating system and networking software prepare it for transmission.
3. The data crosses the local network.
4. The printer receives the data and processes the print job.

The exact protocols and steps depend on the network and printing setup, but the example illustrates resource sharing over a network.

---

## 6. What Is the Internet?

The **Internet is a network of networks**. It links many independently operated networks using shared protocols and interconnections.

Examples of networks that participate in Internet connectivity include:
- A home Wi-Fi or Ethernet network.
- An office network.
- A university network.
- A mobile carrier's network.
- An Internet Service Provider's (ISP's) network.
- A data centre's network.
- Networks operated by content and cloud providers.

### 6.1 How networks connect

A simplified path might look like this:

`Laptop/Phone → Home Router → ISP Network → Other Networks → Destination Server`

The real path may contain many routers and networks, and it can vary from one request to another.

### 6.2 Who owns the Internet?

No single organisation owns or operates the entire Internet. Different organisations own and manage portions of its infrastructure:
- ISPs manage access networks and other network infrastructure.
- Cloud and hosting companies operate data centres and servers.
- Businesses operate their own networks.
- Other network operators provide long-distance links and interconnections.

The Internet works through cooperation, shared protocols, routing, and interconnection among these networks.

### 6.3 The Internet is physical infrastructure

Although users experience the Internet through software, it relies on physical equipment:
- Fibre-optic and copper cables.
- Wireless radio links.
- Routers and switches.
- Data centres and servers.
- Submarine fibre-optic cables.
- Landing stations and other supporting infrastructure.

This is important: the Internet is not merely a website or an abstract service. Software uses a real, physical communication infrastructure.

---

## 7. Physical Infrastructure and Submarine Cables

### 7.1 How data can travel between countries

Imagine a user in India accessing a server in the United States. A simplified path is:

1. The user's device sends traffic through Wi-Fi or Ethernet to the local router or access point.
2. The traffic reaches the ISP's network.
3. Routers forward packets through interconnected networks.
4. For many intercontinental paths, traffic travels over submarine fibre-optic cable systems.
5. The traffic reaches networks near the destination data centre.
6. The destination server processes the request and sends a response back through a route that may not be identical to the forward route.

Wi-Fi normally carries traffic only over a local radio link; it does not directly span the distance from India to the United States.

### 7.2 What are submarine cables?

Submarine cables are communication cables laid on or beneath the seabed. Modern international submarine systems commonly use optical fibre to carry enormous amounts of data as light signals.

They connect landing stations on different coasts and form a major part of global intercontinental communications.

### 7.3 Why they matter

- They provide high-capacity international connectivity.
- They help connect continents, countries, ISPs, and data centres.
- They are a physical dependency for many global services.
- Cable outages can affect capacity or connectivity, although traffic may be rerouted if alternatives are available.

I can use **Submarine Cable Map** to explore cable routes and landing points. If I rely on it for current information, I should verify the latest routes and operational status on the map itself.

---

## 8. Internet vs. World Wide Web

These terms are related but are not interchangeable.

### 8.1 Internet

The **Internet** is the global network infrastructure and the protocols that let connected networks exchange data. It carries many kinds of traffic, including:
- Web pages.
- Email.
- Messaging.
- Voice and video calls.
- Online games.
- File transfers.
- Remote administration.
- Other application data.

### 8.2 World Wide Web (WWW)

The **World Wide Web** is a system of interlinked resources—such as web pages and web applications—that users commonly access through browsers over the Internet.

I learned that Tim Berners-Lee developed the Web in the early 1990s. Three foundational Web technologies are HTML, HTTP, and URLs.

#### HTML — HyperText Markup Language
- Describes the structure and content of a web document.
- Can represent headings, paragraphs, links, images, forms, and other page elements.

#### HTTP — Hypertext Transfer Protocol
- Defines how clients request Web resources and how servers exchange responses.
- HTTPS is HTTP protected by TLS in common modern deployments.

#### URL — Uniform Resource Locator
- Identifies the location and access method for a resource.
- A URL often contains a scheme, host, optional port, path, and query parameters.

### 8.3 How the pieces fit together

For a simplified browser request:
1. A user enters a URL.
2. The browser determines the destination host and resolves its name when necessary.
3. The browser establishes the required network connection.
4. It sends an HTTP request, commonly protected by TLS when using HTTPS.
5. The server responds with HTML or another resource.
6. The browser interprets the response and may request additional resources.

HTML, HTTP, and URLs are central Web technologies, but the modern Web also relies on many additional standards and protocols.

### Quick analogy

- **Internet:** the road and transport infrastructure.
- **World Wide Web:** one service that uses that infrastructure.

The analogy is imperfect, but it helps distinguish the underlying network from an application ecosystem running on top of it.

---

## 9. Client–Server Architecture

Client–server architecture is a common pattern in web applications, cloud systems, and many networked services.

### 9.1 Client

A **client** initiates a request for a resource or service. Examples include:
- A web browser requesting a page.
- A mobile application requesting account data.
- A command-line tool requesting an API endpoint.
- A test script sending a request to an application.

The client is defined by its role in the interaction, not simply by the physical device it runs on.

### 9.2 Server

A **server** is a program or system that waits for or accepts requests and provides responses or services. The word can refer to:
- The server software process.
- The computer or virtual machine running that software.
- The broader server-side system.

A server does not have to be a huge, specialised physical machine. A developer can run a small server program on a laptop for local development and testing.

### 9.3 Ports and listening services

Server software commonly listens on a port for incoming traffic. A port helps the operating system deliver traffic to the intended application or service.

For example:
- A development web server might listen on port `8000`.
- A web server commonly uses port `80` for HTTP.
- HTTPS commonly uses port `443`.
- SSH commonly uses port `22`.

These are common defaults, not guarantees. Services can be configured to use other ports, and firewalls or network policies may block access.

### 9.4 Request–response flow

A basic interaction can be represented as:

```text
Client                         Server
  |                               |
  |------ Request --------------->|
  |                               | Process request
  |<----- Response ---------------|
  |                               |
```

Example: a browser requests a product page. The server receives the request, runs the relevant application logic, and returns a response. That response may contain HTML, JSON, an image, an error, or another type of content.

### 9.5 One machine can play both roles

The roles are logical. One computer can run a client and a server at the same time. For example, a developer may run a browser as a client and a local development server on the same laptop.

A server's capacity depends on its hardware, software, workload, and configuration. A server may handle many simultaneous requests, but it is not correct to assume every single server can handle thousands or millions of requests without limits.

---

## 10. Types of Networks: PAN, LAN, MAN, WAN

Networks are often classified by the geographic area they cover or the purpose they serve. The boundaries are approximate rather than rigid.

### 10.1 PAN — Personal Area Network

**PAN** stands for **Personal Area Network**.

- Covers a very small area around an individual.
- Connects personal devices.
- Often uses Bluetooth or other short-range technologies.

Examples:
- Wireless earbuds connected to a phone.
- A smartwatch synchronising with a phone.
- A phone communicating with a nearby personal accessory.

**Typical purpose:** connect devices used by one person over a short range.

### 10.2 LAN — Local Area Network

**LAN** stands for **Local Area Network**.

- Covers a relatively small area, such as a home, office, lab, or campus building.
- Connects computers, printers, servers, access points, and other devices.
- Often uses Ethernet and Wi-Fi.
- Commonly supports local resource sharing and Internet access.

Example: six office computers and a printer connect through network equipment so they can communicate and access shared resources.

A LAN can be privately managed, but “LAN” primarily describes the local scope; it does not by itself guarantee that the network is secure or private.

### 10.3 MAN — Metropolitan Area Network

**MAN** stands for **Metropolitan Area Network**.

- Covers a city or a metropolitan region.
- Can connect multiple LANs across buildings or sites.
- May be used by organisations, institutions, or network providers.

Example: a university or organisation connects facilities spread across a city.

The transcript also uses the idea of multiple sites in a cloud region to help illustrate a larger geographic scale. Cloud regions and availability zones are provider-specific architecture concepts, however, and should not automatically be equated with a MAN.

### 10.4 WAN — Wide Area Network

**WAN** stands for **Wide Area Network**.

- Covers large geographic areas, potentially across countries or continents.
- Connects networks that are far apart.
- May use leased lines, carrier networks, VPNs, or other technologies.

Example: a bank connects offices in Hyderabad, Mumbai, Bengaluru, London, and New York.

A WAN does not have to be the public Internet. An organisation can operate or contract a private WAN for its own sites.

### 10.5 The Internet as a network of networks

The Internet interconnects many networks across local, metropolitan, regional, and global scales. It is not simply one LAN or one WAN owned by a single company.

---

## 11. Network Topology

**Network topology** describes how devices and communication links are arranged and connected. The chosen topology affects cost, performance, scalability, complexity, and failure behaviour.

I learned about five common network topologies.

### 11.1 Bus topology

**Structure:** multiple devices connect to a shared main cable or backbone.

```text
Device A ---- Device B ---- Device C ---- Device D
             Shared backbone
```

**Advantages**
- Can be simple and inexpensive for small or legacy setups.
- Uses a shared backbone.

**Disadvantages**
- A backbone fault can disrupt communication for many devices.
- Fault isolation can be difficult.
- Performance can degrade as shared-medium traffic increases.
- Adding devices and managing the cable can become awkward.

The WhatsApp-group comparison in the transcript is only an informal analogy: a shared cable is a physical/logical medium, not literally a chat group.

### 11.2 Ring topology

**Structure:** each device connects to neighbouring devices, forming a loop.

```text
Device A ---- Device B
   |              |
Device D ---- Device C
```

Data may travel around the ring according to the protocol used.

**Advantages**
- Can provide orderly access to a shared path in certain designs.
- Some ring technologies can provide a secondary path or protection mechanism.

**Disadvantages**
- A break or device failure can disrupt a simple unprotected ring.
- Troubleshooting and expansion can be more complex than in a basic star network.

Do not assume every ring forwards data through every device in exactly the same way; the details depend on the technology and protocol.

### 11.3 Star topology

**Structure:** every device connects to a central device, commonly a switch in a wired LAN.

```text
             Device A
                |
Device B ---- Switch ---- Device C
                |
             Device D
```

**Advantages**
- Easy to add or remove an endpoint.
- A failure in one endpoint's link usually affects that endpoint rather than all others.
- Centralised switching can make troubleshooting easier.

**Disadvantages**
- The central switch or its power/link can become a single point of failure if there is no redundancy.
- Requires a separate link from each endpoint to the central device.

Star topology is common in modern Ethernet LANs. In a switched star, the switch forwards frames based on its learned forwarding information; it does not simply broadcast every piece of traffic to every device in all circumstances.

### 11.4 Mesh topology

**Structure:** devices or network nodes have multiple interconnections. In a **full mesh**, each node connects directly to every other node. In a **partial mesh**, only selected nodes have direct links to multiple peers.

**Advantages**
- Multiple paths can improve resilience.
- Traffic may be rerouted around a failed link when the network and routing protocols support it.
- Useful where availability is important.

**Disadvantages**
- Full mesh can require many links and ports.
- Configuration, monitoring, and troubleshooting can become complex.
- Cost and cabling requirements can grow rapidly.

For a full mesh of \(n\) nodes, the number of unique point-to-point links is:

\[
\frac{n(n-1)}{2}
\]

For example, 5 nodes require \(5 \times 4 / 2 = 10\) links in a full mesh. This explains why full mesh becomes expensive as the number of nodes increases.

### 11.5 Tree topology

**Structure:** a hierarchy of connected devices or network segments. It is often described as a combination of star-like branches connected through a backbone or higher-level distribution structure.

```text
                 Core
               /      \
          Switch A    Switch B
          /    \       /    \
        PC1    PC2   PC3    PC4
```

**Advantages**
- Supports hierarchical organisation.
- Can scale by adding branches or access switches.
- Fits many campus and enterprise network designs.

**Disadvantages**
- Failures in higher-level devices or links can affect entire branches.
- Design and troubleshooting can be more involved than a small star.
- Redundancy may be needed to avoid major single points of failure.

### 11.6 Choosing a topology

There is no universally best topology. Selection depends on:
- Number and type of devices.
- Required reliability and redundancy.
- Budget.
- Physical layout.
- Expected traffic.
- Ease of maintenance.
- Security and segmentation needs.
- Future expansion.

Modern real-world networks often use hybrid designs rather than a single pure topology.

---

## 12. Quick Comparison Tables

### 12.1 PAN, LAN, MAN, and WAN

| Type | Full form | Approximate scope | Example |
|---|---|---|---|
| PAN | Personal Area Network | Around one person | Bluetooth earbuds and phone |
| LAN | Local Area Network | Home, office, lab, or local site | Office computers and printer |
| MAN | Metropolitan Area Network | City or metropolitan region | Sites connected across a city |
| WAN | Wide Area Network | Country, continent, or global scale | A company's offices across countries |

### 12.2 Internet vs. World Wide Web

| Aspect | Internet | World Wide Web |
|---|---|---|
| What it is | Global interconnection of networks and protocols | Interlinked Web resources and applications |
| Role | Carries many types of network traffic | A service that uses the Internet |
| Examples | Web, email, SSH, online games, messaging | Websites and browser-based web applications |
| Common technologies | IP and transport/network infrastructure | URLs, HTTP, HTML, browsers, web servers |

### 12.3 Client vs. Server

| Aspect | Client | Server |
|---|---|---|
| Main role | Initiates a request | Accepts and processes requests |
| Example | Browser or mobile app | Web server or API service |
| Can it be software? | Yes | Yes |
| Must it be a separate physical machine? | No | No |

### 12.4 Topologies at a glance

| Topology | Basic arrangement | Main strength | Main concern |
|---|---|---|---|
| Bus | Devices share a backbone | Simple shared layout | Backbone failure and shared-medium limits |
| Ring | Devices form a loop | Structured path; protection possible in some designs | Simple ring can be disrupted by a break |
| Star | Devices connect to a central switch/hub | Easy to manage and expand | Central-device failure without redundancy |
| Mesh | Nodes have multiple interconnections | Resilience and alternate paths | Cost and complexity |
| Tree | Hierarchical branches | Scalable organisation | Higher-level failures can affect branches |

---

## 13. Important Clarifications

These points help me avoid taking simplified explanations too literally while keeping the lesson's main ideas intact.

1. **The Internet's history is more nuanced than a single military problem.** Resilient communications were an important motivation in early research, but the Internet emerged through multiple research programmes, institutions, protocols, and later commercial and public networks.

2. **ARPANET's first message was “LO,” not the complete word “LOGIN.”** The intended word was LOGIN, but the system crashed after the first two characters were received.

3. **A host does not simply mean any device with an IP address in every context.** An IP address is assigned to an interface, and networking terminology distinguishes hosts, routers, switches, and other nodes.

4. **The Internet is not made only of submarine cables.** Submarine fibre is crucial for intercontinental connectivity, but traffic also uses terrestrial fibre, copper, radio, mobile networks, data centres, routers, and other links.

5. **The Internet and the Web are not the same thing.** The Web is one service that runs over the Internet. Email, SSH, and many other services also use Internet connectivity without being the Web.

6. **HTTP and HTTPS are not identical.** HTTPS is HTTP protected using TLS in standard modern deployments. TLS provides cryptographic protections for the connection.

7. **A server is defined by its role, not its size.** A small process on a laptop can be a server. Its practical capacity depends on resources, software, workload, and configuration.

8. **PAN/LAN/MAN/WAN categories are approximate.** Actual networks do not always fit perfectly into one category, and terms may be used differently depending on context.

9. **Cloud regions and availability zones should not be treated as synonyms for MAN.** They describe a cloud provider's geographic and fault-isolation architecture; the actual networking design can span several kinds of networks.

10. **Topology diagrams are simplified models.** Modern networks commonly combine star, tree, mesh, and other structures. Resilience depends on actual redundant links, devices, protocols, and configuration—not merely on the topology's name.

11. **A switch is not always the same as a hub.** The transcript informally groups central devices in a star topology. A hub repeats signals to its ports, while a switch forwards Ethernet frames more selectively using MAC-address learning.

12. **The course roadmap is a syllabus, not a guarantee that one video alone covers every practical detail.** For DevOps work, reinforce concepts with command-line exercises, packet-flow reasoning, IP/subnetting practice, DNS, ports, routing, firewall rules, and cloud networking labs as you reach those subjects.

---

## 14. My Revision Questions

I should try answering these without looking at the notes. If I cannot explain an answer in my own words, I need to revisit that concept.

### Foundation
1. What is the difference between a computer network and networking?
2. What is a host? How is a host different from a router?
3. Why is the Internet described as a network of networks?
4. Why does the Internet depend on physical infrastructure?
5. What problem were early packet-network researchers trying to address?

### Internet and Web
6. What happened during the famous first ARPANET message attempt?
7. Why was the adoption of TCP/IP important?
8. Explain the difference between the Internet and the World Wide Web.
9. What are HTML, HTTP, and a URL used for?
10. Why can a request from India to a US server travel through submarine cables?

### Client–server
11. What makes an application a client?
12. What makes a program a server?
13. Can one laptop run both a client and a server? Give an example.
14. What is a port, and why do server applications listen on ports?
15. Describe a basic browser request–response cycle.

### Network types
16. What is the difference between PAN and LAN?
17. Give an example of a MAN.
18. Why is a WAN not necessarily the public Internet?
19. Which network type would connect a company's offices across several countries?

### Topologies
20. How are devices arranged in bus, ring, star, mesh, and tree topologies?
21. Why can a central switch be a failure point in a simple star network?
22. Why can a full mesh become expensive?
23. What does a tree topology's hierarchy help achieve?
24. Why might a real network use a hybrid topology?

### Applied thinking
25. An office has six computers and one printer. What information would you gather before designing its network?
26. A user can connect to Wi-Fi but cannot open a website. Which parts of the path might need investigation?
27. Why should a DevOps engineer understand networking before troubleshooting a deployment?
28. How could you demonstrate the difference between a client and server on your own computer?

---

## 15. Glossary

- **ARPANET:** An early packet-switched research network and an important precursor to the Internet.
- **Client:** A program or system that requests a resource or service.
- **DNS:** Domain Name System; translates domain names into records such as IP addresses.
- **Host:** An end system that communicates over a network.
- **HTML:** HyperText Markup Language; structures Web content.
- **HTTP:** Hypertext Transfer Protocol; transfers Web resources through request–response communication.
- **HTTPS:** HTTP protected with TLS.
- **Internet:** A global interconnection of networks that use shared protocols.
- **IP:** Internet Protocol; provides addressing and packet forwarding between networks.
- **ISP:** Internet Service Provider; an organisation that provides Internet access or related network services.
- **LAN:** Local Area Network.
- **MAN:** Metropolitan Area Network.
- **Mesh topology:** A topology with multiple interconnections between nodes.
- **Network topology:** The arrangement of network nodes and links.
- **Node:** A device or connection point in a network.
- **PAN:** Personal Area Network.
- **Port:** A transport-layer number used to identify an application endpoint on a host.
- **Router:** A device that forwards packets between networks based on routing information.
- **Server:** A program or system that provides a service to clients.
- **Submarine cable:** A cable laid on or beneath the seabed, often using optical fibre for high-capacity communication.
- **Switch:** A device that forwards traffic within a network, commonly using MAC addresses for Ethernet.
- **TCP:** Transmission Control Protocol; provides a reliable, ordered byte stream between endpoints.
- **TCP/IP:** The Internet protocol suite, including IP and transport protocols such as TCP.
- **TLS:** Transport Layer Security; provides cryptographic protections for communication.
- **URL:** Uniform Resource Locator; identifies how and where a resource can be accessed.
- **WAN:** Wide Area Network.
- **World Wide Web:** A system of linked Web resources and applications that uses Internet connectivity.

---

## Chapter 1 — What I Learned

- Networking is foundational for DevOps, cloud, software development, testing, and cybersecurity.
- DevOps and cloud engineering overlap, but they are not the same discipline.
- The Internet is a network of networks built on shared protocols and physical infrastructure.
- ARPANET was an important precursor; its famous first message attempt delivered “LO.”
- TCP/IP gave different networks a common protocol suite for communication.
- The World Wide Web is a service that runs over the Internet; HTML, HTTP, and URLs are foundational Web technologies.
- Client–server architecture describes requesters and service providers, which can run on the same physical machine.
- PAN, LAN, MAN, and WAN classify networks by approximate scale.
- Bus, ring, star, mesh, and tree describe different ways to arrange network links and devices.
- Strong networking knowledge comes from understanding the flow of data and practising—not memorising definitions alone.

**End of my notes for this lesson.**
