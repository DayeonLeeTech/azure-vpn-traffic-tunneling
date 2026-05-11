# azure-vpn-traffic-tunneling

## Introduction
This lab environment was established to demonstrate the deployment of cloud-based infrastructure and the implementation of multi-layered networking tunnels. By provisioning a Virtual Machine (VM) in a distinct geographic region and subsequently layering a Virtual Private Network (VPN) within that environment, this project explores how public IP addresses are assigned, masked, and routed across global infrastructures. The objective is to validate the integrity of encrypted tunnels and observe regional DNS redirection in a controlled cloud environment.

## Technical Skills & Tools
* Cloud Infrastructure: Microsoft Azure (Resource Groups, Virtual Machines, Network Security Groups).
* Networking Protocol: Remote Desktop Protocol (RDP) for secure administrative access.
* Traffic Management: VPN Tunneling via ProtonVPN.
* Geolocation Analysis: Public IP auditing and regional content validation.
* Cost Management: Resource lifecycle management and decommissioning.

---
## Part 1: Cloud Resource Provisioning
The foundation of the lab involved establishing an isolated environment in Microsoft Azure. A dedicated Resource Group was created to act as a logical container for all networking assets. Within this container, a Windows 11 Pro instance was deployed in a South Africa data center to establish a distinct geographic baseline. Network Security Groups (NSGs) were configured to allow secure RDP access from a specific administrative IP, ensuring the instance remained protected while reachable across global boundaries.

<p align="center">
  <img src="assets/vm-ip-check.png" width="800" alt="My Lab Setup" />
</p>

---

# Part 2: VPN Tunneling & Security
ProtonVPN was implemented within the virtualized environment to establish a secondary encrypted tunnel. This configuration allows for "tunnel-within-a-tunnel" routing, effectively masking the VM's cloud-provider origin.
* Traffic Encapsulation: Successfully routed outbound traffic from the Azure backbone through a third-party VPN exit node.
* Geolocation Masking: Transitioned the public identity of the VM from South Africa to a third country (e.g. Netherland) to test regional delivery.
* Administrative Stability: Managed the VPN routing table to ensure the active RDP connection was maintained without a "blackout" or session drop.
* Evidence of Masking: Verified the success of the tunnel by monitoring real-time IP changes via external auditing sites.

<p align="center">
  <img src="assets/vpn-ip-verification.png" width="800" alt="ICMP Connectivity Test" />
  <br>
  <i>Figure 2: Using Wireshark to capture successful ICMP traffic, confirming a solid connection between the two nodes.</i>
</p>
