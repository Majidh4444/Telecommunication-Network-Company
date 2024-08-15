# Telecommunications Office Network Project

## Project Overview

The main goal of this project was to develop a secure, reliable network for a telecommunications office, supporting wired, wireless, and telephone use. The network was built with the following components:

- **1 Core Switch**: A multi-layer switch that functions as both a switch and a router.
- **3 Access Switches**
- **Firewalls**
- **Wireless LAN Controllers (WLCs)**
- **VoIP Gateway**

## Features and Configuration

### Network Security

- **Firewall**: Monitors and controls incoming and outgoing network traffic, ensuring robust security.
- **Wireless LAN Controllers**: Manages access points for secure and efficient wireless connectivity.
- **VoIP Gateway**: Provides voice communication over the IP network.

### Network Zones

The network was divided into several zones to enhance security and manage traffic:

- **Internal Network**: 
  - Consists of departments like HR, Marketing, IT Support, Admin, Software Engineers, and Cloud Engineers.
  - Supports both wired and wireless devices.

- **DMZ (Demilitarized Zone)**: 
  - Contains critical servers such as AD Server, ERP Server, Email Server, and File Storage.
  - Isolates these servers from the internal network to provide an extra layer of security.

- **External Network**: 
  - Connects to external entities like Azure Cloud for hosting applications and storage.

### VLAN Configuration

- **VLAN IDs**:
  - **50**: Wired (LAN) devices
  - **60**: Wireless (WLAN) devices
  - **101**: Telephone (VoIP) devices

- **BPDU Guard**: Enabled on the switch to quickly configure connections between the access switch and new devices without delay.

### Routing and DHCP Configuration

- **Routing**:
  - Routing is configured for LAN and WLAN, but not required for VoIP.
  - OSPF is configured between the core switch (acting as a router) and other devices like the firewall, WLC, and VoIP gateway.

- **DHCP**:
  - Two pools were created in the AD server: **LAN Pool** and **WLAN Pool** for wired and wireless users.
  - The WLAN pool includes the WLC address.
  - The AD server also acts as the DNS server.

### Firewall Configuration

- **Firewall Labels**: 
  - **INSIDE**
  - **OUTSIDE**
  - **DMZ**

- **Traffic Control**:
  - By default, the firewall blocks all traffic between these zones unless explicitly allowed.
  - Created objects within the firewall for necessary communication, such as **INSIDE-OUTSIDE** for wired and wireless users and **DMZ-OUTSIDE**.

### Additional Configurations

- **Remote Administration**:
  - One computer in the Software department is designated for the Senior Engineer to carry out all remote administration tasks using SSH.

- **WLC Configuration**:
  - The Senior Engineer accesses the WLC IP via a web browser to create user accounts and manage WLAN settings for employees and guests.

- **Cloud Integration**:
  - Configured users with Azure Cloud using the firewall for secure access.

- **VoIP Configuration**:
  - Configured to assign IP addresses and line numbers to telephones within the network.

## Conclusion

This network configuration ensures a secure, efficient, and scalable environment for the telecommunications office, with robust support for wired, wireless, and VoIP communications.
