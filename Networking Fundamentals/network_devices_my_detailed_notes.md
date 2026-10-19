# Network Devices — My Detailed Notes

## 1. The Big Picture

I can think about my home Wi-Fi network. My phone, laptop, smart TV, and other devices connect to a network so they can communicate with each other and access the Internet.

Different network devices have different responsibilities. A network is not one device doing everything; it is a collection of devices and services working together.

A simplified network looks like this:

```text
                    Internet
                       |
                     Router
                       |
                     Switch
                  /     |      \
                PC 1   PC 2   Printer
```

Wireless devices can connect through a Wi-Fi access point. In many homes, several of these functions are combined into one physical box.

---

## 2. What Is a Switch?

**A switch connects devices within a local area network (LAN).**

For example, an office might have 10 computers and one network printer. Instead of connecting every computer directly to every other computer, the devices can connect to a switch using Ethernet cables.

### How a switch works

Suppose PC 1 wants to send data to PC 2:

1. PC 1 sends an Ethernet frame to the switch.
2. The switch checks the destination **MAC address** in the frame.
3. It consults its MAC address table to determine which port leads to PC 2.
4. It forwards the frame through the appropriate port.

The switch learns which MAC addresses are reachable through which ports by examining incoming frames.

A normal Ethernet switch generally forwards known unicast traffic only toward the appropriate port, rather than sending every frame to every connected device.

**Remember:**
- A switch primarily uses MAC addresses to forward Ethernet frames within a LAN.
- A router uses IP addresses and routing information to forward packets between networks.

---

## 3. What Is a Router?

**A router connects different IP networks.**

For example, a home router connects a home network to the ISP's network so that devices can access the Internet.

### How a router works

Imagine a laptop with IP address `192.168.1.10` wants to access a server on the Internet:

1. The laptop creates a packet addressed to the destination server.
2. It sends the packet to its default gateway, usually the home router.
3. The router examines the destination IP address.
4. It consults its routing table to determine where to forward the packet.
5. The packet moves toward the destination through other routers and networks.

At home, the router commonly performs **NAT (Network Address Translation)**, allowing several devices with private IP addresses to share one public IPv4 address.

For Internet access, the router commonly acts as the default gateway for devices on the home network.

**Remember:** A switch connects devices within a LAN; a router connects networks.

---

## 4. What Is a Modem or ONT?

**A modem or ONT connects your premises to the ISP's access network.** The exact device depends on the Internet connection technology.

- **Modem:** Converts or terminates signals for a particular access technology, such as cable Internet.
- **ONT (Optical Network Terminal):** Terminates the fibre connection used by a fibre-to-the-home service.

For example, with fibre broadband, the fibre cable from the ISP may connect to an ONT, which then connects to the router.

A common setup is:

```text
ISP fibre → ONT → Router → Your devices
```

Some providers combine the ONT or modem, router, Wi-Fi access point, and switch into one box. That is why a home may have only one device.

---

## 5. What Is a Wi-Fi Access Point?

**An access point (AP) lets wireless devices join a network.**

Imagine an office has a wired LAN, but employees also want to use laptops and phones wirelessly. The access point connects to the wired network and provides Wi-Fi connectivity.

A typical flow is:

```text
Phone → Wi-Fi access point → Switch → Router → Internet
```

A wireless access point is not inherently the same thing as a router. Many home Wi-Fi routers combine both functions in one device.

---

## 6. What Is a Hub?

**A hub sends incoming signals to all its other ports.**

If PC 1 sends data through a traditional Ethernet hub, the hub repeats the signal to the other connected ports, so multiple devices may receive it.

A traditional Ethernet hub:
- Operates at the physical layer (Layer 1).
- Does not learn MAC addresses to make forwarding decisions.
- Shares bandwidth among devices connected to the hub.

A switch is generally preferred today because it forwards Ethernet frames more selectively and supports more efficient communication.

---

## 7. What Is a Firewall?

**A firewall controls network traffic according to security rules.**

It can allow or block traffic based on factors such as:
- IP addresses.
- Ports.
- Protocols.
- Connection state.
- Application rules.

Imagine a company runs a website:
- Visitors should be able to access the website using HTTPS on port `443`.
- Random users should not be allowed to access the server's SSH port `22`.
- Administrators may be allowed to connect over SSH from an approved network.

A firewall enforces rules that help control these connections.

Firewalls can be implemented in hardware, software, cloud services, or a combination of these.

**DevOps example:** If an application is running correctly but users cannot connect, a firewall rule might be blocking the required traffic.

---

## 8. What Is a Repeater?

**A repeater regenerates or repeats a signal to extend its reach.**

It helps a signal travel farther when it would otherwise become too weak or degraded.

For example, a Wi-Fi range extender can receive a wireless signal and retransmit it to improve coverage in another area.

A repeater does not perform the same job as a router. Repeating a signal is different from deciding where IP packets should go.

---

## 9. What Is a Bridge?

**A bridge connects or segments LAN sections at the data-link layer (Layer 2).**

A bridge can learn MAC addresses and forward Ethernet frames between network segments.

For example, two sections of a small network can be connected through a bridge so devices on the sections can communicate.

A modern Ethernet switch is essentially a multiport bridge. In practice, you will usually work with switches rather than separate traditional bridges.

---

## 10. What Is a NIC?

**NIC stands for Network Interface Card or Network Interface Controller.**

It provides a device with a network interface, such as a wired Ethernet connection or a wireless interface.

A laptop may have:
- A Wi-Fi NIC for wireless communication.
- An Ethernet NIC for wired communication.
- Virtual network interfaces created by software.

The NIC handles link-level communication and interacts with the operating system's networking stack.

