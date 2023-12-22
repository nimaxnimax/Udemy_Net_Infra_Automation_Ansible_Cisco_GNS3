![Alt text](image5.png)


Basic Cisco Router and Switch Configuration with Ansible - GNS3 Cisco Routing & Switching Lab


**Linux Commands**
```bash

cd $home

cd Udemy_Net_Infra_Automation_Ansible_Cisco_GNS3/Part_1/Chapter_05

ls -anp | grep yml

ansible-playbook -i ansible_hosts aaa_check.yml

ansible-playbook -i ansible_hosts aaa_config.yml

ansible-playbook -i ansible_hosts logging_check.yml

ansible-playbook -i ansible_hosts logging_config.yml

ansible-playbook -i ansible_hosts service_check.yml

ansible-playbook -i ansible_hosts service_config.yml

ansible-playbook -i ansible_hosts snmp_check.yml

ansible-playbook -i ansible_hosts snmp_config.yml

ansible-playbook -i ansible_hosts telnet_ssh_timeout_check.yml

ansible-playbook -i ansible_hosts telnet_ssh_timeout_config.yml

ansible-playbook -i ansible_hosts vlan_config.yml

ansible-playbook -i ansible_hosts vlan_show.yml

ssh -oHostKeyAlgorithms=ssh-rsa ansible@r1

ssh -oHostKeyAlgorithms=ssh-rsa ansible@r1

ssh -oHostKeyAlgorithms=ssh-rsa ansible@r2

ssh -oHostKeyAlgorithms=ssh-rsa ansible@sw1

ssh -oHostKeyAlgorithms=ssh-rsa ansible@sw2

ssh -oHostKeyAlgorithms=ssh-rsa ansible@sw3

ssh -oHostKeyAlgorithms=ssh-rsa ansible@sw4

ssh -oHostKeyAlgorithms=ssh-rsa ansible@sw5

ssh -oHostKeyAlgorithms=ssh-rsa ansible@sw6

ping r1

ping r1

ping r2

ping sw1

ping sw2

ping sw3

ping sw4

ping sw5

ping sw6

```

**********
Configuring a basic router and switch involves setting up interfaces, IP addresses, and basic routing on the router, as well as configuring VLANs and interfaces on the switch. Here's a simple example using Cisco IOS commands for a router and a switch. Please adapt the commands based on your network requirements and equipment.

### Router Configuration:

1. **Enter Global Configuration Mode:**
   ```bash
   enable
   configure terminal
   ```

2. **Configure Interfaces:**
   ```bash
   interface GigabitEthernet0/0
   ip address 192.168.1.1 255.255.255.0
   no shutdown

   interface GigabitEthernet0/1
   ip address 10.0.0.1 255.255.255.0
   no shutdown
   ```

   Adjust interface types and IP addresses based on your network setup.

3. **Enable Routing (if needed):**
   ```bash
   ip routing
   ```

4. **Configure a Default Gateway (if needed):**
   ```bash
   ip route 0.0.0.0 0.0.0.0 <gateway-IP>
   ```

   Replace `<gateway-IP>` with the IP address of the next-hop router.

5. **Exit Configuration Mode and Save:**
   ```bash
   exit
   write memory
   ```

### Switch Configuration:

1. **Enter Global Configuration Mode:**
   ```bash
   enable
   configure terminal
   ```

2. **Configure VLANs:**
   ```bash
   vlan 10
   name DATA

   vlan 20
   name VOICE
   ```

   Add more VLANs as needed.

3. **Assign VLANs to Interfaces:**
   ```bash
   interface range GigabitEthernet0/1 - 24
   switchport mode access
   switchport access vlan 10
   ```

   This example assigns VLAN 10 to interfaces GigabitEthernet0/1 to 24.

4. **Configure Trunk (if connecting to another switch or router):**
   ```bash
   interface GigabitEthernet0/0
   switchport mode trunk
   ```

   Adjust the interface type as needed.

5. **Enable Interface and Save Configuration:**
   ```bash
   interface range GigabitEthernet0/1 - 24
   no shutdown

   exit
   write memory
   ```

