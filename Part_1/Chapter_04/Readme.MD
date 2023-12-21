Basic Cisco Router and Switch Verification with Ansible - GNS3 Cisco Routing & Switching Lab


**Linux Commands**
   ```
   cat /etc/hosts
   sudo vi /etc/hosts

   ping r1
   ping sw1

   ifconfig
   ip addr
   arp


   ```


**********
Here are some basic cisco router verification commands that you can use to check the status and configuration of your router and switch:

1. **Show Interfaces:**
   ```
   show interfaces
   ```

   This command displays the status and statistics for all interfaces on the router.

2. **Show IP Interface Brief:**
   ```
   show ip interface brief
   ```

   This command provides a brief summary of the status and configuration of all interfaces, along with their IP addresses.

3. **Show Running-Config:**
   ```
   show running-config
   ```

   This command displays the current running configuration of the router. You can use this to view the entire configuration, including interfaces, routing protocols, and more.

4. **Show Version:**
   ```
   show version
   ```

   This command provides information about the router hardware, software version, and the configuration register.

5. **Show IP Route:**
   ```
   show ip route
   ```

   This command displays the routing table, showing the current routing information and how the router will forward packets.

6. **Show ARP:**
   ```
   show arp
   ```

   This command shows the ARP (Address Resolution Protocol) table, displaying the mapping between IP addresses and MAC addresses.

7. **Show CDP Neighbors:**
   ```
   show cdp neighbors
   ```

   If Cisco Discovery Protocol (CDP) is enabled, this command displays information about directly connected Cisco devices.

8. **Show Interfaces Status:**
   ```
   show interfaces status
   ```

   This command provides a summary of the status and connectivity of all interfaces, including information on whether they are up or down.

9. **Show IP Protocols:**
   ```
   show ip protocols
   ```

   This command displays information about routing protocols running on the router, including their status and configuration.

10. **Show Access-Lists:**
    ```
    show access-lists
    ```

    This command shows the configured access lists on the router, including their rules and hit counts.

Remember that the specific commands and their output may vary depending on the router model and the IOS (Internetwork Operating System) version running on the device. Additionally, some commands may require privileged EXEC mode, which you can enter using the `enable` command.

