<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Resources and Virtual Machines VM-1 and VM-2
- Connect to VM-1 using Windows Virtual Desktop
- Install Wireshark on VM-1
- Filter and Observe ICMP Traffic
- Filter and Observe SSH Traffic
- Filter and Observe DNS Traffic
- Filter and Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Before we get started we need to think about what our objectives are. In this lab we're trying to create two <em>virtual machines</em> and get them to talk to each other within the same <em>virtual network</em>. To accomplish this, we first need to create a <em>resource group</em> to house both virtual machines, their components, and the virtual network that will tie them all together.
</p>
<br />
<p>
<img src="https://github.com/amaraphi/azure-network-protocols/assets/144752187/da3daa8d-c707-46d0-8ee5-58d15d28a373"/>
</p>
<p>
On the Azure portal homepage, click "Resource Groups." Alternatively, you can use the search bar to search for resource gruops. Click "create" to create a new resource group, "RG-1," which will be contained inside of your current Azure subscription.
</p>
<p>
<img src="https://github.com/amaraphi/azure-network-protocols/assets/144752187/a8426ecf-ee78-4099-b87b-9714d31c1dc9/>
</p>

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
