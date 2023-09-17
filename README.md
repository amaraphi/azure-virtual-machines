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
<img src="https://github.com/amaraphi/azure-network-protocols/assets/144752187/a8426ecf-ee78-4099-b87b-9714d31c1dc9"/>
</p>
<p>
<b>Next, let's create our first virtual machines.</b> We'll first create a VM with a Windows 10 OS. In the Azure portal search for 
"virtual machines." Once in the virtual machiens default directory, click "Create --> Azure Virtual Machine."
Select the resource group you just created. DOuble-check to make sure that your VM is within this resource group. Remember, our virtual network environment will be within this resource group. 
</p>
<p>
  Scrolling down to "Instance Details," select your apprpriate region. Keep note of the region selected -- both your VMs will need to be within the same region. Though optional, you can select a redunancy option to protect against data loss.
</p>
  <p>
    <img src="https://github.com/amaraphi/azure-network-protocols/assets/144752187/d8c54a26-664a-4947-bdbf-14bc0066f128"/>
</p>
<p>Under "Image," select "Windows 10 Pro." Under "Size," select a Standard machine with 2-4 CPUs.</p>
<p><img src="https://github.com/amaraphi/azure-network-protocols/assets/144752187/9beb90ea-d35c-4417-a552-70271bf7b0cf"/>
</p>
<p>Under "Administrator Account" create a username and password. For the sake of this lab we'll have a generic username, lab_user. This username and password will be used to remotely log in to our VM. Under "Inbound Port Rules," note that only inbound RDP traffic is accessible to our VM from the internet. Click "Review and Create." On the Validation page, if we scroll down to "Networking," we can observe that a virtual network, subnet, and public IP address has been created for our VM. Click "Create." </p>
<p><img src="https://github.com/amaraphi/azure-network-protocols/assets/144752187/7a6544c0-92fd-4d9a-98d8-5f5c32f5fa07"/>
</p>
<p>Repeating the same steps above, create another VM. Again, this VM should be inside of the same resource group, RG-1, as your Windows 10 VM. Select the same region as VM-1. Under image, we're selecting an Ubuntu Server.</p>
<img src="https://github.com/amaraphi/azure-network-protocols/assets/144752187/ab358ffb-0770-4765-8298-fa5577f86fb1"/>
Scrolling down to "Administrator Account," select "Password" under "Authentication Type." This will prompt us to enter a username and password in order for us to remotely access our Ubuntu machine later in our lab. Observe that under "inbound port rules," our newly-created VM's SSH port 22 will be open and accessible from the Internet.
<br />
