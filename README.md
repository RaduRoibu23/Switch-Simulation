# Switch Simulation with VLAN and STP Support

This project simulates a network switch with support for VLAN (Virtual Local Area Networks) and STP (Spanning Tree Protocol). It is designed to help you understand the inner workings of network switches and the protocols they use to manage network traffic and avoid loops.

## Learning Objectives

- Understand the basics of network switching.
- Learn how VLANs are used to segment network traffic.
- Explore the STP protocol and how it prevents network loops.
- Gain experience with Python and C libraries for low-level networking tasks.

## Features

- **Ethernet Header Parsing**: Extracts destination MAC, source MAC, EtherType, and VLAN ID from Ethernet frames.
- **VLAN Tagging**: Adds VLAN tags to Ethernet frames.
- **BDPU Sending**: Sends Bridge Protocol Data Units (BPDUs) periodically to maintain the spanning tree.
- **Resource Initialization**: Sets up the switch's MAC address table, VLAN configuration, and interface states.
- **Trunk and Access Forwarding**: Handles packet forwarding for both trunk and access interfaces.

## Functions

- `parse_ethernet_header(data)`: Parses the Ethernet header from the given data and returns the destination MAC, source MAC, EtherType, and VLAN ID.

- `create_vlan_tag(vlan_id)`: Creates a VLAN tag for the specified `vlan_id`.

- `send_bdpu_every_sec()`: Sends Bridge Protocol Data Unit (BPDU) packets every second if necessary. This function runs in a separate thread to avoid blocking the main process.

- `init_resources()`: Initializes switch resources, including the MAC address table, VLAN configuration, and interface states.

- `translate_trunk(vlan)`: Converts the VLAN string to an integer value. Returns `0` if the VLAN is set to "trunk" (`'T'`).

- `trunk_forwarding(dest_mac, vlan_id, interface, data, length, table, vlan, interfaces, interface_state)`: Handles packet forwarding for trunk interfaces. Looks up the MAC address table and VLAN configuration and forwards the packet to the correct interface based on these settings.

- `access_forwarding(dest_mac, vlan_id, interface, data, length, table, vlan, interfaces, interface_state)`: Manages packet forwarding for access interfaces. Utilizes the MAC address table and VLAN configuration and forwards the packet to the appropriate access interface based on the destination MAC and VLAN settings.

- `main()`: The main function that initializes switch resources, starts the BPDU sending thread, and continuously processes incoming packets by updating the MAC address table, processing BPDUs, and forwarding packets according to the VLAN configuration.

## Learning Process

This project is an opportunity to explore network programming concepts. By working through the code, you will gain insights into:

- Parsing and manipulating Ethernet frames
- Using VLANs for network segmentation
- Understanding STP to prevent network loops
- Gaining practical experience with threading and low-level networking in Python

## Conclusion

This switch simulation project serves as a valuable learning tool for anyone interested in network programming and protocols. It provides hands-on experience with key networking concepts and helps build a foundational understanding of how network switches operate.

Feel free to explore the code, try different configurations, and enhance the functionality as you deepen your knowledge of network switches and protocols.
