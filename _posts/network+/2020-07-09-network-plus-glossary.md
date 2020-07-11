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

**Disclaimer**: These are notes I'm taking as I go through the material and I tend to summarize, paraphrase and add my own insights. Although I try to be as accurate as possible, there may be things I've misunderstood. Additionally, since I'm not writing a paper here, I may quote definitions I've found on various sites. If you see any mistakes and would like to fix them, please create a PR [here](https://github.com/thomashzhang/thomaszhang.com). Also note that this may not be a complete list of terms.

- **5 9's of Availability** - Uptime of 99.999% of the time. This means in a year only 5 minutes of downtime are expected (525600 - (525600 * 0.99999)).
- **Ad Hoc** - Peer to peer connection (no centralized router/server).
- **ANT+** - "Collection and transfer of sensory data."
- **AP or WAP (Access Point)** - "In computer networking, a wireless access point, or more generally just access point, is a networking hardware device that allows other Wi-Fi devices to connect to a wired network."
- **Bus Topology** - A single cable running through each computer to connect each device to the network. We don't use this today (generally). Any device talking will collide with other devices.
- **CAN (Campus Area Network)** - This can cover several kilometers and can include multiple builds. Think college campuses. 
- **Client** - A device used by the end user to access the network.
- **Client/Server Model** - Dedicated server will serve resources to the client. This makes administration a lot easier as it is centralized but usually costs more money. This is used in business a lot today.
- **Full-Mesh Topology** - Every node connects to every other node, very redundant, but there's a lot of connections.
- **Hub** - Connects network devices by taking in data and sending that data to all connected devices. This is not used for the most part today as switches are used more often.
- **Hub-and-Spoke Topology** - Like Star, but the end devices can also connect to different hubs. Think Star Topology, but the end devices can connect to more that one central device.
- **ICMP (Internet Control Message Protocol)** - Think about the `ping` command. "The Internet Control Message Protocol is an internet layer protocol used by network devices to diagnose network communication issues. ICMP is mainly used to determine whether or not data is reaching its intended destination in a timely manner. Commonly, the ICMP protocol is used on network devices, such as routers."
- **IEEE 802.11** - WiFi (a, b, g, n, ac)
- **IEEE 802.3** - Ethernet
- **IR (Infrared)** - Line of sight communication with the infrared frequency. Think remote controls.
- **LAN (Local Area Network)** - A type of network that is generally a around a few hundred meters. Think business - all those office devices are connected through a LAN.
- MAC (Media Access Control) - Physical addressing system where each Network Interface Card has a hardcoded 48-bit address.
- **MAN (Metropolitan Area Network)** - Think up to 25 miles. An example would be the police department in a city or a bunch of college campuses.
- **NFC (Near Field Communication)** - Shorter distance than RFID. Communication of two electronic devices within 4-cm range.
- **PAN (Personal Area Network)** - A type of network generally in a much smaller range (usually < 10 meters between connections). As an example, a bluetooth watch connected to your phone is considered a personal area network. USB connections are usually also considered a PAN.
- **Peer-to-Peer Model** - Think torrents or Bitcoin. Each device connects to peer devices to share files and connect. The benefit is redundancy and lower costs as there's no server involved. 
- **Ring Topology** - Cable runs in a circular loop and each device is connect on the ring. Only when a token ring is obtained by the device, then the device can talk on the network. Also not used that often today.
- **RFID (Radio Frequency ID)** - Electromagnetic to read data from a chip.
- **RTP (Real-time Transport Protocol)** - Layer 5. "The Real-time Transport Protocol is a network protocol for delivering audio and video over IP networks. RTP is used in communication and entertainment systems that involve streaming media, such as telephony, video teleconference applications including WebRTC, television services and web-based push-to-talk features."
- **Server** - A device that clients can connect to and provide network functionality.
- **Star Topology** Devices are connected directly to a central device (think of a star pattern). Downside is if the central device goes down, the entire network goes down.
- **Switch** - Like a hub, but forwards traffic only to the devices that are requested (and not a general broadcast).
- **TCP (Transmission Control Protocol)** - Layer 4 protocol. Allows for reordering and ensure data is sent and not lost. Used for transmitting files and important data.
- **TDM (Time-Division Multiplexing)** - For base-band models, all users use a share of the time to communicate on the network. StatTDM (Statistical Time-Division Multiplexing) is a variant of TDM that dynamically allocates time slots. FDM (Frequency-Division Multiplexing) allows each client on a base-band model transmit over a specific frequency (like Broadband).
- **UDP (User Datagram Protocol)** - Layer 4 protocol. Transports segments in a unreliable way. This is useful for things like Skype where not every single data packet is important.
- **WAN (Wide Area Network)** - A type of network that physically connects two geographically separated network locations (ex. Los Angeles and San Francisco) and are connected through a tunnel. Two business in two different states can be connected through a WAN.
- **Z-Wave** - Short range low-latency data transfer technology.