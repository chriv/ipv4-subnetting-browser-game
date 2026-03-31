# IPv4 Subnetting Game for Networking Students

This is a work in progress, but here's something for networking students, network engineers, and IT professionals (yes, that includes you, networking nerds! 😉). How about a game for mastering IPv4 subnetting—computing subnet addresses, subnet masks, broadcast addresses, and first/last usable host addresses?

Ask and ye shall receive: [chriv.github.io/ipv4-subnetting-browser-game](https://chriv.github.io/ipv4-subnetting-browser-game)

If you're wondering how the chart at the top works, here's a simple, non-binary approach to subnetting that anyone can use, using the example **10.189.174.5/23** in the screenshot.

---

### Compute the Subnet Mask:

IP addresses and Subnet masks are 32-bits long, written as 4 8-bit octets separated by dots. The CIDR prefix (e.g., /23) determines the boundary between the network bits and the host bits. CIDR stands for Classless Inter-Domain Routing, but I'll spare you the lecture on classful vs. classless networks/subnets.

* Octets to the left of the transition point are fully 255 (all network bits).
* Octets to the right of the transition point are fully 0 (all host bits).
* Only the transition octet will have a value other than 0 or 255.

1. Find the CIDR value, **/23**. It lands in the 3rd Octet. This is our transition octet.
2. The "Mask" row for /23 shows **254** in that 3rd octet.
3. **Subnet Mask: 255.255.254.0**

---

### Compute the Subnet Address:

The subnet address is the first IP address on a network. It is reserved and identifies (together with the subnet mask) the subnet; it cannot be used for a host/node on the network. The left part of an IP address is the network portion, while the right portion is the host portion.

1. Look at the "Bits" row for /23—the value is **2**. This is our block size (or subnet increment) for the 3rd octet. The subnet will start on a multiple of this number in this octet.
2. 1st and 2nd Octets: Copy them (**10.189.**).
3. 3rd Octet: Find the closest multiple of 2 (our block size) that is less than or equal to 174. In this case, **174** is a multiple of 2.
4. 4th Octet: Set to **0**.
**Subnet Address: 10.189.174.0**

---

### Compute the Broadcast Address:

Every subnet has two reserved addresses. The last address is the broadcast address. To find it, first find where the next subnet starts. 

1. For **10.189.174.0/23**, the next subnet starts at **10.189.176.0** (adding our block size of 2 to the 3rd octet).
2. The broadcast address is the IP address immediately preceding the start of the next subnet.
**Broadcast Address: 10.189.175.255**

---

### Figure out the First and Last Usable Host Addresses:

The subnet address (first IP) and broadcast address (last IP) cannot be used for hosts. 

1. The **first usable IP** is one more than the subnet address (**10.189.174.1**). 
2. The **last usable IP** is one less than the broadcast address (**10.189.175.254**). 
**Usable Range: 10.189.174.1 - 10.189.175.254**

---

Let me know if you try the game! What's the hardest subnet you've encountered? 

#networking #ipv4 #subnetting #cisco #itcareers
