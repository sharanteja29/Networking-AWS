# Networking Fundamentals

## 1. Why Networking Exists

Networking allows independent devices to communicate and share resources such as files, printers, applications, and internet access.

**Example:** In an office with six computers and one printer, networking lets all six computers use the same printer and exchange files without using USB drives.

### History of the Internet

- During the Cold War, researchers explored ways to keep communication working even if part of a network became unavailable.
- The US Department of Defense funded ARPANET, an important precursor to the modern internet.
- On October 29, 1969, an early communication attempt between UCLA and Stanford was made. The intended message was `LOGIN`, but the system failed after transmitting `LO`.
- ARPANET expanded during the 1970s and 1980s.
- On January 1, 1983, ARPANET adopted TCP/IP, an important milestone in the development of the internet.

**Key idea:** A network can be designed with alternative paths so communication may continue when a link or node fails, provided suitable routing and redundancy are available.

### Why Networking Matters in Cloud Engineering

Cloud systems rely on networking to connect:
- A laptop to a cloud server.
- A web application to its backend API.
- A backend API to a database.
- Servers and services across different locations.

A service can fail to work even when its code is correct if the network, routing, DNS, or firewall configuration is wrong.

---

## 2. Computer Network, Host, and Networking

### Computer Network

A **computer network** is a group of connected devices that can communicate and share resources.

Examples:
- A laptop and phone connected to home Wi-Fi.
- Computers connected to an office switch.
- Application servers communicating with database servers.

### Host

A **host** is a device connected to a network that can communicate using network protocols. Hosts commonly have IP addresses assigned to their network interfaces.

Examples:
- Laptop
- Smartphone
- Server
- Virtual machine

Example private IPv4 addresses:

```text
Laptop A: 192.168.1.10
Laptop B: 192.168.1.11
Printer:  192.168.1.20
```

An IP address alone does not guarantee that two devices can communicate. Routing, subnet configuration, firewall rules, and the destination service can also matter.

### Networking

**Networking** is the process of connecting devices and enabling them to exchange data or share resources.

| Term | Analogy |
|---|---|
| Computer network | The road system |
| Host | A vehicle using the roads |
| Networking | The process of travelling between destinations |

---

## 3. The Internet

The **internet is a network of networks**. Home networks, office networks, internet service provider (ISP) networks, and data-center networks connect through routers and communication links.

### Example: Opening YouTube

1. Your device connects to the local Wi-Fi router.
2. The router forwards internet-bound traffic to the ISP.
3. The ISP routes traffic through interconnected networks.
4. Traffic reaches the network hosting the requested service or a content-delivery cache.
5. Data returns to the device over a suitable route.

The exact route depends on routing, network conditions, peering arrangements, and the location of the service or cache.

### Physical Infrastructure of the Internet

The internet depends on physical infrastructure, including:
- Optical-fiber cables
- Routers and switches
- Data centers and servers
- Telecommunications equipment
- Submarine cables that cross oceans

A request from India to a server in the United States may travel through terrestrial and submarine fiber-optic cables.

### Who Owns the Internet?

No single organization owns the entire internet. Different companies and organizations operate parts of its infrastructure, including ISPs, cloud providers, telecommunications companies, and data-center operators.

### Wi-Fi vs Router vs ISP vs Internet

- **Wi-Fi:** Wireless technology used to connect devices to a local network.
- **Router:** Forwards packets between networks; home routers may combine several functions.
- **ISP:** Provides connectivity from a local network to other networks and the internet.
- **Internet:** The global system of interconnected networks.

**Example:** Your device may remain connected to Wi-Fi even when the ISP connection is down. Local devices may still communicate, while external websites may be inaccessible.

---

## 4. TCP/IP

A **protocol** is a set of rules that governs communication between devices. TCP/IP is a family of networking protocols.

### IP — Internet Protocol

IP provides logical addressing and packet forwarding toward destinations across networks.

### TCP — Transmission Control Protocol

TCP provides a reliable, ordered byte stream between communicating endpoints. It detects missing data and retransmits it when needed.

### Example: Downloading a File

When downloading a file over TCP:
1. Data is transferred between the communicating endpoints.
2. TCP helps detect missing data.
3. Missing data can be retransmitted.
4. TCP presents the received data in order to the application.

A simplified analogy:
- **IP:** Like putting destination addresses on packages.
- **TCP:** Like tracking whether the pieces of a shipment arrived and putting them in the correct order.

Not all internet communication uses TCP. UDP is also used, and HTTP/3 uses QUIC over UDP.

---

## 5. Internet vs World Wide Web (WWW)

The **internet** is the global network infrastructure. The **World Wide Web** is a system of interlinked resources accessed over networks, commonly using browsers and HTTP or HTTPS.

