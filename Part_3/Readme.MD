
![Alt text](cover.jpg)

Udemy Course >> Network Infrastructure Automation Ansible Cisco GNS3 Part 3 (CCT/CCNA)

**********

Ansible Automation YAML Network Administration Cisco Infrastructure Deployment Programming Engineering GNS3 CCT CCNA P3

**********

Tips/Tricks/Notes/Commands URL Link: https://github.com/nimaxnimax/Udemy_Net_Infra_Automation_Ansible_Cisco_GNS3/

Instructor & Courses >> https://www.udemy.com/user/adrian-fischer-infotech/

**********

![Alt text](image.png)

GNS3 Cisco Lab Diagram

Topics:
- Router and Switch Configuration with Ansible YAML Files/Playbooks
- How to Configure L2 Switch and L3 Switch (MLS)
- How to Configure and Verify STP and RSTP

**********

Review Ansible Installation and Configuration + Git Repository

```bash

sudo apt update -y
sudo apt install ansible -y
ansible --version
sudo apt install git -y
git clone https://github.com/nimaxnimax/Udemy_Net_Infra_Automation_Ansible_Cisco_GNS3.git

```

**********

GNS3 and How to Install and Configure Routers and Switches for Cisco Ansible Lab? And Play a YAML File

```bash

cd Udemy_Net_Infra_Automation_Ansible_Cisco_GNS3/Part_3
ls -anp
cat ansible_hosts
cat secrets.yml
cat /etc/hosts
ansible-playbook -i ansible_hosts arp.yml

```

**********

How to Check IP Address Config on Routers Switches - Ansible YAML

```bash

ansible-playbook -i ansible_hosts interface_ip_address.yml
ansible-playbook -i ansible_hosts interface_svi_vlan_ip_address.yml

```

**********

How to Check Routing Table on Routers and MLS Switches - Ansible YAML

```bash

ansible-playbook -i ansible_hosts check_routing_table.yml
ansible-playbook -i ansible_hosts check_routing_table_static.yml

```

**********

How to Check Interfaces Connected to Routers or Switches - Asnbile YAML

```bash

ansible-playbook -i ansible_hosts cdp.yml
ansible-playbook -i ansible_hosts cdp_check_sw1_sw2_sw3_example.yml

```

**********



**********



**********



**********



**********



**********



**********



**********



**********



**********



**********

Review Configuring Cisco Routers & Switches for Basic Connectivity (Console/Telnet) and Cisco IOS Automation with Ansible

```bash
ansible-playbook -i ansible_hosts telnet_ssh_timeout_config.yml 
ansible-playbook -i ansible_hosts telnet_console_username_password_config.yml 
ansible-playbook -i ansible_hosts telnet_ssh_timeout_check.yml 
```

**********

Cisco Router & Switch Verification with Ansible (GNS3 Cisco Routing & Switching Lab)

```bash
ansible-playbook -i ansible_hosts version_check.yml
ansible-playbook -i ansible_hosts version_interface.yml 
ansible-playbook -i ansible_hosts version_uptime.yml 
ansible-playbook -i ansible_hosts version_memory.yml 
ansible-playbook -i ansible_hosts version_ios.yml 
ansible-playbook -i ansible_hosts version_check.yml
```

**********

Cisco Router & Switch SSH Configuration with Ansible

```bash
ansible-playbook -i ansible_hosts ssh_config.yml 
ssh-keygen -f "/home/adrian/.ssh/known_hosts" -R "sw1"
ssh -oHostKeyAlgorithms=ssh-rsa ansible@sw1
```

**********

How to Check MAC Address-Table on Switches with Ansible?

```bash
ansible-playbook -i ansible_hosts mac_address_table_3725_check.yml 
ansible-playbook -i ansible_hosts mac_address_table_3725_check_count.yml 
ansible-playbook -i ansible_hosts mac_address_table_vios_check.yml 
ansible-playbook -i ansible_hosts mac_address_table_vios_check_count.yml 
```

**********

How to Change Hostname on Routers/Switches with Ansible?

```bash
ansible-playbook -i ansible_hosts hostname_config_and_check.yml
```

**********

How to Check Interfaces on Routers/Switches with Ansible?

```bash
ansible-playbook -i ansible_hosts if_desc.yml
ansible-playbook -i ansible_hosts if_up.yml
ansible-playbook -i ansible_hosts interface_ip.yml
```

**********

How to Check Interface Speed Duplex with Ansible?

```bash
ansible-playbook -i ansible_hosts interface_speed_duplex_run_config.yml
ansible-playbook -i ansible_hosts interface_speed_duplex.yml
```

**********

How to Check Errors and CRC on Routers/Switches with Ansible?

```bash
ansible-playbook -i ansible_hosts interface_CRC.yml
```

**********

How to Change Passwords on Routers/Switches with Ansible?

```bash
ansible-playbook -i ansible_hosts username_password_enable_secret.yml
```

**********

How to Config VLANs on vIOS L2 Switches and Verify with Ansible?

```bash
ansible-playbook -i ansible_hosts vlan_config_vios_switch.yml
ansible-playbook -i ansible_hosts vlan_checking_vios.yml
```

**********

How to Config VLANs on 3725/3745 Ether Switches and Verify with Ansible?

```bash
ansible-playbook -i ansible_hosts vlan_config_3725_3745_switch.yml
```

**********

How to Config SVI Interface VLANs on vIOS & 3725/3745 MLS Switches and Verify with Ansible?

```bash
ansible-playbook -i ansible_hosts interface_vlan_svi_config_switches_mls.yml
```

**********

How to Configure Routing on MLS Switches and Check Routing Table and ARP with Ansible?

```bash
ansible-playbook -i ansible_hosts mls_config_and_routing.yml
```

**********

How to Check CDP and IP Addresses on Routers/Switches with Ansible?

```bash
ansible-playbook -i ansible_hosts cdp.yml 
ansible-playbook -i ansible_hosts cdp_detail.yml 
```

**********

How to Configure Access Ports & Trunk Ports on L2 L3 Switches with Ansible?

```bash
ansible-playbook -i ansible_hosts access_and_trunk_port_config_switches.yml
```

**********

How to Configure Default Gateway on L2 Switches with Ansible?

```bash
ansible-playbook -i ansible_hosts switch_default_gw_config.yml
```

**********

How to Check Connectivity in the Network on Routers/Switches with Ansible?

```bash
ansible-playbook -i ansible_hosts cisco_ping_check.yml
```

