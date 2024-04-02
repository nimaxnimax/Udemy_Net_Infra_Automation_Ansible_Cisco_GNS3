
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

How to Check Interfaces Connected to Routers or Switches - Ansible YAML

```bash

ansible-playbook -i ansible_hosts cdp.yml
ansible-playbook -i ansible_hosts cdp_check_sw1_sw2_sw3_example.yml

```

**********

L2 and L3 Switch Trunk Interface Config - Ansible YAML

```bash

ansible-playbook -i ansible_hosts interface_trunk_config_switches.yml
ansible-playbook -i ansible_hosts interface_trunk_check.yml

```

**********

Ansible and Ping Commands - How to Check IP Connectivity and MAC TAble

```bash

ansible-playbook -i ansible_hosts check_ping_sw1to3.yml
ansible-playbook -i ansible_hosts mac_address_table_3725_check.yml

```

**********

Spanning Tree Protocol (STP) is a network protocol used to prevent loops in bridged or switched networks. Loops can occur when there are redundant paths between network devices, and if not properly managed, they can cause network congestion and even network outages.

STP works by allowing network switches to exchange information about their connections and then collectively decide which paths should be active and which should be blocked to ensure there is only one active path between any two network devices. This active path forms a loop-free topology.

Here are some key points about STP and its importance:

1. **Loop Prevention**: The primary function of STP is to prevent loops in the network. Loops occur when there are multiple paths between switches, and packets end up being forwarded endlessly between them. STP ensures that only one active path exists between any two network devices, effectively eliminating loops.

2. **Redundancy**: While loops are undesirable, having redundant links in a network can be beneficial for fault tolerance and load balancing. STP allows for the creation of a loop-free topology while still utilizing redundant links. If the active path fails, STP reconverges to use an alternate path, ensuring network reliability.

3. **Automatic Configuration**: STP operates autonomously once configured. It dynamically determines the best paths and adjusts the network topology in response to changes such as link failures or additions, without requiring manual intervention.

4. **Compatibility**: STP is a widely adopted standard and is supported by most network switches and routers. This makes it a versatile solution for ensuring loop-free operation in Ethernet networks.

5. **Variants and Enhancements**: Over time, various enhancements and extensions to STP have been developed to improve its efficiency and convergence time. These include Rapid Spanning Tree Protocol (RSTP) and Multiple Spanning Tree Protocol (MSTP), which offer faster convergence and better support for VLANs, respectively.

STP is crucial for maintaining a stable and efficient network infrastructure by preventing loops and ensuring reliable communication between network devices. Its automatic operation and widespread support make it an essential protocol in modern Ethernet networks.

**********

Spanning Tree Protocol (STP) and Rapid Spanning Tree Protocol (RSTP) are both network protocols designed to prevent loops in bridged or switched networks, but they differ in their operation and features. Here's a comparison between the two:

1. **Convergence Time**:
   - STP: Traditional STP typically has a convergence time of around 30 to 50 seconds. This is because it goes through multiple stages (blocking, listening, learning, and forwarding) before determining the optimal topology.
   - RSTP: RSTP significantly improves convergence time compared to STP. It typically converges in just a few seconds (usually less than 5 seconds) by using techniques like port roles (e.g., discarding, learning, forwarding) and link types (e.g., point-to-point, edge).

2. **Topology Changes**:
   - STP: In STP, topology changes are detected by exchanging Bridge Protocol Data Units (BPDUs) between switches. Upon detecting a change, STP goes through the entire convergence process, leading to longer reconvergence times.
   - RSTP: RSTP reduces the impact of topology changes by immediately transitioning ports to the forwarding state when a topology change occurs. This rapid transition helps to minimize the disruption caused by network changes.

3. **Port States**:
   - STP: STP has five port states: blocking, listening, learning, forwarding, and disabled. Ports go through these states sequentially during the convergence process.
   - RSTP: RSTP simplifies the port states to three: discarding (similar to blocking in STP), learning, and forwarding. This simplification helps in faster convergence by reducing the number of states a port goes through.

