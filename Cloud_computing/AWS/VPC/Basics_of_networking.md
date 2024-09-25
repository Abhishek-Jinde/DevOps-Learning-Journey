# Basics of Networking for DevOps Engineers

Networking is a critical concept for any DevOps engineer, as it forms the backbone of communication between services, users, and systems. This document dives into the foundational networking concepts necessary for managing and troubleshooting networks effectively.

---

## Table of Contents

1. [What is Networking?](#what-is-networking)
2. [Types of Networks](#types-of-networks)
3. [Network Topologies](#network-topologies)
4. [IP Addressing](#ip-addressing)
   - [IPv4](#ipv4)
   - [IPv6](#ipv6)
5. [Subnetting](#subnetting)
6. [DNS (Domain Name System)](#dns)
7. [HTTP and HTTPS](#http-and-https)
8. [TCP/IP Model](#tcpip-model)
9. [Network Devices](#network-devices)
10. [Load Balancing](#load-balancing)
11. [Firewalls](#firewalls)
12. [Virtual Private Networks (VPN)](#virtual-private-networks-vpn)
13. [Common Networking Tools](#common-networking-tools)

---

## What is Networking?

Networking refers to the practice of connecting computers, servers, and devices to share resources, data, and communication channels. In the DevOps context, networking is essential for service communication, cloud setups, and application deployments.

**Example**:  
A microservice architecture where multiple containers (like a database, API server, and frontend) need to communicate with each other relies on proper network configuration.

---

## Types of Networks

### 1. Local Area Network (LAN)

A **LAN** is a network covering a small geographical area, such as an office or building. It allows devices within the same area to communicate quickly and efficiently.

**Example**:  
An office environment where employees' computers, printers, and servers are connected on a single network.

### 2. Wide Area Network (WAN)

A **WAN** spans large geographical areas, such as cities or countries, and connects multiple LANs. The internet is the largest WAN.

**Example**:  
Connecting branch offices of a company across different cities.

### 3. Virtual Private Network (VPN)

A **VPN** creates a secure tunnel over a public network, such as the internet, allowing for private communication. VPNs are commonly used for secure remote access to company resources.

---

## Network Topologies

Network topology defines the arrangement of various elements (links, nodes, etc.) in a network.

### 1. Star Topology

In **Star Topology**, all devices connect to a central hub. This hub manages communication across the devices.


**Advantages**:
- Easy to set up and manage.
- Failure of one device doesn’t affect the rest.

### 2. Bus Topology

In **Bus Topology**, all devices are connected to a single central cable, or backbone.


**Disadvantages**:
- A failure in the backbone cable can bring down the entire network.

### 3. Mesh Topology

In **Mesh Topology**, every device connects directly to every other device. It’s used for redundancy and fault tolerance.

---

## IP Addressing

An IP address uniquely identifies a device on a network. There are two types of IP addresses: IPv4 and IPv6.

### IPv4

**IPv4** addresses are 32-bit numeric addresses written as four octets separated by periods (e.g., `192.168.1.1`).

- **Example**:  
  IPv4 Address: `192.168.0.1`  
  Subnet Mask: `255.255.255.0`

### IPv6

**IPv6** addresses are 128-bit hexadecimal numbers separated by colons (e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`). IPv6 provides a vastly larger address space than IPv4.

- **Example**:  
  IPv6 Address: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`

---

## Subnetting

Subnetting is the practice of dividing a network into smaller subnetworks (subnets). Subnets help organize networks efficiently, improving performance and security.

**Example**:  
Given the IP range `192.168.0.0/24`, subnetting it into two subnets may result in:
- Subnet 1: `192.168.0.0/25`
- Subnet 2: `192.168.0.128/25`

Subnet masks help identify the boundary between the network and the host portion of the IP address.

---

## DNS (Domain Name System)

**DNS** translates human-readable domain names (like `example.com`) into machine-readable IP addresses (like `192.168.1.1`). This process enables easier communication between users and machines on the internet.

**Example**:  
When a user types `www.google.com` into their browser, DNS resolves it to the IP address `142.250.190.78`, allowing the browser to connect to Google’s servers.

---

## HTTP and HTTPS

### HTTP (Hypertext Transfer Protocol)

**HTTP** is the standard protocol for transmitting web pages over the internet. It operates at the application layer of the TCP/IP model.

**Example**:  

A user visits a webpage with the URL `http://example.com`.

### HTTPS (HTTP Secure)

**HTTPS** is the secure version of HTTP. It encrypts communication between the client and server using SSL/TLS protocols.

**Example**:  
When a user visits `https://example.com`, the communication is secured, making it safe from eavesdropping or man-in-the-middle attacks.

---

## TCP/IP Model

The **TCP/IP Model** is a set of protocols that govern communication over the internet. It consists of four layers:

1. **Network Interface Layer**: Manages hardware-level protocols for connecting devices.
2. **Internet Layer**: Routes data between devices using IP addresses.
3. **Transport Layer**: Ensures reliable transmission of data between devices. The main protocols are TCP and UDP.
4. **Application Layer**: Provides communication services such as HTTP, FTP, and DNS.


---

## Network Devices

### 1. **Router**

A **router** forwards data packets between networks, determining the best path for data to reach its destination.

### 2. **Switch**

A **switch** connects devices within the same network and forwards data based on MAC addresses, operating at the data link layer.

### 3. **Firewall**

A **firewall** filters incoming and outgoing traffic based on predefined security rules. It acts as a barrier between trusted and untrusted networks.

---

## Load Balancing

**Load balancing** is the process of distributing incoming network traffic across multiple servers to ensure that no single server is overwhelmed. It improves fault tolerance and ensures high availability.

### Example:

A website using a load balancer distributes user requests to multiple backend servers.


---

## Firewalls

A **firewall** monitors and controls incoming and outgoing network traffic. Firewalls are essential for securing a network by blocking or permitting traffic based on rules.

**Example**:  
Blocking all incoming traffic on port `22` (SSH) except from specific IP addresses.

---

## Virtual Private Networks (VPN)

A **VPN** allows secure communication over an untrusted network (like the internet) by encrypting the connection. VPNs are commonly used by remote workers to securely access company resources.

**Example**:  
A DevOps engineer can use a VPN to securely connect to internal cloud resources while working from a remote location.

---

## Common Networking Tools

### 1. **Ping**

`Ping` tests the connectivity between two devices on a network.

```bash
ping google.com

### 2. Traceroute

`Traceroute` shows the path that data takes to reach a destination, identifying each hop along the way.

```bash
traceroute google.com

### Nslookup

`Nslookup` queries DNS records to find the IP address associated with a domain.

```bash
nslookup google.com