Certainly! Let's go through a basic example of configuring a Cisco router and switch. In this example, we'll set up a router with two interfaces and a switch with VLANs.

### Router Configuration:

1. **Enter Global Configuration Mode:**
   ```bash
   enable
   configure terminal
   ```

2. **Configure Interfaces:**
   ```bash
   interface GigabitEthernet0/0
   ip address 192.168.1.1 255.255.255.0
   no shutdown

   interface GigabitEthernet0/1
   ip address 10.0.0.1 255.255.255.0
   no shutdown
   ```

   Adjust interface types and IP addresses based on your network setup.

3. **Enable Routing:**
   ```bash
   ip routing
   ```

4. **Configure a Default Gateway (if needed):**
   ```bash
   ip route 0.0.0.0 0.0.0.0 <gateway-IP>
   ```

   Replace `<gateway-IP>` with the IP address of the next-hop router.

5. **Exit Configuration Mode and Save:**
   ```bash
   exit
   write memory
   ```

### Switch Configuration:

1. **Enter Global Configuration Mode:**
   ```bash
   enable
   configure terminal
   ```

2. **Configure VLANs:**
   ```bash
   vlan 10
   name DATA

   vlan 20
   name VOICE
   ```

   Add more VLANs as needed.

3. **Assign VLANs to Interfaces:**
   ```bash
   interface range FastEthernet0/1 - 24
   switchport mode access
   switchport access vlan 10
   ```

   This example assigns VLAN 10 to interfaces FastEthernet0/1 to 24.

4. **Configure Trunk (if connecting to another switch or router):**
   ```bash
   interface GigabitEthernet0/1
   switchport mode trunk
   ```

   Adjust the interface type as needed.

5. **Enable Interface and Save Configuration:**
   ```bash
   interface range FastEthernet0/1 - 24
   no shutdown

   exit
   write memory
   ```

Configuring various services on a Cisco router involves setting up features such as DHCP, NAT, and NTP. Here's an example of configuring some common services on a router or switch:

### DHCP Configuration:

1. **Configure DHCP Pool:**
   ```bash
   ip dhcp pool MY_POOL
   network 192.168.1.0 255.255.255.0
   default-router 192.168.1.1
   dns-server 8.8.8.8
   ```

   Adjust the network, default-router (gateway), and DNS server as needed.

2. **Assign DHCP to an Interface:**
   ```bash
   interface GigabitEthernet0/0
   ip address dhcp
   ```

### NAT Configuration:

3. **Configure NAT (Dynamic PAT - Overload):**
   ```bash
   ip nat inside source list 1 interface GigabitEthernet0/1 overload
   ```

4. **Define NAT Inside and Outside Interfaces:**
   ```bash
   interface GigabitEthernet0/0
   ip nat inside

   interface GigabitEthernet0/1
   ip nat outside
   ```

5. **Create an Access Control List (ACL):**
   ```bash
   access-list 1 permit 192.168.1.0 0.0.0.255
   ```

   Adjust the ACL to match your internal network.

### NTP Configuration:

6. **Configure NTP Server:**
   ```bash
   ntp server 0.pool.ntp.org
   ```

7. **Set Timezone:**
   ```bash
   clock timezone EST -5
   ```

8. **Enable NTP on the Router:**
   ```bash
   clock calendar-valid
   ntp update-calendar
   ```

### Syslog Configuration:

9. **Configure Syslog:**
    ```bash
    logging buffered 51200
    logging console critical
    logging host 192.168.1.2
    ```

   Adjust the logging host IP address as needed.

10. **Configure SSH Timeout:**
    ```bash
    line vty 0 4
    exec-timeout 10 0
    ```

   This example sets an SSH timeout of 10 minutes.

11. **Configure SNMP:**
    ```bash
    snmp-server community public RO
    ```

   Replace "public" with your desired SNMP community string.

### AAA Configuration:

12. **Configure AAA for Local Authentication:**
    ```bash
    aaa new-model
    aaa authentication login default local
    ```

   This example uses local authentication.

13. **Configure Enable Secret Password:**
    ```bash
    enable secret <enable-secret>
    ```

   Replace `<enable-secret>` with your desired enable secret.