4. **Backward Compatibility**:
   - STP: Traditional STP is backward compatible with older switches that only support STP. However, it does not take advantage of the rapid convergence features of RSTP.
   - RSTP: RSTP is backward compatible with STP, allowing RSTP-enabled switches to interoperate with legacy STP switches. RSTP switches can also operate in a compatibility mode where they function as STP switches when communicating with legacy devices.

5. **Protocol Overhead**:
   - STP: Traditional STP has relatively high protocol overhead due to the periodic exchange of BPDUs and the longer convergence time.
   - RSTP: RSTP reduces protocol overhead by minimizing the frequency of BPDU exchanges and by quickly converging to the optimal topology.

RSTP offers significant improvements over traditional STP in terms of convergence time, handling topology changes, and reducing protocol overhead. Its rapid convergence makes it more suitable for modern networks where fast reconvergence is essential for maintaining network stability and minimizing downtime.

**********

A broadcast storm is a phenomenon that occurs in a computer network when a large volume of broadcast or multicast messages is generated by one or more network devices, leading to a significant increase in network traffic and potentially causing network congestion or even network failure. Here are some advantages, disadvantages, and the relationship between broadcast storms and STP:

Advantages:

1. **Redundancy Testing**: Broadcast storms can inadvertently reveal weaknesses or inefficiencies in network redundancy configurations. By flooding the network with broadcasts, potential issues with redundant paths and loops can be uncovered, allowing network administrators to address them proactively.

2. **Network Troubleshooting**: In some cases, broadcast storms can help pinpoint faulty network equipment or misconfigurations. When a broadcast storm occurs, it can quickly draw attention to the affected network segment, aiding in the troubleshooting process.

Disadvantages:

1. **Network Congestion**: One of the most significant drawbacks of broadcast storms is the resulting network congestion. The excessive volume of broadcast traffic can saturate network links and overwhelm network devices, leading to degraded performance or complete network outage.

2. **Packet Loss and Latency**: As network devices become inundated with broadcast traffic, they may struggle to process legitimate data packets, resulting in increased packet loss and latency for normal network traffic.

3. **Service Disruption**: In extreme cases, a severe broadcast storm can bring down an entire network, causing widespread service disruption and downtime for users and applications.

Relation to STP:

Spanning Tree Protocol (STP) plays a crucial role in mitigating the risks associated with broadcast storms. By actively monitoring the network topology and selectively blocking redundant paths, STP helps prevent the formation of network loops, which are often a precursor to broadcast storms.

Here's how STP helps address broadcast storms:

1. **Loop Prevention**: STP ensures that redundant paths in the network are identified and blocked to prevent the formation of loops. By maintaining a loop-free topology, STP reduces the likelihood of broadcast storms occurring due to looping broadcast traffic.

2. **Topology Changes**: In the event of a network topology change, such as a link failure or addition, STP rapidly reconverges to adapt to the new topology and prevent the propagation of broadcast storms. This rapid reconvergence helps minimize the duration and impact of potential broadcast storms on the network.

While broadcast storms can pose significant challenges to network stability and performance, STP serves as a critical mechanism for mitigating the risks associated with these disruptive events and maintaining a resilient and efficient network infrastructure.

**********

When redundant LANs (Local Area Networks) are deployed without using Spanning Tree Protocol (STP) or a similar loop prevention mechanism, several classes of problems can arise, which can severely impact network performance, stability, and reliability. Here are three main classes of problems caused by not using STP in redundant LANs:

1. **Broadcast Storms**:
   - **Description**: A broadcast storm occurs when broadcast or multicast packets flood the network, often due to network loops. Without STP to prevent loops, broadcast packets can endlessly circulate between network devices, exponentially increasing traffic volume and consuming network resources.
   - **Impact**: Broadcast storms lead to network congestion, packet collisions, increased latency, and degraded performance for all network traffic. They can ultimately result in network downtime or severe service disruptions.
   - **Example**: In a redundant LAN configuration without STP, if a broadcast packet is sent out from a device and encounters multiple redundant paths, it can loop back to the originating device, initiating a broadcast storm.

