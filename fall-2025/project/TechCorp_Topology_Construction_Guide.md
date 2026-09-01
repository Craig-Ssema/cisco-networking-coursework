# TechCorp Network - Step-by-Step Topology Construction Guide
## Cisco Packet Tracer Implementation

---

# PART 1: SETTING UP THE WORKSPACE

## Step 1.1: Open Packet Tracer
1. Launch Cisco Packet Tracer
2. Click **File → New** to create a new project
3. Save immediately: **File → Save As → "CraigLastName_TechCorp_Network.pkt"**

## Step 1.2: Configure Workspace
1. At the bottom-left, ensure you're in **Logical** view (not Physical)
2. Use the zoom controls to set a comfortable zoom level (80-100% works well)
3. The workspace should be large enough to fit all devices comfortably

---

# PART 2: ADDING NETWORK DEVICES

## Step 2.1: Add Routers (2 Total)

### Router R1 (Core Router)
1. Click **Network Devices** (bottom-left panel)
2. Click **Routers** (router icon)
3. Find and click **2911** router
4. Click in the **CENTER** of the workspace to place it
5. Click on the router → **Config** tab → Change Display Name to **R1**

### Router R2 (Edge Router)  
1. With **2911** still selected, click **ABOVE** R1 to place R2
2. Click on router → **Config** tab → Change Display Name to **R2**
3. Position R2 directly above R1 with some space between them

### ISP Router (Optional - for testing)
1. Add another **2911** router
2. Place it at the **TOP** of your workspace (above R2)
3. Name it **ISP**

**Your layout so far (top to bottom):**
```
        [ISP]
          |
        [R2]
          |
        [R1]
```

---

## Step 2.2: Add Switches (3 Total)

### Switch SW1 (Distribution Switch)
1. Click **Network Devices** → **Switches**
2. Find and click **2960** switch
3. Click **BELOW** R1 to place SW1
4. Click on switch → **Config** tab → Change Display Name to **SW1**

### Switch SW2 (Access Switch - IT/HR)
1. With **2960** still selected, click **BELOW and to the LEFT** of SW1
2. Name it **SW2**

### Switch SW3 (Access Switch - Finance/Servers)
1. Click **BELOW and to the RIGHT** of SW1
2. Name it **SW3**

**Your layout so far:**
```
        [ISP]
          |
        [R2]
          |
        [R1]
          |
        [SW1]
        /    \
    [SW2]    [SW3]
```

---

## Step 2.3: Add Servers (3 Total)

1. Click **End Devices** (bottom-left panel)
2. Click **End Devices** subcategory
3. Find and click **Server** (or Server-PT)

### Web Server
1. Click **BELOW SW3** on the RIGHT side
2. Click server → **Config** tab → Change Display Name to **Web-Server**

### Email Server
1. Add another server to the **RIGHT** of Web-Server
2. Name it **Email-Server**

### FTP Server
1. Add another server to the **RIGHT** of Email-Server
2. Name it **FTP-Server**

---

## Step 2.4: Add PCs (6+ Total)

1. In **End Devices**, find **PC** (or PC-PT)

### IT Department PCs (VLAN 20)
1. Add 2 PCs **BELOW SW2** on the LEFT side
2. Name them **IT-PC1** and **IT-PC2**

### HR Department PCs (VLAN 30)
1. Add 2 PCs **BELOW SW2** on the RIGHT side (next to IT PCs)
2. Name them **HR-PC1** and **HR-PC2**

### Finance Department PCs (VLAN 40)
1. Add 2 PCs **BELOW SW3** on the LEFT side
2. Name them **Finance-PC1** and **Finance-PC2**

**Your complete layout:**
```
                    [ISP]
                      |
                    [R2]
                      |
                    [R1]
                      |
                    [SW1]
                   /      \
               [SW2]      [SW3]
              /    \      /    \
         [IT-PCs] [HR-PCs] [Fin-PCs] [Servers]
```

---

# PART 3: CABLING THE NETWORK

## Cable Types Reference
| Connection Type | Cable | Color in PT |
|----------------|-------|-------------|
| Router to Router | Crossover (or Auto) | Red dashed |
| Router to Switch | Straight-through | Black solid |
| Switch to Switch | Crossover (or Auto) | Red dashed |
| Switch to PC/Server | Straight-through | Black solid |

**TIP:** In modern Packet Tracer, you can use **Automatically Choose Connection Type** (lightning bolt icon) and it will select the correct cable.

## Step 3.1: Connect Routers

### ISP to R2
1. Click **Connections** (lightning bolt icon, bottom-left)
2. Click **Copper Cross-Over** (or use Auto)
3. Click **ISP** → Select **GigabitEthernet0/0**
4. Click **R2** → Select **GigabitEthernet0/1**

### R2 to R1
1. Click **R2** → Select **GigabitEthernet0/0**
2. Click **R1** → Select **GigabitEthernet0/1**

---

