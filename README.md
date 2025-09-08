# static-routing
My Project on Static Routing
## Steps

### Setting Up and Configuration

This project aims to test whether both systems (PC0 and PC1) can communicate with each other, ensuring effective troubleshooting within the network and reliable packet delivery.

2. **Network Topology Setup**

   - This project was successfully completed using **CISCO Packet Tracer** as the simulation tool.

   - **Devices Needed:**
     - 2 PCs: **PC0**, **PC1**
     - 2 Routers: **Router1**, **Router2**
     - 2 Network Switches
     - 3 Networks: `10.1.1.0/24`, `10.1.2.0/24`, `10.1.3.0/24`

   - **Sample Topology:**
     ```
     [PC0]---[Switch1]---[Router1]---[Router2]---[Switch2]---[PC1]
                      |             |            |
                  10.1.1.0      10.1.2.0    10.1.3.0
     ```

3. **Configuring the PCs**
   - Assign IP addresses and gateways as follows:
     - **PC0**:  
       - IP address: `10.1.1.100`  
       - Subnet mask: `255.255.255.0`  
       - Default gateway: `10.1.1.1`
     - **PC1**:  
       - IP address: `10.1.3.100`  
       - Subnet mask: `255.255.255.0`  
       - Default gateway: `10.1.3.1`

4. **Configuring the Router Interfaces**

   - **Router1:**
     - `fa0/0`: `10.1.1.1` (connects to Switch1 and PC0)
     - `fa0/1`: `10.1.2.1` (connects to Router2)

   - **Router2:**
     - `fa0/0`: `10.1.2.254` (connects to Router1)
     - `fa0/1`: `10.1.3.1` (connects to Switch2 and PC1)

5. **Configuring Static Routes**

   - **Router1:**  
     To reach the `10.1.3.0/24` network, set the next hop as `10.1.2.254`:
     ```shell
     ip route 10.1.3.0 255.255.255.0 10.1.2.254
     ```

   - **Router2:**  
     To reach the `10.1.1.0/24` network, set the next hop as `10.1.2.1`:
     ```shell
     ip route 10.1.1.0 255.255.255.0 10.1.2.1
     ```

6. **Test Connectivity (Project Goal)**
   - Ping from **PC0** (`10.1.1.100`) to **PC1** (`10.1.3.100`).
   - Successful communication confirms that static routes are correctly configured and packet delivery between systems is effective.
   - This validates the troubleshooting process and connectivity within the network.

---