2. **MAC Address Table Instability**:
   - **Description**: In a redundant LAN environment without STP, network switches may encounter inconsistent or conflicting MAC address tables due to the presence of network loops. Switches learn MAC addresses associated with specific ports, but in the presence of loops, they may receive MAC addresses from multiple ports simultaneously, leading to ambiguity and instability.
   - **Impact**: MAC address table instability can cause packet forwarding errors, resulting in misdirected traffic, packet drops, or even network loops. This instability can disrupt normal network operations and compromise network performance.
   - **Example**: Without STP, if a switch receives frames with the same source MAC address from multiple ports simultaneously due to a loop, it may have difficulty determining the correct egress port for forwarding subsequent frames to that MAC address.

3. **Switching Loops and Packet Duplication**:
   - **Description**: In the absence of STP, redundant LAN configurations can create switching loops where packets circulate endlessly between switches. These loops cause packets to be duplicated and forwarded repeatedly, leading to inefficient use of network bandwidth and resources.
   - **Impact**: Switching loops result in increased network traffic, congestion, and degradation of network performance. Duplicate packets consume network bandwidth and can overwhelm network devices, potentially causing network instability or failure.
   - **Example**: If two switches are interconnected via multiple redundant links without STP, a packet sent from one switch may traverse both links repeatedly, resulting in packet duplication and wasting network resources.

Not using STP in redundant LANs can lead to various problems such as broadcast storms, MAC address table instability, and switching loops, all of which can degrade network performance, stability, and reliability. Implementing STP or a similar loop prevention mechanism is essential for maintaining a robust and efficient network infrastructure.

**********

Spanning Tree Protocol (STP) and Rapid Spanning Tree Protocol (RSTP) are network protocols designed to prevent loops in bridged or switched networks. One of the fundamental actions performed by STP/RSTP to prevent loops is to block specific ports in the network topology. This action helps break potential loops and ensures the creation of a loop-free network topology. Here's how STP/RSTP accomplishes this:

1. **Loop Detection and Prevention**:
   - When switches are interconnected to form a network, there is a possibility of creating loops, especially in redundant network designs where multiple paths exist between switches.
   - STP/RSTP algorithms run on the switches to detect and mitigate these loops. They achieve this by collectively electing a root bridge (the switch serving as the root of the spanning tree) and selectively blocking ports to prevent loops.

2. **Root Bridge Election**:
   - The first step in loop prevention is to elect a root bridge. Each switch in the network compares the Bridge ID (BID), which consists of a priority value and a MAC address, of all the switches it knows about. The switch with the lowest BID becomes the root bridge.
   - All ports on the root bridge remain in the forwarding state because it serves as the reference point for the spanning tree topology.

3. **Designated and Non-Designated Ports**:
   - After electing the root bridge, each non-root switch selects one of its ports as the root port (the port through which it has the shortest path to the root bridge).
   - The remaining ports on each switch are designated ports, which are responsible for forwarding traffic toward the root bridge.
   - Any ports that are not root ports or designated ports are considered non-designated ports.

4. **Blocking Ports**:
   - STP/RSTP determines additional ports that need to be blocked to eliminate loops in the network topology. These ports are typically those that would create a loop if left in the forwarding state.
   - Blocking a port effectively disables it from forwarding traffic, ensuring that loops cannot form.
   - The blocked ports remain in a state known as the "blocking" or "discarding" state. While in this state, they still listen to BPDUs (Bridge Protocol Data Units) to monitor the network topology and quickly transition to forwarding if necessary due to a topology change.

5. **Adapting to Topology Changes**:
   - STP/RSTP continuously monitors the network topology for changes, such as link failures or additions. When a change occurs, the protocol quickly recalculates the spanning tree and adjusts port states accordingly to maintain a loop-free topology.

STP/RSTP blocks specific ports in the network to break potential loops and ensure the creation of a loop-free spanning tree topology. By selectively blocking ports and continuously adapting to changes in the network, STP/RSTP helps maintain network stability and prevent the adverse effects of loops, such as broadcast storms and network congestion.

**********