## Step 3.2: Connect R1 to SW1 (Trunk Link)

1. Select **Copper Straight-Through** cable
2. Click **R1** → Select **GigabitEthernet0/0**
3. Click **SW1** → Select **GigabitEthernet0/1**

---

## Step 3.3: Connect Switches (Trunk Links)

### SW1 to SW2
1. Select **Copper Cross-Over** (or Auto)
2. Click **SW1** → Select **GigabitEthernet0/2**
3. Click **SW2** → Select **GigabitEthernet0/1**

### SW1 to SW3
1. Click **SW1** → Select **FastEthernet0/1**
2. Click **SW3** → Select **FastEthernet0/1**

---

## Step 3.4: Connect End Devices to SW2

### IT Department PCs
| Device | Switch Port |
|--------|-------------|
| IT-PC1 | SW2 FastEthernet0/2 |
| IT-PC2 | SW2 FastEthernet0/3 |

1. Select **Copper Straight-Through** cable
2. Click **IT-PC1** → Select **FastEthernet0**
3. Click **SW2** → Select **FastEthernet0/2**
4. Repeat for IT-PC2 using **FastEthernet0/3**

### HR Department PCs
| Device | Switch Port |
|--------|-------------|
| HR-PC1 | SW2 FastEthernet0/11 |
| HR-PC2 | SW2 FastEthernet0/12 |

1. Click **HR-PC1** → Select **FastEthernet0**
2. Click **SW2** → Select **FastEthernet0/11**
3. Repeat for HR-PC2 using **FastEthernet0/12**

---

## Step 3.5: Connect End Devices to SW3

### Finance Department PCs
| Device | Switch Port |
|--------|-------------|
| Finance-PC1 | SW3 FastEthernet0/2 |
| Finance-PC2 | SW3 FastEthernet0/3 |

1. Click **Finance-PC1** → **FastEthernet0** → **SW3** → **FastEthernet0/2**
2. Click **Finance-PC2** → **FastEthernet0** → **SW3** → **FastEthernet0/3**

### Servers
| Device | Switch Port |
|--------|-------------|
| Web-Server | SW3 FastEthernet0/20 |
| Email-Server | SW3 FastEthernet0/21 |
| FTP-Server | SW3 FastEthernet0/22 |

1. Click **Web-Server** → **FastEthernet0** → **SW3** → **FastEthernet0/20**
2. Click **Email-Server** → **FastEthernet0** → **SW3** → **FastEthernet0/21**
3. Click **FTP-Server** → **FastEthernet0** → **SW3** → **FastEthernet0/22**

---

# PART 4: VERIFY YOUR TOPOLOGY

## Step 4.1: Check All Connections

After a few seconds, connection indicators should appear:
- **Green triangles** = Link is up (good!)
- **Orange triangles** = Link is initializing (wait)
- **Red triangles** = Link is down (problem!)

**Note:** Router-to-Switch links will stay orange/red until interfaces are configured with `no shutdown`.

## Step 4.2: Connection Summary Table

| From Device | From Port | To Device | To Port | Cable Type |
|-------------|-----------|-----------|---------|------------|
| ISP | G0/0 | R2 | G0/1 | Crossover |
| R2 | G0/0 | R1 | G0/1 | Crossover |
| R1 | G0/0 | SW1 | G0/1 | Straight |
| SW1 | G0/2 | SW2 | G0/1 | Crossover |
| SW1 | Fa0/1 | SW3 | Fa0/1 | Crossover |
| IT-PC1 | Fa0 | SW2 | Fa0/2 | Straight |
| IT-PC2 | Fa0 | SW2 | Fa0/3 | Straight |
| HR-PC1 | Fa0 | SW2 | Fa0/11 | Straight |
| HR-PC2 | Fa0 | SW2 | Fa0/12 | Straight |
| Finance-PC1 | Fa0 | SW3 | Fa0/2 | Straight |
| Finance-PC2 | Fa0 | SW3 | Fa0/3 | Straight |
| Web-Server | Fa0 | SW3 | Fa0/20 | Straight |
| Email-Server | Fa0 | SW3 | Fa0/21 | Straight |
| FTP-Server | Fa0 | SW3 | Fa0/22 | Straight |

---

# PART 5: CONFIGURE SERVER IP ADDRESSES (GUI)

Before CLI configuration, set up server IPs through the GUI.

## Step 5.1: Web Server Configuration

1. Click **Web-Server**
2. Go to **Desktop** tab → **IP Configuration**
3. Select **Static**
4. Enter:
   - IP Address: **172.16.50.10**
   - Subnet Mask: **255.255.255.0**
   - Default Gateway: **172.16.50.1**
   - DNS Server: **8.8.8.8**

## Step 5.2: Email Server Configuration

1. Click **Email-Server** → **Desktop** → **IP Configuration**
2. Enter:
   - IP Address: **172.16.50.20**
   - Subnet Mask: **255.255.255.0**
   - Default Gateway: **172.16.50.1**
   - DNS Server: **8.8.8.8**

