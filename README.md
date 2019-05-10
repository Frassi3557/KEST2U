# Lokaverkefni KEST2U

All end devices refer to the ISP_DHCP_DNS server for their DNS address.

The home network and the business network can not communicate with each other.
They can both ping the S_ISP and ISP_DHCP_DNS.
ISP_DHCP_DNS provides the wireless networks as well as the S_ISP with their IP's.
All wireless devices are connected to the given router in their network via WPA2 Personal mode.
All passwords in the project are: "password".
Each network has access for guests, with one user on each connected.

As for the RIX and tskoli server, I couldn't figure out how to get them to work.


# ISP_DHCP_DNS:

FastEthernet 0: 192.168.1.1 /24

# R_ISP:

VLAN 1 - 192.168.4.1 /24

GigabitEthernet 0/0/0 - 192.168.11.11 /24 (Conects to RIX)
GigabitEthernet 0/0/1 - 192.168.1.3 /24 ( Connects to S_ISP)

# S_ISP:

VLAN 1 - 192.168.1.2 /24

FastEthernet 0/1 - Connects to Home Router (Heimili)
FastEthernet 0/2 - Connects to Home Router (Fyrirtæki)

GigabitEthernet 0/1 - Connects to R_ISP
GigabitEthernet 0/2 - Connects to ISP_DHCP_DNS

# Home Router (Heimili):

Internet - Supplied via DHCP.

LAN - 192.168.2.1 /24

All wireless and wired devices connect to the home router. Their IP's are supplied via DHCP.

# Home Router (Fyrirtæki):

Internet - Supplied via DHCP.

LAN - 192.168.3.1 /24

GigabitEthernet 0/1 - Connects to SW1
	
	SW1:

	All wired devices connect to this switch.

	VLAN 1 - 192.168.2.3 /24	

	FastEthernet 0/1-8 - Connects to PC's 0-7, IP addresses are supplied via DHCP (192.168.2.130-254 /24).
	Default Gateway refers to the Home Router.