Spanning Tree Protocol (STP) is a network protocol used to prevent loops in bridged or switched Ethernet networks. Here's how STP works and the port states associated with it:

1. **Root Bridge Election**:
   - Every switch participating in STP elections initially thinks itself as the root bridge. The process of root bridge election involves comparing Bridge IDs (BIDs), which consist of a priority value and a MAC address. The switch with the lowest BID becomes the root bridge.
   - All other switches in the network then determine their shortest path to the root bridge.

2. **Port States**:
   - **Root Bridge Ports**:
     - Root ports are the ports on non-root bridges that have the shortest path to the root bridge. These ports are in the forwarding state, allowing traffic to flow towards the root bridge.
     - The root bridge itself has all of its ports in the forwarding state because it serves as the reference point for the spanning tree topology.

   - **Non-Root Bridge Ports**:
     - Non-root bridges have ports that are either designated ports or blocked ports.
     - Designated ports are ports on non-root bridges that have the lowest path cost to the root bridge for a particular segment. They are in the forwarding state, forwarding traffic towards the root bridge.
     - Blocked ports are ports that are not designated ports or root ports. These ports are put into a blocking state, effectively blocking any traffic from being forwarded through them. This prevents loops in the network topology.

   - **Ports Connected to End Devices**:
     - Ports connected to end devices (e.g., computers, servers) are typically designated ports because they provide the shortest path to the root bridge for those devices. These ports are in the forwarding state, allowing end device traffic to reach the rest of the network.

3. **Transitioning Between Port States**:
   - Port states transition based on the receipt of Bridge Protocol Data Units (BPDUs) and changes in the network topology.
   - Initially, ports go through the blocking state, then move to the listening state, followed by the learning state, and finally reach the forwarding state.
   - When topology changes occur (e.g., link failure, link recovery), STP reconverges, recalculates the spanning tree, and adjusts port states accordingly to maintain a loop-free topology.

STP works by electing a root bridge and selecting ports on switches to be in forwarding or blocking states based on their role in the spanning tree topology. This process ensures that a loop-free topology is maintained, preventing broadcast storms and other adverse effects of network loops.

**********

BPDU stands for Bridge Protocol Data Unit. It is a type of frame used by Spanning Tree Protocol (STP) and its variants (such as Rapid Spanning Tree Protocol, RSTP) for communication between network switches to exchange information about the spanning tree topology. BPDUs contain various parameters and configuration details that switches use to participate in the spanning tree algorithm and maintain a loop-free network topology.

Here's some information about BPDUs and the timers associated with them:

1. **Content of BPDUs**:
   - BID (Bridge ID): This uniquely identifies the switch sending the BPDU and consists of a priority value and the MAC address of the switch.
   - Root Bridge ID: Identifies the root bridge of the spanning tree.
   - Path Cost: Represents the cumulative cost from the sending switch to the root bridge.
   - Port ID: Identifies the port through which the BPDU is being sent.
   - Port Role: Indicates the role of the port in the spanning tree topology (root port, designated port, or blocked port).
   - Message Age: Indicates how long the BPDU has been circulating in the network.
   - Hello Time: Specifies the interval at which BPDUs are sent.
   - Forward Delay: Specifies the time a port remains in the listening and learning states before transitioning to the forwarding state.
   - Max Age: Specifies the maximum time a switch will wait without receiving a BPDU before considering the root bridge lost.

2. **Timers Associated with BPDUs**:
   - **Hello Time**: This timer determines the interval between the transmission of BPDUs by a switch. It is typically 2 seconds for STP and 1 second for RSTP. Shorter hello times allow for faster detection of network topology changes.
   - **Forward Delay**: This timer defines the time a port spends in the listening and learning states before transitioning to the forwarding state. It is typically 15 seconds for STP and 4 seconds for RSTP. Shorter forward delay times reduce the convergence time of the spanning tree.
   - **Max Age**: This timer specifies the maximum age allowed for a BPDU before it is considered stale. It is typically 20 seconds for STP and 6 seconds for RSTP. If a switch does not receive BPDUs within the max age, it assumes that the root bridge has failed, and it initiates a topology change.

