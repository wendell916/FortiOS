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
We are going to configure the interfaces of the lan interface on port 1 and configure the wan interface on port 2,Use the following commands to edit them successfully
```````````
config system interface -This get into the interfaces of the FortiOS
edit port1
set mode dhcp 
set role lan  
set alias wendellLAN 
set allowaccess https ssh ping

To verify your configuration use can use the command show 



