![Topology Diagram](images/topology.png)
🎯 Lab Objective

The objective of this lab is to configure IP addresses on Cisco router interfaces, enable those interfaces, and verify end-to-end connectivity between multiple networks using basic Layer 3 routing.

This lab demonstrates how a router connects different IP networks and acts as a default gateway for hosts.

🌐 Topology Overview

Devices:

1 Router (R1)

3 Switches (SW1, SW2, SW3)

3 PCs (PC1, PC2, PC3)

⚙️ Configuration Steps

1️⃣ Set Router Hostname

Enter privileged EXEC mode

Enter global configuration mode

Change hostname to R1

2️⃣ Verify Interfaces

Use a show command to check interface status

Observe that interfaces are administratively down by default

3️⃣ Configure Router Interfaces

For each interface:

Enter interface configuration mode

Assign IP address and subnet mask

Add interface description

Enable the interface using no shutdown

4️⃣ Verify Interface Status

Confirm interfaces show up/up state

5️⃣ Save Configuration

Save running configuration to startup configuration

6️⃣ Configure PC IP Addresses

Assign IP address and subnet mask manually

Configure default gateway as the router interface IP

7️⃣ Test Connectivity

Use ping to verify inter-network communication

enable

configure terminal

hostname R1

show ip interface brief

do show ip interface brief

interface gigabitethernet 0/0

ip address 15.255.255.254 255.0.0.0

description ## To SW1 ##

no shutdown

interface gigabitethernet 0/1

ip address 182.98.255.254 255.255.0.0

description ## To SW2 ##

no shutdown

interface gigabitethernet 0/2

ip address 201.191.20.254 255.255.255.0

description ## To SW3 ##

no shutdown

end

show ip interface brief

show running-config

copy running-config startup-config

write memory

🧠 Technical Explanation

This lab teaches fundamental Layer 3 routing principles.

Each router interface must belong to a different IP subnet. When hosts send traffic to another network, they forward it to their default gateway, which is the router interface.

The no shutdown command changes the administrative state of the interface from down to up, activating Layer 1.

In show ip interface brief:

Status represents Layer 1 (physical layer)

Protocol represents Layer 2 (data link layer)

Saving the configuration ensures the router retains settings after a reboot.

🏢 Real-World Use Case

This configuration reflects a small business network where different departments operate on separate subnets.

A router connects these subnets and enables communication between them.

Without correct IP addressing and gateway configuration, devices in different networks cannot communicate.

🛠️ Skills Gained

Cisco IOS CLI navigation

Router interface configuration

IP addressing and subnet mask usage

Understanding administrative vs operational interface states

Default gateway logic

Configuration verification

Basic network troubleshooting

🚀 Possible Improvements

Add static routes between multiple routers

Implement VLAN segmentation

Configure DHCP instead of static IP assignment

Add SSH for secure remote access

Apply basic ACLs for traffic filtering

Configure basic security settings

🧩 Troubleshooting Notes

If connectivity fails, check the following:

show ip interface brief

Ensure interfaces are not administratively down

Verify correct subnet masks

Confirm correct default gateway configuration on PCs

Ensure IP addresses belong to the correct subnet

Verify physical connections in the topology

A common issue is forgetting the no shutdown command, which keeps the interface in an administratively down state.