BPDUs are crucial for switches to exchange information and participate in the spanning tree algorithm effectively. They allow switches to determine the root bridge, calculate the shortest path to the root, and select ports for forwarding or blocking to ensure a loop-free topology.

**********

Here are some important notes about the root bridge election process in Spanning Tree Protocol (STP):

1. **Priority and MAC Address**: The root bridge is elected based on a combination of the bridge priority and the MAC address. The bridge priority is a configurable value (ranging from 0 to 65,535) assigned to each switch. By default, all switches have a priority of 32,768. If the priorities are equal, the switch with the lowest MAC address becomes the root bridge.

2. **Lowest Bridge ID**: The combination of bridge priority and MAC address forms the Bridge ID (BID). The switch with the lowest BID becomes the root bridge. The root bridge is the central point of the spanning tree and serves as the reference point for all other switches in the network.

3. **Priority Preemption**: Bridge priority can be manually configured to influence the root bridge election process. Lowering the priority of a switch increases its chances of becoming the root bridge. Priority preemption allows for administrative control over the root bridge selection process.

4. **Topology Stability**: The root bridge election process is critical for the stability and efficiency of the spanning tree topology. A stable root bridge ensures consistent path selection and optimal traffic flow throughout the network.

5. **Convergence Time**: The root bridge election process occurs initially when switches are powered on or connected to the network. Subsequent changes in the network topology, such as link failures or additions, trigger a rapid reconvergence process to re-elect the root bridge and update the spanning tree accordingly.

6. **Network Stability**: The root bridge is responsible for determining the shortest path to all other switches in the network. By minimizing the path cost to the root bridge, STP ensures a loop-free topology, preventing broadcast storms and other network issues caused by loops.

7. **Bridge ID Propagation**: During the root bridge election process, switches exchange Bridge Protocol Data Units (BPDUs) containing their BIDs. These BPDUs propagate throughout the network, allowing switches to compare BIDs and determine the root bridge.

Understanding the root bridge election process is essential for network administrators to design and maintain stable and efficient spanning tree topologies. It ensures proper traffic distribution and fault tolerance in Ethernet networks.

**********

Root ports are crucial components in Spanning Tree Protocol (STP) that determine the shortest path from a non-root bridge to the root bridge within a network topology. Understanding root ports and their associated root paths is essential for optimizing network performance and ensuring a loop-free spanning tree topology. Here are some important points about root ports and root paths:

1. **Root Port Selection**:
   - Each non-root bridge in the network selects one of its ports as the root port. The root port is the port that offers the shortest path to the root bridge in terms of cumulative path cost.
   - Path cost is calculated based on the sum of the costs associated with traversing each link between the non-root bridge and the root bridge. Lower path costs represent shorter and more efficient paths.

2. **Optimal Path to Root Bridge**:
   - The root port is crucial for ensuring that traffic from the non-root bridge reaches the root bridge along the most direct and efficient path. By selecting the root port, switches can minimize latency, reduce network congestion, and optimize traffic flow throughout the network.

3. **Path Cost Calculation**:
   - Path cost is determined by the speed of the links between switches. Faster links have lower costs, while slower links have higher costs. For example, a Gigabit Ethernet link typically has a lower path cost than a Fast Ethernet link.
   - The STP algorithm uses path cost to compare alternative paths to the root bridge and selects the path with the lowest cumulative cost as the root port.

4. **Adapting to Topology Changes**:
   - If the network topology changes, such as a link failure or addition, switches may need to reevaluate their root port selection. The STP algorithm reconverges to recalibrate the spanning tree topology and adjust root port assignments as necessary to maintain optimal connectivity.

5. **Loop Prevention**:
   - Root ports play a crucial role in preventing loops in the network topology. By ensuring that each non-root bridge has a designated path to the root bridge, STP constructs a loop-free spanning tree, eliminating the risk of broadcast storms and other network disruptions caused by loops.

Root ports and their associated root paths are essential for establishing optimal connectivity and maintaining a loop-free spanning tree topology in Ethernet networks. By selecting the shortest path to the root bridge, root ports help minimize latency, optimize traffic flow, and ensure network stability and reliability.