| Internet | World Wide Web |
|---|---|
| Global network infrastructure | A service that runs over the internet |
| Carries data for many services | Provides linked web pages and web applications |
| Supports web, email, voice calls, and more | Commonly accessed through a web browser |

### Example

When opening YouTube in a browser:
- The internet provides connectivity.
- The Web provides the web page and web application.
- HTTPS is used to exchange web requests and responses securely.

An internet-based voice call may use the internet without using the World Wide Web.

### Three Building Blocks of the Web

#### HTML — HyperText Markup Language

HTML defines the structure and content of a web page.

```html
<h1>Welcome</h1>
<p>This is my website.</p>
<a href="https://example.com">Visit</a>
```

The browser interprets the markup to display a heading, paragraph, and link.

#### HTTP — HyperText Transfer Protocol

HTTP defines how clients request web resources and how servers respond. HTTPS is HTTP protected by TLS, which provides encryption and server authentication.

#### URL — Uniform Resource Locator

A URL identifies a resource and how it can be accessed.

Example:

```text
https://example.com/products?id=25
```

- `https` — scheme
- `example.com` — hostname
- `/products` — path
- `id=25` — query parameter

Tim Berners-Lee developed the World Wide Web around 1989–1990. It became publicly accessible in 1991.

---

## 6. Client-Server Architecture

Client-server architecture divides communication into two logical roles:

- **Client:** Initiates a request for a resource or service.
- **Server:** Receives requests and provides responses.

### Basic Flow

```text
Client  ---- request ---->  Server
Client  <--- response ----  Server
```

### Example 1: Opening a Website

1. The browser acts as the client.
2. It sends a web request.
3. The server receives and processes the request.
4. The server returns a response.
5. The browser renders the result.

A response may contain HTML, JSON, images, video segments, or an error.

### Example 2: Logging In

1. A user submits a login form.
2. The browser sends the request over HTTPS.
3. The backend validates the request and checks the account.
4. The server returns an authentication result, such as a session cookie.
5. The browser displays the result.

### Can a Laptop Act as a Server?

Yes. A server is often software that listens for incoming requests and responds to them. It does not have to be a large, dedicated physical machine.

For example, a Python HTTP server can run locally on macOS:

```bash
python3 -m http.server 8000
```

Open `http://localhost:8000` in a browser.

- `localhost` refers to the same computer.
- `8000` is the port used by the server.
- Python runs the server application.
- The browser is the client.

Stop the server by pressing `Control + C` in Terminal.

This is a development example, not a production server configuration.

### What Is a Port?

A **port** identifies a communication endpoint associated with a service on a host.

Common examples:
- HTTP: port `80`
- HTTPS: port `443`
- Local example server: port `8000`

An IP address can be compared to a building address, while a port is like the particular service or entrance being contacted. One computer can run multiple network services on different ports.

### Why Might a Website Be Unavailable?

Possible causes include:
- The application is not running.
- The application is listening on another port.
- A firewall blocks traffic.
- The client uses the wrong IP address.
- The service is bound only to `localhost`.
- DNS or routing is failing.

A server being online does not guarantee that every service on it is accessible.

Server capacity depends on hardware, application complexity, database performance, concurrency, and traffic patterns.

---

## 7. Types of Networks: PAN, LAN, MAN, WAN

Networks are often categorized by the geographical area they cover.

### PAN — Personal Area Network

A **Personal Area Network** connects personal devices over a very small area, often using Bluetooth.

Examples:
- Wireless earbuds connected to a phone.
- A smartwatch synchronized with a phone.

### LAN — Local Area Network

A **Local Area Network** connects devices within a relatively small area, such as a home, office, lab, or building.

Examples:
- Computers sharing a printer in an office.
- Devices connected through a home router.

LANs are useful for local communication and resource sharing.

### MAN — Metropolitan Area Network

A **Metropolitan Area Network** connects networks across a city or metropolitan region.

Example:
- An organization connecting several campuses across one city.

### WAN — Wide Area Network

A **Wide Area Network** connects networks across large geographic distances, such as different cities, countries, or continents.

Example:
- A bank connecting offices in Hyderabad, Mumbai, London, and New York.

### Comparison

| Feature | PAN | LAN | MAN | WAN |
|---|---|---|---|---|
| Coverage | Personal space | Home, office, or building | City or metropolitan area | Large geographic area |
| Example | Bluetooth devices | Office network | City-wide network | International bank network |
| Typical scale | Very small | Small | Medium to large | Very large |
| Internet required? | Not necessarily | Not necessarily | Not necessarily | Not necessarily |

