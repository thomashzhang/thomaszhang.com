---
layout: post
current: post
cover: assets/images/network+/network_plus.jpg
navigation: True
title: Network+ Full Glossary of Terms
date: 2020-07-09 10:30:00
tags: network+ comptia
class: post-template
subclass: 'post'
author: thomas
---

As I go through course material, study sessions, exploratory sessions, I will list all of the terms that have come up in a master alphabetized glossary list.

**Disclaimer**: These are notes I'm taking as I go through the material and I tend to summarize, paraphrase and add my own insights. Although I try to be as accurate as possible, there may be things I've misunderstood. Additionally, since I'm not writing a paper here, I may quote definitions I've found on various sites. I do want to mention that I used this [Udemy course](https://www.udemy.com/course/networkplus/learn/lecture/9596690) for some of the definitions. If you see any mistakes and would like to fix them, please create a PR [here](https://github.com/thomashzhang/thomaszhang.com).

- **5 9's of Availability** - Uptime of 99.999% of the time. This means in a year only 5 minutes of downtime are expected (525600 - (525600 * 0.99999)).
- **Ad Hoc** - Peer to peer connection (no centralized router/server).
- **ANT+** - "Collection and transfer of sensory data."
- **AP or WAP (Access Point)** - "In computer networking, a wireless access point, or more generally just access point, is a networking hardware device that allows other Wi-Fi devices to connect to a wired network."
- **APC (Angled Physical Contact [Connector])** - The connector type is slightly offset at an angle. The prevents reflection of the signal back into the original source because light hitting the end of the connector gets reflected at a non parallel angle. SC connectors tend to use APC more.
- **APIPI (Automatic Private IP Address)** - The range 169.254.0.0/16 is automatically assigned to a device when an IP address cannot be obtained from the DHCP server. This is actually a useful feature where without a router, you can create an internal adhoc network using those IP ranges. Though you can't route outside of the internal network.
- **BGP (Border Gateway Protocol)** - An EGP protocol that uses path vector and autonomous system hops (instead of router hops). Backbone of the internet. Doesn't converge very quickly.
- **BNC Connector (Bayonet Neill-Concelman Connector)** - A type of connector for coax cables that's a twist to tighten. See more info on [Wikipedia](https://en.wikipedia.org/wiki/BNC_connector).
- **BPL (Broadband over Power Lines)** - Not very popular, but more popular in rural areas. This allows broadband internet to be delivery through regular power lines (a little like powerline technology for houses). 2.7 Mbs per second.
- **BSS (Basic Service Set)** - One AP on the network (in contrast to IBSS).
- **Bus Topology** - A single cable running through each computer to connect each device to the network. We don't use this today (generally). Any device talking will collide with other devices.
- **CAN (Campus Area Network)** - This can cover several kilometers and can include multiple builds. Think college campuses. 
- **CARP (Common Address Redundancy Protocol)** - Open standard of the HSRP.
- **Client** - A device used by the end user to access the network.
- **Client/Server Model** - Dedicated server will serve resources to the client. This makes administration a lot easier as it is centralized but usually costs more money. This is used in business a lot today.
- **CSMA/CA (Carrier Sense Multiple Access/Collision Avoidance)** - WLAN uses this instead of CSMA/CD. It'll check if it's safe to transmit first to avoid collisions ahead of time. Back off until CTS (clear to send).
- **CSMA/CD (Carrier Sense Multiple Access / Collision Detect)** - When a collision happens on a contention based network, then there's an algorithm to determine who actually gets to speak (ex, back-off and then wait a little bit of time).
- **DB9/DB25** - A termination for serial cables. Used for external modems for asynchronous communications.
- **F Connector** - A type of connector for coax cables that's a simple push to connect. Think cable TV which this connector is often used.
- **DCE (Data Communications Equipment)** - Switches and modems, they are the "providers" of network interface.
- **DMVPN (Dynamic Multipoint Virtual Private Network)** - Allows internet to be used as WAN between two different sites (no dedicated point VPN like T1). Low cost without dedicated/lease line access.
- **DSSS (Direct-Sequence Spread Spectrum)** - Type of frequency that uses the entire spectrum.
- **DTE (Data Terminating Equipment)** - Examples are desktops and laptops, they are the "end-user" of the network interface.
- **EAP (Extensible Authentication Protocol)** - This is used under the hood for 802.11x.
- **EIGRP (Enhanced Interior Gateway Routing Protocol)** - An IGP protocol which is advanced. Uses bandwidth and delay (so hybrid of distance-vector and link state). Proprietary Cisco protocol. Not as widely used as OSPF.
- **EGP (Exterior Gateway Protocols)** - A type of routing protocol category where it operates between autonomous systems. Contrast this to IPG.
- **ESS (Extended Service Set)** - Multiple APs that provide wireless coverage. Good coverage with multiple access points.
- **FHSS (Frequency-Hopping Spread Spectrum)** - Hop between frequencies for better security.
- **Full-Mesh Topology** - Every node connects to every other node, very redundant, but there's a lot of connections. See more info on [Wikipedia](https://en.wikipedia.org/wiki/F_connector).
- **GLBP (Gateway Load Balancing Protocol)** - Like HSRP where it's proprietary by Cisco, but actually focuses on load balancing (uses both routers) instead of an active/standby pair.
- **HSRP (Hot Standby Router Protocol)** - Redundancy protocol by Cisco where one router is on standby while another has all the traffic routed to it (and it'll switch one the active router is broken). There's a "virtual" router that can route to either router.
- **Hub** - Connects network devices by taking in data and sending that data to all connected devices. This is not used for the most part today as switches are used more often.
- **Hub-and-Spoke Topology** - Like Star, but the end devices can also connect to different hubs. Think Star Topology, but the end devices can connect to more that one central device.
- **IBSS (Independent Basic Service Set)** - A network that contains devices in Ad-hoc mode without access to internet.
- **ICMP (Internet Control Message Protocol)** - Think about the `ping` command. "The Internet Control Message Protocol is an internet layer protocol used by network devices to diagnose network communication issues. ICMP is mainly used to determine whether or not data is reaching its intended destination in a timely manner. Commonly, the ICMP protocol is used on network devices, such as routers."
- **IEEE 802.11** - WiFi (a, b, g, n, ac). STandard for wireless network.
- **IEEE 802.1d** - STP (Spanning Tree Protocol)
- **IEEE 802.1q** - VLAN Trunking (each VLAN is a trunk)
- **IEEE 802.1x** - User Authentication. "A standard on switches to require users to authenticate themselves before gaining access to the network."
- **IEEE 802.3** - Ethernet
- **IEEE 802.3ad** - Link Aggregation. Turns multiple physical connections into a single logical connection.
- **IEEE 802.3af** - PoE (Power over Ethernet) which supplies power over Ethernet cables (CAT 5 cables or higher). 15.4 Watts 15.4 watts of power max.
- **IEEE 802.3at** - PoE+ (Power over Ethernet Plus) which supplies power over Ethernet cables (CAT 5 cables or higher). 25.5 watts of power max.
- **IGMP (Internet Group Management Protocol)** - Allows clients to join a multicast group. A protocol to let routers know which clients can join the group.
- **IGP (Interior Gateway Protocol)** - Type of routing protocol (layer 3) category that operate within an autonomous system.
- **Infiniband** - High performance/throughput and low latency. Extremely expensive.
- **IR (Infrared)** - Line of sight communication with the infrared frequency. Think remote controls.
- **ISDN (Integrated Services Digital Network)** - Older tech. 64-kbps signaling data, we'll probably not come across this in real life that often or at all today.
- **IS-IS (Intermediate System to Intermediate System)** - IGP routing protocol that uses costs. Like OSPF, but not as popular. Costs is based on link speed.
- **LACP (Link Aggregation Control Protocol)** - Multiple links between devices (achieves redundancy between switches).
- **LAN (Local Area Network)** - A type of network that is generally a around a few hundred meters. Think business - all those office devices are connected through a LAN.
- **MAC (Media Access Control)** - Physical addressing system where each Network Interface Card has a hardcoded 48-bit address.
- **LC (Lucent Connector)** - A type of optical connector where there's kind of two SC connectors combined together. Think *love connector* because there's two connectors connected together.
- **MAN (Metropolitan Area Network)** - Think up to 25 miles. An example would be the police department in a city or a bunch of college campuses.
- **Media Converter** - A layer 1 device which converts different physical mediums into others. As an example, a converter that converts light signals to copper signals, or technically copper signals to wireless signals.
- **MDIX** - "Automated way to electronically simulate a crossover connector."
- **MMF (Multimode Fiber)** - This is an optical cable type generally for distances shorter than 1 km. It's got a bigger core which allows for multiple signals to transfer through it. "Multi-mode optical fiber is a type of optical fiber mostly used for communication over short distances, such as within a building or on a campus. Multi-mode links can be used for data rates up to 100 Gbit/s."
- **MPLS (Multiprotocol Label Switching)** - Multiple protocol support on the same network. This is what a service provider would use (maybe both Frame Relay and ATM on the same MPLS backbone). More efficient than layer 3 tech.
- **MTBF (Mean Time Between Failures)** - Average time between failures of a device. Time to Failure + Time to Repair = MTBF.
- **MTRJ (Mechanical Transfer-Registered Jack)** - A type of optical connector, smaller than the LC connector type.
- **MTTR (Mean Time to Repair)** - Time it takes to repair a device or network after breakage.
- **NAC (Network Access Control)** - Checks the device on the network (like OS, make sure it's up to date) before allowing the device on the network.
- **NAS (Network Attached Storage)** - Disk storage that goes over TCP/IP.
- **NAT (Network Address Translate)** - Translate private IP to public IP addresses.
- **NDP (Neighbor Discovery Protocol)**- Assigns own IP address on an IPv6 network by discovering the IP of other devices on the network.
- **NFC (Near Field Communication)** - Shorter distance than RFID. Communication of two electronic devices within 4-cm range.
- **OFDM (Orthogonal Frequency Division Multiplexing)** - Type of frequency algorithm that uses modulate that can transmit over 52 data streams. Best for high data rates and better to resist interference among other channels.
- **OSPF (Open Shortest Path First)** - Type of IGP routing protocol. A link state protocol that uses costs. More efficient and much more popular today. Cost is based on link speed (faster network speed) and NOT hop count (number of routers) like RIP.
- **PAN (Personal Area Network)** - A type of network generally in a much smaller range (usually < 10 meters between connections). As an example, a bluetooth watch connected to your phone is considered a personal area network. USB connections are usually also considered a PAN.
- **PAP (Password Authentication Protocol)** - One-way authentication between client and server. Credentials are sent in cleartext (not good security). Compare this to CHAP (Challenge Authentication Protocol) where there's a three way protocol and no password in plaintext (similar to MS-CHAP, but that has 2 way authentication).
- **PAT (Port Address Translation)** - Multiple private IP addresses share one public IP. The router uses a port to determine which device should have the traffic routed from the public IP.
- **PD - Powered Device** - Specifically refers to devices that can operate through the PoE standard.
- **PDU - Protocol Data Unit** - The data unit for each OSI layer. Layer 4 and higher = segment, layer 3 = packet, layer 2 = frame, layer 1 = bit.
- **Peer-to-Peer Model** - Think torrents or Bitcoin. Each device connects to peer devices to share files and connect. The benefit is redundancy and lower costs as there's no server involved.
- **PIM (Protocol Independent Multicast)** - Multicast traffic. Focused on routers. In dense mode (PIM-DM) starts with flooding and then picks the optimal route. In sparse mode (PIM-SM), will try any hop (not optimal, but pretty good as there's no flooding - takes a little longer to find the optimal route).
- **POTS (Plain Old Telephone Service)** - Actual analog service for telephones (instead of digit VOIP).
- **PPP (Point-to-Point Protocol)** - Layer 2 protocol that is used on top of dedicated lease lines (DSL, T1, E1, T3, etc.). Other protocols can be used on top of this such as IP. Each layer 3 control protocol runs an instance of PPP's LCP (Link Control Protocol).
- **PSE - Power Sourcing Equipment** - The equipment that provides power over ethernet
- **Ring Topology** - Cable runs in a circular loop and each device is connect on the ring. Only when a token ring is obtained by the device, then the device can talk on the network. Also not used that often today.
- **RIP (Routing Information Protocol)** - IGP type protocol. This is a distance vector protocol which uses hop count to find the fastest path. Max hops is 15. Oldest dynamic protocol. Harder to maintain convergence. Uses UDP as protocol. 
- **RFI (Radio Frequency Interference)** - Overlapping channels ex. multiple networks on 2.4 GHz on the same channel.
- **RFID (Radio Frequency ID)** - Electromagnetic to read data from a chip.
- **RG-6** - Copper coax cable specification. This is a lot thicker insulation that provides better shielding. And actually has a thicker copper core as well for better signal transfer. All of this is compared to RG-59.
- **RG-59** - Copper coax cable specification. Like RG-6, but thinner in all areas. Less shielding, thinner core, etc.
- **RJ-11 (Registered Jack)** - Phone system connector with 6 pins. Only 2 pins need to be used for phones.
- **RJ-45 (Registered Jack)** - Ethernet connector with 8 pins. Ethernet itself actually only uses 4 pins, and the other 4 are reserved for "future" usage which may include PoE (power over ethernet).
- **RTP (Real-time Transport Protocol)** - Layer 5. "The Real-time Transport Protocol is a network protocol for delivering audio and video over IP networks. RTP is used in communication and entertainment systems that involve streaming media, such as telephony, video teleconference applications including WebRTC, television services and web-based push-to-talk features."
- **SAN (Storage Area Network)** - Like NAS, but doesn't use TCP/IP and is much faster.
- **SC (Subscriber Connector)** - A connector for optical fiber cables. It looks like you have to *snap* and *click* the connector in place, so you can think "snap click" for SC connectors. See more in [Wikipedia](https://en.wikipedia.org/wiki/Optical_fiber_connector).
- **SDN (Software Defined Networking)** - Easy frontend to configure virtual and physical devices on your network (or in some cases code to configure virtual networks).
- **Server** - A device that clients can connect to and provide network functionality.
- **SMF (Single-Mode Fiber)** - A type of optical cable that is used for much longer distances than MMF, but with a much smaller core size.
- **SFP (Small Form-Factor Pluggable [Transceiver])** - "Hot-pluggable network interface module used for both telecommunication and data communications applications." This is in contrast to GBIC, another much larger transceiver. There also exists the QSFP (Quad SFP) where it's only slightly bigger than the SFP, but allows for up to 4x the speed.
- **SONET (Synchronous Optical Network)** - Layer 1 tech that uses fiber as media. 155Mbps to 10Gbps or more. Uses ATM (asynchronous transfer mode).
- **SPB (Shorted Path Bridging)** - Alternative to STP, generally for larger network environments.
- **Star Topology** Devices are connected directly to a central device (think of a star pattern). Downside is if the central device goes down, the entire network goes down.
- **ST Connector** - A type of optical fiber connector. You'll have to *snap* and *twist* so you can think that ST stands for that.
- **STP (Shielded Twisted Pair)** - A type of copper twisted pair cable where each pair of inner wires (8 in total) are twisted in pairs of two. There is additional metal shielding that covers the cables to prevent EMI. More expensive that UTP cables.
- **STP (Spanning Tree Protocol)** - Prevent looping of network traffic and allow for redundancy.
- **Switch** - Like a hub, but forwards traffic only to the devices that are requested (and not a general broadcast).
- **T568A** - This is a type of termination. When a cable has T568A on one end and T568B on the other end, it's known as a crossover cable. This needs to be used to connect devices that are DTE to DTE and DCE to DCE. BUT, because of modern advances, many devices will support MDIX and a straight-through cable will also work.
- **T568B** - This is a type of termination. Straight-through cable or a patch cable will use this termination on both ends. Take a look at which colors to use under the [wiring section in Wikipedia](https://en.wikipedia.org/wiki/TIA/EIA-568). Use this cable on a DTE to a DCE or vice versa device. Though a lot of modern switches and networking equipment will also accept this type of cabling even from a DTE to DTE or DCE to DCE because of MDIX, which is "an automated way to electronically simulate a crossover connector."
- **TCP (Transmission Control Protocol)** - Layer 4 protocol. Allows for reordering and ensure data is sent and not lost. Used for transmitting files and important data.
- **TDM (Time-Division Multiplexing)** - For base-band models, all users use a share of the time to communicate on the network. StatTDM (Statistical Time-Division Multiplexing) is a variant of TDM that dynamically allocates time slots. FDM (Frequency-Division Multiplexing) allows each client on a base-band model transmit over a specific frequency (like Broadband).
- **UDP (User Datagram Protocol)** - Layer 4 protocol. Transports segments in a unreliable way. This is useful for things like Skype where not every single data packet is important.
- **UPC (Ultra Physical Contact [Connector])** - A connector type where the ends are flat (perpendicular to the signal). This can cause more of the optical signal to be reflected back into the source. This is used more with MTRJ connectors.
- **UTP (Unshielded Twisted Pair)** - A type of copper twisted pair cable where each pair of inner wires (8 in total) are twisted in pairs of two, BUT don't have any shielding around the cable.
- **VLAN (Virtual LAN [Local Area Network])** - Same hardware can be split up into multiple logical networks and can have logical separation of network traffic (different broadcast domain).
- **VLSM (Variable Length Subnet Mask)** - Subnets of unequal number of IP addresses can be used. It's like a subnetting of subnets.
- **VRRP (Virtual Router Redundancy Protocol)** - Another open standard variant of HSRP.
- **WAN (Wide Area Network)** - A type of network that physically connects two geographically separated network locations (ex. Los Angeles and San Francisco) and are connected through a tunnel. Two business in two different states can be connected through a WAN.
- **WAP** - Wireless access point. Like a hub/media converter to translate ethernet to wireless.
- **WLAN (Wireless LAN)** - Wireless network.
- **Z-Wave** - Short range low-latency data transfer technology.