**********

Spanning Tree Protocol (STP) uses a cost metric to determine the most efficient path from each switch to the root bridge within a network topology. The cost of a path is calculated based on the speed of the links (interfaces) between switches. Here's how STP costs are calculated and some important points about interface costs:

1. **Link Speed and Cost**:
   - The cost of a path is inversely proportional to the speed of the link. Faster links have lower costs, while slower links have higher costs.
   - The cost of a path is calculated as a function of the link speed, typically measured in Mbps (megabits per second). The formula for calculating the cost is: \( \text{Cost} = 10^{8} \div \text{Link Speed in Mbps} \).
   - For example, a Fast Ethernet link (100 Mbps) has a cost of \( 10^{8} \div 100 = 1000 \), while a Gigabit Ethernet link (1000 Mbps) has a cost of \( 10^{8} \div 1000 = 100 \).

2. **Standard Interface Costs**:
   - STP defines standard interface costs for different link speeds to ensure interoperability and consistency across network devices.
   - The IEEE 802.1D standard specifies the following interface costs:
     - 10 Mbps (Ethernet): Cost = 10,000
     - 100 Mbps (Fast Ethernet): Cost = 1,000
     - 1 Gbps (Gigabit Ethernet): Cost = 100
     - 10 Gbps (10 Gigabit Ethernet): Cost = 10
     - 40 Gbps (40 Gigabit Ethernet): Cost = 4
     - 100 Gbps (100 Gigabit Ethernet): Cost = 2
     - 1 Tbps (1 Terabit Ethernet): Cost = 1

3. **Custom Interface Costs**:
   - Network administrators have the flexibility to manually adjust interface costs to prioritize certain paths or accommodate specific network requirements.
   - By modifying interface costs, administrators can influence the spanning tree topology and control the path selection process.

4. **Path Cost Calculation**:
   - The path cost is the sum of the costs associated with traversing each link along the path from a switch to the root bridge.
   - When multiple paths exist between switches, STP selects the path with the lowest cumulative cost as the preferred path to the root bridge.
   - The goal is to establish a loop-free topology while optimizing network performance and resource utilization.

Understanding STP costs and interface costs is essential for network administrators to design and maintain efficient spanning tree topologies. By carefully managing interface costs, administrators can control path selection and ensure optimal connectivity within the network.

**********

Spanning Tree Protocol (STP) and Rapid Spanning Tree Protocol (RSTP) use timers to control various aspects of the spanning tree operation, including convergence time and port roles. Here's an overview of STP timers, convergence time, and a comparison of RSTP port roles with STP:

1. **STP Timers**:

   a. **Hello Time**: Determines the interval at which BPDUs (Bridge Protocol Data Units) are sent between switches. The default hello time for STP is 2 seconds. BPDUs are used for neighbor discovery and to maintain connectivity within the spanning tree.

   b. **Forward Delay**: Specifies the time a port remains in the listening and learning states before transitioning to the forwarding state. The default forward delay for STP is 15 seconds. During this time, the switch learns MAC addresses and populates its forwarding table.

   c. **Max Age**: Specifies the maximum time a switch will wait without receiving a BPDU before considering the root bridge lost. The default max age for STP is 20 seconds. If a switch does not receive BPDUs within the max age, it assumes that the root bridge has failed and initiates a topology change.

2. **Convergence Time**:
   
   - Convergence time refers to the time it takes for the spanning tree topology to stabilize after a topology change, such as a link failure or recovery.
   
   - STP convergence time is relatively slow, typically taking 30 to 50 seconds to reconverge after a topology change. This slow convergence time is due to the sequential nature of the STP algorithm, which involves multiple phases (blocking, listening, learning, and forwarding) before reaching a stable topology.
   
   - RSTP significantly improves convergence time compared to STP. RSTP typically converges in just a few seconds (usually less than 5 seconds) by using techniques like port roles and link types to quickly adapt to topology changes.

