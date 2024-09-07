# Cisco Packet Tracer Lab: Router Configuration & Ping Troubleshooting

## Objective
The objective of this lab is to troubleshoot connectivity issues between **PC1** and **PC2** by identifying and fixing misconfigurations on the routers in the network. You have successfully completed the lab when **PC1** can successfully ping **PC2**.

## Network Topology
![Network Topology](./path-to-image)

### Network Overview:
- **PC1**:
  - IP: `192.168.1.1`
  - Subnet: `255.255.255.0`
  - Connected to Switch 1 (SW1)

- **Router 1 (R1)**:
  - Interface G0/1: `192.168.1.254`
  - Interface G0/0: `192.168.12.1`

- **Router 2 (R2)**:
  - Interface G0/0: `192.168.12.2`
  - Interface G0/1: `192.168.13.1`

- **Router 3 (R3)**:
  - Interface G0/0: `192.168.13.2`
  - Interface G0/1: `192.168.3.254`

- **PC2**:
  - IP: `192.168.3.1`
  - Subnet: `255.255.255.0`
  - Connected to Switch 2 (SW2)

## Problem Statement
Both **PC1** and **PC2** are unable to ping each other. There are misconfigurations on the routers that prevent successful communication. Your task is to locate and fix these misconfigurations so that both PCs can communicate successfully via ICMP ping.

## Steps for Troubleshooting

1. **Verify IP Addressing**:  
   - Check the IP addressing on **PC1**, **PC2**, **Router 1 (R1)**, **Router 2 (R2)**, and **Router 3 (R3)** to ensure they match the given network design.
   - Make sure all devices are in the correct subnet and their default gateways are properly configured.

2. **Check Router Interfaces**:
   - Verify that the interfaces on **R1**, **R2**, and **R3** are up and properly assigned with the right IP addresses. Use the following commands:
     ```bash
     show ip interface brief
     ```
   - Confirm that all interfaces are up and configured correctly.

3. **Check Routing Tables**:
   - Use the following command to check the routing tables on **R1**, **R2**, and **R3**:
     ```bash
     show ip route
     ```
   - Verify that static routes or dynamic routing protocols are properly configured to ensure packets can be routed between the three subnets.

4. **Correct Misconfigurations**:
   - **R1**: Ensure there is a static route from **192.168.1.0/24** to **192.168.3.0/24** via **192.168.12.2**.
   - **R2**: Ensure there is a static route from **192.168.12.0/24** to **192.168.3.0/24** via **192.168.13.2** and from **192.168.3.0/24** to **192.168.1.0/24** via **192.168.12.1**.
   - **R3**: Ensure there is a static route from **192.168.3.0/24** to **192.168.1.0/24** via **192.168.13.1**.

5. **Ping Tests**:
   - After making the corrections, perform the following tests to ensure connectivity:
     - Ping **PC1** to **PC2**:
       ```bash
       ping 192.168.3.1
       ```
     - Ping **PC2** to **PC1**:
       ```bash
       ping 192.168.1.1
       ```

6. **Verify Success**:
   - Once **PC1** and **PC2** can successfully ping each other, the lab is complete.

## Conclusion
This lab exercise demonstrates basic troubleshooting steps to resolve routing misconfigurations and ensure proper communication between devices in different subnets. By following the steps outlined, you will be able to successfully enable PC1 and PC2 to communicate using ICMP ping.
## Acknowledgements


Special thanks to **Jeremy's IT Lab** for providing valuable resources and tutorials that greatly contributed to the completion of this exercise. His in-depth explanations and practical demonstrations have been instrumental in enhancing my understanding of Cisco networking concepts and the effective use of Packet Tracer.

For more information and additional resources, visit [Jeremy's IT Lab](https://jeremysitlab.com/) and check out his YouTube for the full course, [Jeremy's IT Lab Free CCNA 200-301 | Complete Course](https://www.youtube.com/playlist?list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ)
