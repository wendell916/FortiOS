# FortiOS
Installation and configuration of fortigate firewall in vmware 

* Create an account on Fortinet to download the installation image.
* Log in to your account.
* Navigate to Support > VM Images.
* Due to licensing issues, preferably install FortiGate version 7.2.10 instead of the latest version.
* Select the platform as VMware ESXi and download the image.
* Import the OVA file into VMware.
* The default CLI credentials are:
````
Username: admin
Password: (Press Enter, as there is no default password)
``````
* You will be prompted to change your password before proceeding.
  
# Case Study 
A client requires a FortiGate firewall to prevent unauthorized access to their network and enforce strict content filtering policies. The firewall should ensure that end users cannot access social media sites, betting sites, and sexually explicit websites while connected to the company network.

# Network Archictecture Overview.
*  Lan interface-The internal network of the company
*  Wan interface- Internet provided by the isp

# Configuring of interfaces via cli
We are going to configure the interfaces of the wan interface on port 1 and configure the lan interface on port 2,Use the following commands to edit them successfully
```````````
config system interface -This get into the interfaces of the FortiOS
edit port1
set mode dhcp 
set role wan  
set alias wendellWAN 
set allowaccess https ssh ping

To verify your configuration use the command show
enter command next
edit port2
set mode static

set role lan
set alias wendellLAN
set allowaccess https ssh ping
set ip  "your-default gateway of your internal network" eg. 192.168.200.1/24
end -To exit out of the interface
```````````
````
To access the fortigate firewall via gui
Enter the command get system interface physical
Under the management port, you should see an ip address .Use that to access the gui via https.
````
You can equally configure the interface via the gui as well. 
![image](https://github.com/user-attachments/assets/4ea6433f-61b2-4a9a-bab8-692b3ea36f3d)

# Configuring the interfaces via gui
````
Since I made the interface configurations directly through the CLI, the interfaces were already correctly reflected in the system as per the configuration I applied.
You can click on any of the ports to make changes to the interfaces as preferred.
````
<img width="959" alt="image" src="https://github.com/user-attachments/assets/37e63d0c-a5a6-45cb-bf4c-cbac0d196f83" />

# Configuring DNS Filtering
DNS Filtering enhances network security by restricting access to unauthorized or malicious websites by preventing DNS resolution. When enabled, requests to blocked domains—such as google.com—will fail to resolve into an IP address, effectively preventing users from accessing those sites. This proactive approach helps enforce security policies, minimize exposure to harmful content, and improve overall network control.

* Go to Security Profiles > DNS Filter
* Create New Profile
* Under Fortiguard Filtering, toggle it enabled if not enabled
* You will see categories you can either allow,monitor or redirect to block portal.
* In this case study, I chose gambling, nudity and risque, pornography and entertainment to block portal.
* I also enabled Redirect botnet C&C requests to Block portal
* Enabled Enforce 'SafeSearch' pm Google,Bing,Youtube and also restricted Youtube Access to strict

![image](https://github.com/user-attachments/assets/5abae4f0-caad-44d0-b8bc-49892be87be3)


# Configuring Web Filtering
* Go to Security Profiles > Web Filter
* Create New profile
* Under Fortiguard Filtering
* Choose the categories you prefer to monitor,allow or block to redirect portal.
* You can also enable URL filter and manually enter websites you will want to block. I manually blocked two social media websites.
  
![image](https://github.com/user-attachments/assets/80f1af66-ebcc-49be-a946-78c26e482d38)

# Configuring Firewall Policies
Firewall policies control how traffic flows between networks eg. lan to wan traffice  and vice versa.
Without Firewall policies:
* Internal users cannot access the internet
* Security policies like the ones we have created cannot be applied.
* In this case I only configured two  firewall policies. i.e lan-to-internet policy and internet-to-lan policies.
* Go Policy & Objects > Firewall policy
  
![image](https://github.com/user-attachments/assets/7ecd234b-1e17-4c06-84f1-d7797689b149)

![image](https://github.com/user-attachments/assets/c9ad8b23-5d5e-4b94-9130-42b74f56ac81)

![image](https://github.com/user-attachments/assets/0d0d4bd0-1f0d-4efd-b7a3-63cf43ef5ad3)