3. **Comparison of RSTP Port Roles with STP**:

   a. **Root Port**:
      - In STP, the root port is the port on a non-root bridge that offers the shortest path to the root bridge.
      - In RSTP, the root port serves the same function but with faster convergence due to the simplified port roles and faster transition times.

   b. **Designated Port**:
      - Designated ports are ports on switches that have been selected as the designated forwarder for a particular segment.
      - Both STP and RSTP use designated ports to forward traffic towards the root bridge. RSTP typically converges faster due to its rapid transition times.

   c. **Blocked Port**:
      - Blocked ports are ports that are not root ports or designated ports. They are put into a blocking state to prevent loops in the network topology.
      - RSTP uses a similar concept of blocked ports for loop prevention, but it converges faster than STP due to its improved port roles and faster transition times.

RSTP improves upon STP by reducing convergence time through faster transition times and simplified port roles. This improvement enhances network efficiency and responsiveness to topology changes, making RSTP a preferred choice for modern Ethernet networks.

**********

Rapid Spanning Tree Protocol (RSTP) introduces the concept of link types or port types to facilitate faster convergence and better support for modern network environments. RSTP defines three main port types, each with its specific behavior and role in the spanning tree topology:

1. **Root Port (RP)**:
   - The Root Port is the port on a non-root bridge that provides the shortest path to the root bridge. It is responsible for forwarding traffic towards the root bridge.
   - RSTP rapidly selects the Root Port based on path costs, allowing for faster convergence compared to STP.

2. **Designated Port (DP)**:
   - Designated Ports are selected on each network segment to forward traffic towards the root bridge. They are responsible for aggregating traffic from multiple switches and ensuring efficient communication within the spanning tree topology.
   - RSTP ensures rapid selection of Designated Ports, reducing convergence time and optimizing network performance.

3. **Alternate Port (AP)**:
   - Alternate Ports serve as backup paths to the Root Port on a non-root bridge. They are placed in a discarding state but are ready to transition to the forwarding state if the Root Port fails.
   - RSTP ensures that Alternate Ports are quickly activated in case of a Root Port failure, providing fast convergence and fault tolerance.

4. **Backup Port (BP)**:
   - Backup Ports are similar to Alternate Ports and serve as backup paths to Designated Ports on a network segment. They are placed in a discarding state but can quickly transition to the forwarding state if the Designated Port fails.
   - RSTP ensures rapid activation of Backup Ports to maintain network connectivity and minimize downtime in the event of a Designated Port failure.

5. **Edge Port (EP)**:
   - Edge Ports are ports that connect to end devices, such as computers or servers, rather than to other switches. They are configured as point-to-point links and do not participate in the spanning tree topology.
   - RSTP rapidly identifies Edge Ports and places them in the forwarding state immediately, bypassing the listening and learning states. This feature reduces latency for end devices and enhances network performance.

By introducing these port types, RSTP improves upon the original STP by providing faster convergence, better support for redundant links, and optimized performance for modern network environments. These port types play a crucial role in maintaining a stable and efficient spanning tree topology while minimizing network downtime and disruptions.

**********

How to Verify and Configure STP on Switches 3725 Platform

```bash

ansible-playbook -i ansible_hosts stp_summary_check.yml
ansible-playbook -i ansible_hosts stp_vlan_check_c3725.yml
ansible-playbook -i ansible_hosts stp_cost_config_interface_per_vlan.yml

```

**********

Example vIOS VIRL Image (L2 and L3 Switch) Trunk STP Verification Config

```bash

ansible-playbook -i ansible_hosts cdp_check_sw4_sw5_sw6_example.yml
ansible-playbook -i ansible_hosts interface_ip_address_check_sw4to6.yml
ansible-playbook -i ansible_hosts interface_trunk_check_sw4to6.yml
ansible-playbook -i ansible_hosts interface_trunk_config_sw4to6.yml
ansible-playbook -i ansible_hosts stp_summary_check_sw4to6.yml
ansible-playbook -i ansible_hosts stp_mode_config_vios_switch.yml
ansible-playbook -i ansible_hosts check_ping_sw4to6.yml

```

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

