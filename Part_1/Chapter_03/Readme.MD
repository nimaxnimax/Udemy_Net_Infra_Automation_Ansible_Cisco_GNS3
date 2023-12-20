![Alt text](image3.png)


Configuring Cisco Routers and Switches for Basic Connectivity and Cisco IOS Automation with Ansible


Ansible typically connects to devices over SSH, so we'll ensure that SSH is properly configured on the router and switch. Configuration example >>

### Basic Cisco Router or Switch Configuration:

```bash
enable
configure terminal

hostname Router_Switch
enable secret cisco
line console 0
  password cisco
  login
exit

line vty 0 15
  login local
exit

interface GigabitEthernet0/0
  ip address 192.168.1.1 255.255.255.0
  no shutdown
exit

ip domain-name domain.local
crypto key generate rsa modulus 2048
username ansible privilege 15 secret ansible

end
write memory

```

### Notes:
- Ensure that the router and switch are reachable from the Ansible control machine (have proper routing and connectivity).
- For Ansible to manage these devices, you would typically have an Ansible inventory file with the devices' IP addresses and SSH credentials.

This is a basic setup, and in a production environment, you'd likely use more advanced security measures. Always follow best practices and security guidelines when configuring network devices.