## Step 5.3: FTP Server Configuration

1. Click **FTP-Server** → **Desktop** → **IP Configuration**
2. Enter:
   - IP Address: **172.16.50.30**
   - Subnet Mask: **255.255.255.0**
   - Default Gateway: **172.16.50.1**
   - DNS Server: **8.8.8.8**

## Step 5.4: ISP Router Loopback (for testing)

1. Click **ISP** → **CLI** tab
2. Enter commands:
```
enable
configure terminal
hostname ISP
interface GigabitEthernet0/0
  ip address 203.0.113.2 255.255.255.252
  no shutdown
interface Loopback0
  ip address 8.8.8.8 255.255.255.255
ip route 0.0.0.0 0.0.0.0 203.0.113.1
end
```

---

# PART 6: ENABLE SERVER SERVICES (GUI)

## Step 6.1: Configure HTTP on Web Server

1. Click **Web-Server** → **Services** tab → **HTTP**
2. Ensure **HTTP** and **HTTPS** are **ON**
3. Click on **index.html** to edit
4. Replace content with:
```html
<html>
<head><title>TechCorp Portal</title></head>
<body>
<h1>Welcome to TechCorp</h1>
<p>Internal web server - Network Project</p>
<p>Server IP: 172.16.50.10</p>
</body>
</html>
```
5. Click **Save**

## Step 6.2: Configure Email on Email Server

1. Click **Email-Server** → **Services** tab → **EMAIL**
2. Set **Domain Name**: **techcorp.local**
3. Add users by entering username and password, then clicking **+**:
   - User: **admin** | Password: **admin123**
   - User: **user1** | Password: **user123**
   - User: **user2** | Password: **user123**
4. Ensure **SMTP** and **POP3** are **ON**

## Step 6.3: Configure FTP on FTP Server

1. Click **FTP-Server** → **Services** tab → **FTP**
2. Ensure FTP Service is **ON**
3. Add a user:
   - Username: **ftpuser**
   - Password: **ftp123**
   - Check: **Write**, **Read**, **Delete**, **Rename**, **List**
4. Click **Add**

---

# PART 7: ARRANGE AND LABEL YOUR TOPOLOGY

## Step 7.1: Organize Device Positions

Arrange devices in a clean hierarchical layout:

```
Level 1 (Top):        [ISP]

Level 2:              [R2]

Level 3:              [R1]

Level 4:              [SW1]

Level 5:          [SW2]    [SW3]

Level 6:    [PCs]  [PCs]  [PCs]  [Servers]
            IT     HR     Finance
```

## Step 7.2: Add Labels/Notes (Optional but Professional)

1. Click **Place Note** tool (bottom panel, looks like a sticky note)
2. Add labels for each section:
   - "INTERNET" above ISP
   - "WAN" between routers
   - "VLAN 20 - IT Department" near IT PCs
   - "VLAN 30 - HR Department" near HR PCs
   - "VLAN 40 - Finance Department" near Finance PCs
   - "VLAN 50 - Server Farm" near servers

## Step 7.3: Add a Title Box

1. Use **Place Note** to add a title:
```
TechCorp Enterprise Network
Student: Craig [Last Name]
Course: COMP 3326
```

---

# PART 8: SAVE YOUR WORK

## Step 8.1: Save the Project
1. **File → Save** (or Ctrl+S)
2. File should be named: **CraigLastName_TechCorp_Network.pkt**

## Step 8.2: Take a Screenshot of Topology
1. Arrange the view to show all devices
2. Press **Print Screen** or use Snipping Tool
3. Save as **Topology_Screenshot.png** for your documentation

---

# WHAT'S NEXT?

Now that your physical topology is complete, proceed to:

1. **Phase 1**: Basic device configuration (hostnames, passwords)
2. **Phase 2**: VLAN configuration on switches
3. **Phase 3**: Router-on-a-Stick (subinterfaces)
4. **Phase 4**: DHCP configuration
5. **Phase 5**: Server service testing
6. **Phase 6**: Security (ACLs, Port Security, SSH)
7. **Phase 7**: NAT configuration

Use the **Quick Reference Commands** document to copy-paste configurations!

---

# TROUBLESHOOTING COMMON ISSUES

## Issue: Links showing red/down
**Solution**: Router interfaces are administratively down by default. Configure them with `no shutdown`.

## Issue: Wrong cable type selected
**Solution**: Delete the cable (click on it, press Delete), use **Auto Connect** to let Packet Tracer choose.

## Issue: Can't find a port
**Solution**: Some switches have limited ports. Use the **Physical** tab to add more modules if needed.

## Issue: Device not responding to CLI
**Solution**: Wait for device to boot (watch the power indicator), then access CLI.

## Issue: Accidentally deleted something
**Solution**: Use **Edit → Undo** (Ctrl+Z) immediately.

---

**Document Version:** 1.0  
**Last Updated:** [Current Date]
