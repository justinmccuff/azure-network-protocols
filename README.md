<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>
<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this instructive tutorial, we embark on a comprehensive exploration of network traffic interactions involving Azure Virtual Machines through the utilization of Wireshark. Additionally, we engage in practical experimentation with Network Security Groups (NSGs), enhancing our understanding of network security within the Azure environment. Throughout this tutorial, we delve into the intricacies of network monitoring, analysis, and security configuration, equipping you with valuable insights and skills for effective network management and security in an Azure Virtual Machine environment.<br />

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

- Create our Resources
- Create Virtual Machine
- Install Wireshark
- Observe SSH, RDH, DNS, HTTP/S, ICMP Traffic

<h2>Actions and Observations</h2>

![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/a4344f8f-1f11-4894-ae19-38967276734f)
![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/3a5a91a7-3820-4f42-b311-73329b8f947e)
![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/7fd697ff-56c7-42b2-a780-d4148a5d40ab)

<p>
Let's commence the process by establishing our resource groups within the Azure environment. To do this, navigate to the Azure homepage and initiate a search for 'Resource Groups.' If you don't find it readily listed under Azure services, please conduct the search.

While creating your resource groups, you have the liberty to assign them any relevant names. However, it's imperative to exercise diligence when selecting the region. Take note of the region you choose, as this information will be pivotal when we proceed to configure our Virtual Machines (computers).
</p>
<br />

![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/61ce7de1-5b48-467e-9b77-e4f8fcc9d31c)

Our subsequent step entails the creation of a Virtual Machine (VM). Should you not find it readily available under Azure Services, utilize the search function to locate it.

When configuring your VM, it is of utmost importance to ensure its placement within the identical region as your designated resource group. Moreover, you retain the freedom to designate custom names for your VMs. However, it is critically imperative to meticulously recall and document these chosen names for future reference.

Ensure that you select 'Windows 10 Pro' as the operating system, and take note of both the PC name and password for later use. Maintain the default settings for all other configuration options. After creating your initial VM, proceed to create a second VM. For this one, opt for the 'Linux (Ubuntu)' image under the 'image' selection.

![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/61985342-2f64-4295-8b11-ae28b40ce632)


![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/16afc86f-f8a4-4915-b1ac-d2e66c1780b9)

<p>
Next, we will initiate the login process to access your Windows Virtual Machine (VM) using the 'Remote Desktop' feature. To do this, we need to obtain the IP address of your Windows VM in the Azure environment. Please copy and paste the VM's IP address into the 'Remote Desktop' application, as shown in the image above.

Subsequently, the system will prompt you to provide your username and password for the Windows VM that we created earlier. Please enter the designated VM username and password accordingly.

Upon successful login, you will be greeted with an interface resembling the following.
![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/0c1bea19-bd04-4fc3-8532-31c11c4de1ce)

While logged into your Virtual Machine (VM), it's essential to navigate to your VM's web browser. From there, proceed to initiate a search for 'Install Wireshark.'

Wireshark is a highly regarded network protocol analyzer and packet inspection tool used for in-depth network analysis. Installing Wireshark can greatly enhance your network monitoring and troubleshooting capabilities.

Once you locate the appropriate download source, follow the installation process diligently. Ensure that you adhere to best practices regarding software installation, including verifying the source's authenticity and accepting any necessary licenses or agreements.

After successfully installing Wireshark, you'll have a powerful tool at your disposal for monitoring and analyzing network traffic within your VM environment.
</p>
<br />

![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/f76c9ed2-2e8d-46b3-9504-d6b8255ccac4)

<p>
After successfully completing the installation of the Wireshark program, proceed to open it. Wireshark, a robust network protocol analyzer and packet inspection tool, provides valuable insights into network traffic.

Within Wireshark, employ a filter to focus exclusively on ICMP (Internet Control Message Protocol) traffic. ICMP traffic encompasses important network control messages, including ping requests and responses.

Now, your objective is to retrieve the private IP address of the Ubuntu Virtual Machine (VM). To accomplish this, open the 'Command Prompt' within your Windows 10 VM and initiate a ping command directed towards the Ubuntu VM's IP address.

Observe the ping requests and replies meticulously within the Wireshark interface. This step allows you to gain a clear understanding of how ICMP traffic is processed within your network environment.

Subsequently, extend your network analysis by attempting to ping a public website, such as 'www.google.com.' Observe and analyze the traffic patterns captured by Wireshark as it reflects the communication between your Windows 10 VM and the external website.

These exercises with Wireshark offer valuable insights into network behavior, enabling you to monitor and troubleshoot network activities effectively 

  ![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/91b7ffb5-3b70-4be4-b985-4a66ecbdf2de)


To delve into the observation of DHCP (Dynamic Host Configuration Protocol) traffic, return to the Wireshark application. Once there, create a filter that specifically isolates DHCP traffic, enabling you to focus exclusively on the dynamic network configuration processes.

From your Windows 10 VM, you can actively participate in this network operation. Initiate the process by attempting to request a new IP address for your VM from the command line. Execute the 'ipconfig /renew' command to trigger this operation.

Observing this DHCP traffic within Wireshark provides a comprehensive view of the DHCP negotiation process, including requests and responses. It offers invaluable insights into how IP addresses are dynamically assigned and managed within your network environment, fostering a deeper understanding of network dynamics and troubleshooting capabilities.

![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/afd52767-8659-4436-8a17-44ec25eeefe6)

To gain insights into DNS (Domain Name System) traffic, return to the Wireshark application and create a dedicated filter to isolate DNS traffic exclusively. This focused approach allows for a detailed examination of DNS-related network activity.

Now, from your Windows 10 VM, proceed to the command line interface to engage in DNS resolution. Utilize the 'nslookup' command to query and retrieve the IP addresses associated with specific domains. For instance, you can inquire about the IP addresses of 'google.com' and 'disney.com.'

Observing DNS traffic within Wireshark alongside the DNS resolution performed through 'nslookup' provides a comprehensive understanding of how domain names are translated into IP addresses. This insight is crucial for troubleshooting network connectivity and ensuring smooth and accurate domain resolution within your network environment.

![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/ac7246e5-8302-4fa2-a3b1-c9e10889de43)

To gain a deeper understanding of Remote Desktop Protocol (RDP) traffic, return to the Wireshark application and create a precise filter to exclusively capture RDP traffic. Use the filter 'tcp.port == 3389' to focus solely on RDP-related network activity.

RDP is a dynamic protocol that facilitates live streaming of one computer's display to another, facilitating seamless remote connections. Consequently, RDP traffic is in a constant state of transmission as it conveys the real-time screen and input data between devices.

Analyzing RDP traffic within Wireshark provides valuable insights into the intricacies of remote desktop connections. By isolating and studying this traffic, you can gain a comprehensive view of how data is exchanged between computers during remote desktop sessions. This knowledge enhances your ability to troubleshoot and optimize remote desktop configurations within your network environment.
![image](https://github.com/justinmccuff/azure-network-protocols/assets/143865133/8bf6201f-4fa7-444d-b065-8083cc0be0ef)

</p>
<br />