A MAC address is associated with a network interface, although addresses can sometimes be changed or virtualised.

---

## 11. What Are DNS and DHCP Servers?

DNS and DHCP are services, not necessarily separate physical machines. They often run on routers, dedicated servers, or cloud infrastructure.

### DNS server — Domain Name System

DNS translates domain names into records, such as IP addresses.

For example, when I visit `example.com`, DNS helps my device find the IP address associated with that name.

### DHCP server — Dynamic Host Configuration Protocol

DHCP automatically provides devices with network configuration, commonly including:
- An IP address.
- A subnet mask.
- A default gateway.
- DNS server addresses.

For example, when my phone joins my home Wi-Fi, DHCP can assign it an address such as `192.168.1.25`.

**Easy way to remember:**
- **DHCP:** helps my device configure its network settings.
- **DNS:** helps my device find the address associated with a domain name.

My home router often provides DHCP and DNS-related functionality, even if it forwards DNS queries to another server.

---

## 12. What Is a Load Balancer?

**A load balancer distributes incoming requests or connections across multiple servers.**

Imagine a company runs a website with three application servers. Instead of sending every request to just one server, the load balancer distributes requests among them according to its configuration and health checks.

```text
               Users
                  |
            Load Balancer
            /     |     \
         Server Server Server
            1      2      3
```

Benefits include:
- Distributing workloads.
- Improving availability when healthy alternatives are configured.
- Supporting application scaling.
- Helping prevent one server from becoming overloaded.

A load balancer is especially useful in cloud and DevOps environments.

---

## 13. What Is a Proxy Server?

**A proxy is an intermediary that handles requests on behalf of a client or server.**

Two common types are:

### Forward proxy

Acts on behalf of clients when they access other services. Organisations may use one to control or monitor outbound access.

### Reverse proxy

Sits in front of application servers and receives requests before forwarding them to the appropriate backend.

Example:

```text
User → Reverse Proxy → Application Server
```

A reverse proxy can provide TLS termination, routing, caching, or other functions.

A load balancer and a reverse proxy can overlap in functionality, but they are not exactly the same thing.

---

## 14. Quick Comparison of Network Devices

| Device | Main responsibility | Common layer or role |
|---|---|---|
| Switch | Connects devices within a LAN | Layer 2 |
| Router | Forwards packets between IP networks | Layer 3 |
| Modem | Interfaces with a particular access technology | Depends on technology |
| ONT | Terminates a fibre access connection | Access-network device |
| Access point | Connects Wi-Fi devices to a network | Wireless LAN |
| Hub | Repeats signals to other ports | Layer 1 |
| Bridge | Connects LAN segments and forwards frames | Layer 2 |
| Firewall | Allows or blocks traffic using rules | Multiple layers, depending on type |
| Repeater | Regenerates or repeats signals | Usually Layer 1 |
| NIC | Provides a network interface | Hardware/interface |
| DNS server | Resolves domain names and other DNS records | Application service |
| DHCP server | Assigns network configuration | Application service |
| Load balancer | Distributes requests or connections | Layer 4 or 7 implementations |
| Proxy | Intermediates client/server communication | Depends on proxy type |

The OSI layer labels are useful learning aids, but real devices and services can operate across multiple layers.

---

## 15. How These Devices Work Together

A simplified home network might look like this:

```text
                 Internet / ISP
                        |
                  Modem or ONT
                        |
                  Router + Firewall
                        |
                 +------+------+
                 |             |
               Switch      Access Point
                 |             |
            Wired devices  Wireless devices
                              /    |    \
                          Laptop  Phone  Smart TV
```

This diagram is simplified. A home router may already contain the modem or ONT, switch ports, Wi-Fi access point, firewall, DHCP service, and DNS forwarding functionality.

### Example: Opening a website

When I open a website on my phone:

1. My phone connects to the network through Wi-Fi.
2. DHCP may have already provided my phone with its IP address, gateway, and DNS settings.
3. DNS helps resolve the website's domain name into an IP address.
4. My phone sends traffic through the access point and router.
5. The router forwards packets toward the ISP and the destination network.
6. Firewalls along the path may allow or block the traffic according to their rules.
7. The destination server processes the request and sends a response.

The exact path and devices vary depending on the network.

---

## 16. Test My Understanding

### Question

My laptop connects to Wi-Fi, but it cannot access a website by its domain name. Which service translates the domain name into an IP address?

- A. Switch
- B. Router
- C. DNS server
- D. NIC

**Correct answer: C — DNS server.**

DNS resolves domain names into records such as IP addresses. If the website still fails after DNS resolution, the cause could instead be routing, a firewall, TLS, or the server itself.

---

## 17. Key Takeaways

- **Switch:** connects devices within a LAN and forwards Ethernet frames using MAC addresses.
- **Router:** forwards IP packets between networks.
- **Modem/ONT:** connects premises to the ISP's access technology.
- **Access point:** allows wireless devices to join a network.
- **Hub:** repeats signals to all other ports; mostly obsolete in modern Ethernet networks.
- **Firewall:** controls which network traffic is allowed.
- **Repeater:** extends signal reach by repeating or regenerating signals.
- **Bridge:** connects LAN segments; a switch is essentially a multiport bridge.
- **NIC:** provides a device's network interface.
- **DNS:** resolves domain names.
- **DHCP:** automatically provides network configuration.
- **Load balancer:** distributes requests across servers.
- **Proxy:** acts as an intermediary for clients or servers.

The most important distinction to remember is:

> **A switch moves frames within a LAN, a router forwards packets between networks, and a firewall controls which traffic is permitted.**

Once I understand these roles, learning IP addresses, ports, routing tables, and cloud networking becomes much easier.