**Important:** A WAN does not automatically mean the public internet. An organization can use a private WAN to connect offices without making those connections publicly accessible.

A cloud VPC is a logically isolated virtual network. It uses concepts such as IP addressing, routing, and traffic control, but it is not simply synonymous with a LAN or MAN.

---

## 8. Network Topology

**Network topology** describes how devices and connections are arranged in a network.

Imagine setting up an office with six computers and a shared printer. Topology helps determine how those devices are connected.

### A. Bus Topology

In a bus topology, devices connect to a shared backbone cable.

```text
[T] ================================= [T]
         |       |       |
        PC1     PC2     PC3
```

`[T]` represents a terminator at the end of the cable in a traditional bus network.

**Advantages**
- Simple structure.
- Historically required relatively little cable.
- Can be inexpensive for small setups.

**Disadvantages**
- A fault in the main backbone can disrupt the network.
- Fault diagnosis can be difficult.
- The shared medium can become a performance bottleneck.

Traditional Ethernet bus networks are largely obsolete in modern office environments.

### B. Ring Topology

In a ring topology, devices form a loop.

```text
      PC1 ------ PC2
     /              \
   PC6              PC3
     \              /
      PC5 ------ PC4
```

Data moves through the ring according to the technology and protocol used.

**Advantages**
- Some designs provide orderly access to a shared medium.
- Certain ring systems support predictable traffic behavior.

**Disadvantages**
- A single link or device failure can interrupt an unprotected ring.
- Adding or removing devices may disrupt service.
- Troubleshooting can be complicated.

Some real-world ring networks use protection mechanisms to continue operating after a link failure.

### C. Star Topology

In a star topology, every device connects to a central device, usually an Ethernet switch in a modern wired LAN.

```text
             PC1
              |
 PC2 ------ [SWITCH] ------ PC3
              |
           [Printer]
              |
             PC4
```

When PC1 sends data to PC2, the switch forwards traffic to the appropriate destination port.

**Advantages**
- Easy to add or remove devices.
- Failure of one individual cable generally affects only its connected device.
- Troubleshooting is relatively straightforward.

**Disadvantages**
- The central switch can be a single point of failure.
- Each device generally requires its own link to the switch.
- The switch must have sufficient capacity for the network.

Modern switched Ethernet LANs generally use switches rather than older hubs.

### D. Mesh Topology

In a full mesh topology, every device has a direct link to every other device.

```text
       A -------- B
       |\        /|
       | \      / |
       |  \    /  |
       |  /    \  |
       | /      \ |
       D -------- C
```

The illustration represents four devices with all six pairwise connections.

A full mesh of `n` devices requires:

```text
n * (n - 1) / 2 links
```

For six devices:

```text
6 * (6 - 1) / 2 = 15 links
```

**Advantages**
- Multiple direct paths can provide resilience.
- Failure of one link need not disconnect all communication.
- Reduces dependence on a single intermediate device.

**Disadvantages**
- Expensive and complex as the number of devices grows.
- Requires more connections and maintenance.
- Adding devices may require several new links.

Partial mesh topologies are often used in larger networks.

### E. Tree Topology

Tree topology organizes devices in a hierarchy, with branches connecting to lower-level branches.

```text
             [Core]
             /    \
         [SW1]    [SW2]
          / \      / \
        PC1 PC2  PC3 PC4
```

**Advantages**
- Easy to organize a large network hierarchically.
- Supports expansion by adding branches.
- Helps separate departments or groups of devices.

**Disadvantages**
- Failure of an upper-level device or link can affect an entire branch.
- More levels can increase configuration and troubleshooting complexity.
- Critical infrastructure needs appropriate redundancy.

### Topology Comparison

| Topology | Structure | Main advantage | Main limitation |
|---|---|---|---|
| Bus | Shared backbone | Simple cabling | Backbone failure can affect all devices |
| Ring | Closed loop | Organized communication in some designs | Unprotected failures may disrupt the loop |
| Star | Central device | Easy management and expansion | Central device is a potential failure point |
| Mesh | Multiple interconnections | Redundant paths | Higher cost and complexity |
| Tree | Hierarchical branches | Scalable organization | Upper-level failures can affect branches |

### Which Topology Fits a Small Office?

For a typical small office, a **star topology using an Ethernet switch** is a sensible choice.

- Each computer has a connection to the switch.
- The printer can be shared through the LAN.
- Adding another computer is straightforward.
- A single computer's cable failure generally does not disconnect the others.

A full mesh connecting every computer directly would usually add unnecessary cost and complexity.

---

## 9. How Networking Concepts Work Together

Suppose you use your MacBook to access an application running on a cloud server.

```text
Your MacBook
     |
     v
Home router
     |
     v
ISP and internet
     |
     v
Cloud network
     |
     v
Application server
```

The concepts fit together as follows:

1. **Host:** Your MacBook and the cloud server are network-connected endpoints.
2. **LAN:** Your home devices connect through your local network.
3. **WAN and internet:** Traffic travels through networks connecting distant locations.
4. **TCP/IP:** Protocols support addressing, packet delivery, and communication.
5. **Client-server architecture:** Your browser requests a resource from the server.
6. **HTTP/HTTPS:** The browser and web server exchange web requests and responses.
7. **Topology:** The connections inside each network have a physical or logical arrangement.
8. **Cloud networking:** Virtual networks and security rules control communication between cloud resources.

These concepts form the foundation for cloud engineering, DevOps, backend development, and network troubleshooting.

---

## 10. Practical Exercises on macOS

### Exercise 1: Inspect Network Interfaces

Open Terminal and run:

```bash
ifconfig
```

This displays network interfaces and their configurations.

To list hardware ports and associated interface names:

```bash
networksetup -listallhardwareports
```

To check the local Wi-Fi IP address:

```bash
ipconfig getifaddr en0
```

This works when `en0` is the active interface; the interface name can differ.

### Exercise 2: Test Network Connectivity

Send four ICMP echo requests to a public IP address:

```bash
ping -c 4 1.1.1.1
```

Then try a hostname:

```bash
ping -c 4 example.com
```

Interpretation:
- If both work, basic IP connectivity and hostname resolution are likely working.
- If the first works but the second fails, DNS may be the issue.
- If both fail, there may be a connectivity problem, but ICMP filtering or other restrictions can also explain the results.

### Exercise 3: Run a Local Web Server

Create a directory and a sample page:

```bash
mkdir -p ~/networking-demo
cd ~/networking-demo
echo "Hello from my MacBook server" > index.html
python3 -m http.server 8000
```

Open a second Terminal window and run:

```bash
curl -i http://localhost:8000
```

You should receive an HTTP response containing your test page.

Identify the roles:
- `curl` — client.
- Python — server.
- `localhost` — the same computer.
- `8000` — the port.
- HTTP — the application-layer protocol.

Stop the server with `Control + C` when finished.

This is a development exercise, not a production server configuration.

---

## 11. Quick Revision Notes

- **ARPANET:** An early network and an important precursor to the modern internet.
- **Computer network:** Connected devices that can exchange data.
- **Host:** A network-connected endpoint.
- **Networking:** Connecting devices and enabling communication.
- **Internet:** A global network of interconnected networks.
- **TCP/IP:** A family of protocols supporting internet communication.
- **WWW:** A system of interlinked web resources accessed over networks.
- **HTML:** Defines the structure of web content.
- **HTTP/HTTPS:** Protocols for web communication; HTTPS protects HTTP with TLS.
- **URL:** Identifies a resource and how it can be accessed.
- **Client:** Initiates a request.
- **Server:** Receives requests and provides responses.
- **PAN:** Personal devices.
- **LAN:** A local area, such as a home or office.
- **MAN:** A metropolitan area.
- **WAN:** A geographically extensive network.
- **Bus:** Devices share a backbone.
- **Ring:** Devices form a loop.
- **Star:** Devices connect to a central device.
- **Mesh:** Devices or nodes have multiple interconnections.
- **Tree:** Devices are arranged hierarchically.

## 12. Suggested Interview Questions

1. What is a computer network?
2. What is the difference between a host and a network?
3. Why is the internet called a network of networks?
4. What is the difference between Wi-Fi and the internet?
5. What is TCP/IP?
6. What is the difference between TCP and IP?
7. What is the difference between the internet and the World Wide Web?
8. What are HTML, HTTP, HTTPS, and URL?
9. Explain client-server architecture with an example.
10. Can a laptop act as a server?
11. What is a port, and why is it needed?
12. Compare PAN, LAN, MAN, and WAN.
13. What is network topology?
14. Compare bus, ring, star, mesh, and tree topologies.
15. Which topology would you choose for a small office, and why?
16. Why can a website fail even when its server is online?
17. What is the role of networking in cloud computing?
18. How can you test basic connectivity from a macOS terminal?

---

## 13. Key Takeaway

Networking is about connecting devices and moving data between them. The internet connects networks globally, TCP/IP provides communication protocols, the Web provides linked web resources, client-server architecture explains request-response interactions, and network types and topologies describe the scope and arrangement of networks.

The next set of networking concepts to learn is **IP addresses, MAC addresses, packets, ports, DNS, routing, and TCP vs UDP**. These explain how data actually travels from one endpoint to another.
