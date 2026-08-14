# Azure Virtual Machine (VM)

## 1. What is Azure VM?

**Azure Virtual Machine (VM)** is a virtual server provided by Microsoft Azure.

It provides:

- CPU
- RAM
- Storage
- Networking

You can run **Windows or Linux** on an Azure VM and install applications/software on it.

### Simple Definition

> **Azure VM = Virtual Server in Azure Cloud**

---

# 2. Cloud Service Model

Azure VM is an:

## IaaS — Infrastructure as a Service

In IaaS:

- Azure manages the physical infrastructure.
- We manage the operating system and applications.

### Responsibility

| Azure Manages | We Manage |
|---|---|
| Physical Server | Operating System |
| Data Center | Applications |
| Physical Network | Software |
| Hypervisor | Users |
| Physical Storage | Configuration |

### Remember

```text
Azure VM
   ↓
IaaS
   ↓
Azure manages Infrastructure
   ↓
We manage OS + Application
```

---

# 3. Azure VM vs AWS EC2

| AWS | Azure |
|---|---|
| EC2 | Azure VM |
| VPC | VNet |
| Security Group | NSG |
| EBS | Managed Disk |
| Auto Scaling | VM Scale Sets |
| AMI | VM Image |
| Elastic IP | Public IP |
| CloudWatch | Azure Monitor |

---

# 4. Why Do Companies Use Azure VM?

Common use cases:

- Web servers
- Application servers
- Windows servers
- Linux servers
- Legacy applications
- Development/Test environments
- Custom software
- Applications requiring OS-level control

### Example

```text
Company
   ↓
Azure VM
   ↓
Windows Server
   ↓
IIS
   ↓
Website
```

---

# 5. Azure VM Important Components

When you create a VM, you commonly work with:

```text
                 Azure VM
                    |
       ┌────────────┼────────────┐
       ↓            ↓            ↓
    Compute       Storage      Network
       |            |            |
    CPU/RAM      OS Disk      NIC
                 Data Disk      |
                              VNet
                               |
                             Subnet
```

### Important Components

- VM
- VM Size
- VM Image
- OS Disk
- Data Disk
- NIC
- VNet
- Subnet
- Private IP
- Public IP
- NSG
- Managed Identity

---

# 6. VM Size

VM Size defines the resources available to the VM.

It determines things such as:

- vCPU
- RAM
- Network performance
- Disk capabilities

Example:

```text
VM Size
   ↓
4 vCPU
16 GB RAM
   ↓
Application
```

### Important

**VM Series = Family**

**VM Size = Specific configuration**

---

# 7. Important VM Series

Azure provides different VM series for different types of workloads.

You don't need to memorize every VM size/SKU. As a Cloud/DevOps Engineer, understand **why and when to choose each series**.

| VM Series | Main Purpose | When to Use | Example |
|---|---|---|---|
| **B-Series** | Burstable CPU | CPU usage is normally low but sometimes increases | Dev/Test, small websites |
| **D-Series** | General Purpose | Need a balanced amount of CPU and RAM | Web/App servers |
| **E-Series** | Memory Optimized | Application needs more RAM | Databases, caching, memory-heavy apps |
| **F-Series** | Compute Optimized | Application needs more CPU power | Batch processing, CPU-heavy applications |
| **L-Series** | Storage Optimized | Need high disk I/O and throughput | Large databases, data processing |
| **N-Series** | GPU Optimized | Need GPU processing | AI/ML, deep learning, rendering |
| **M-Series** | High Memory | Need very large amounts of RAM | Large databases, SAP workloads |

## B-Series — Burstable

- Designed for workloads where CPU usage is usually low but occasionally increases.
- Use for Dev/Test, small websites, and small application servers.
- **B = Burstable**

```text
Normal CPU → 20%
     ↓
Occasional Spike → 80%
     ↓
B-Series can be suitable
```

## D-Series — General Purpose

- Balanced CPU, RAM, storage and networking.
- Use for web servers, application servers, enterprise applications, and Dev/Test.
- **D = General Purpose**

```text
Web Server
     ↓
D-Series VM
     ↓
Website/Application
```

## E-Series — Memory Optimized

- Provides more RAM compared with general-purpose VMs.
- Use for databases, caching, in-memory processing, and analytics.
- **E = Extra Memory**

```text
Application
     ↓
Needs Large RAM
     ↓
E-Series VM
```

## F-Series — Compute Optimized

- Provides a higher CPU-to-memory ratio for compute-intensive workloads.
- Use for batch processing, data processing, scientific calculations, and CPU-intensive applications.
- **F = CPU / Compute Focused**

```text
CPU Usage
   ↓
Very High
   ↓
F-Series
```

## L-Series — Storage Optimized

- Designed for workloads requiring high disk I/O and storage performance.
- Use for high IOPS applications, large databases, big data, and storage-intensive workloads.
- **L = Storage Optimized**

```text
Application
     ↓
High Disk I/O
     ↓
L-Series VM
```

## N-Series — GPU Optimized

- Provides GPU resources for workloads that benefit from GPU processing.
- Use for AI/ML, deep learning, video processing, 3D rendering, and graphics-intensive applications.
- **N = GPU**

```text
AI / ML Application
       ↓
GPU Required
       ↓
N-Series VM
```

## M-Series — High Memory

- Designed for workloads requiring very large amounts of memory.
- Use for large databases, SAP workloads, large in-memory databases, and enterprise applications requiring huge RAM.
- **M = Massive Memory**

```text
Database
    ↓
Very Large RAM Required
    ↓
M-Series
```

## Easy VM Series Memory Trick

```text
B → Burstable
D → General Purpose
E → Extra Memory
F → Compute / CPU
L → Storage
N → GPU
M → Massive Memory
```

---

# 8. VM Image

A **VM Image** is a template used to create a VM.

It can contain:

- Operating System
- OS configuration
- Applications
- Custom settings

Examples:

- Windows Server
- Ubuntu
- Red Hat Enterprise Linux

### Simple Example

```text
VM Image
   ↓
Create VM
   ↓
Windows/Linux
   ↓
Application
```

---

# 9. Storage

Azure VM uses **Managed Disks** for VM storage.

Storage selection depends mainly on:

- Performance required
- IOPS required
- Throughput required
- Cost
- Workload type

## OS Disk

The **OS Disk** contains the operating system.

```text
OS Disk
   ↓
Windows / Linux
   ↓
VM Boots
```

### Use When:

- You need to store the operating system.
- VM needs to boot.

> **Every VM needs an OS disk.**

## Data Disk

A **Data Disk** is used to store application or business data separately from the OS.

```text
OS Disk
   ↓
Windows / Linux

Data Disk
   ↓
Application Data
Database Data
Website Files
```

### Use When:

- Application generates large data.
- Database needs separate storage.
- You want to separate OS and application data.
- You need additional storage capacity.

---

## Managed Disk Types

### 1. Standard HDD

**Use when:**

- Cost is more important than performance.
- Workload has low I/O requirements.
- Development/Test environments.
- Less frequently accessed data.

> **Standard HDD = Low Cost + Low Performance**

### 2. Standard SSD

**Use when:**

- You need better performance than HDD.
- Application has moderate I/O requirements.
- Development/Test workloads.
- General-purpose workloads where high performance is not required.

> **Standard SSD = Balanced Cost + Performance**

### 3. Premium SSD

**Use when:**

- Application requires high disk performance.
- Production workloads.
- Databases.
- High IOPS applications.
- Applications where disk latency is important.

> **Premium SSD = High Performance**

### 4. Premium SSD v2

**Use when:**

- You need high performance.
- You need more flexibility in configuring performance.
- Workload has demanding I/O requirements.
- Production databases and high-performance applications.

> **Premium SSD v2 = Flexible + High Performance**

### 5. Ultra Disk

**Use when:**

- Extremely high disk performance is required.
- Very high IOPS and throughput are required.
- Mission-critical databases.
- High-performance workloads.

> **Ultra Disk = Very High Performance**

## Storage Quick Comparison

| Disk Type | Performance | Cost | Best Use |
|---|---|---|---|
| **Standard HDD** | Low | Low | Low I/O, Dev/Test |
| **Standard SSD** | Medium | Medium | General workloads |
| **Premium SSD** | High | Higher | Production, databases |
| **Premium SSD v2** | High | Higher | Flexible high-performance workloads |
| **Ultra Disk** | Very High | High | Mission-critical, extreme I/O |

## Easy Storage Decision

```text
Low I/O + Low Cost
        ↓
Standard HDD

General Workload
        ↓
Standard SSD

High Performance
        ↓
Premium SSD

Flexible High Performance
        ↓
Premium SSD v2

Extreme IOPS / Throughput
        ↓
Ultra Disk
```

> **Important:** Actual disk capabilities and supported combinations depend on the Azure region, VM size, and workload requirements.

---

# 10. Azure VM Networking

Azure VM normally connects to an Azure **Virtual Network (VNet)**.

```text
Internet
   ↓
Public IP
   ↓
NIC
   ↓
Subnet
   ↓
VNet
   ↓
Azure VM
```

### Important Networking Terms

| Term | Meaning |
|---|---|
| VNet | Private network in Azure |
| Subnet | Smaller network inside VNet |
| NIC | Connects VM to network |
| Private IP | Internal IP |
| Public IP | Internet-facing IP |
| NSG | Controls network traffic |

---

# 11. NSG — Network Security Group

NSG controls inbound and outbound network traffic.

Example:

```text
Internet
   ↓
NSG
   ↓
Allow HTTPS 443
   ↓
VM
```

### Common Ports

| Port | Protocol | Use |
|---:|---|---|
| 22 | SSH | Linux |
| 80 | HTTP | Website |
| 443 | HTTPS | Secure Website |
| 3389 | RDP | Windows |

### Security Best Practice

Avoid exposing management ports such as:

```text
0.0.0.0/0 → RDP 3389
```

or:

```text
0.0.0.0/0 → SSH 22
```

unless there is a strong reason and appropriate controls.

Prefer:

- VPN
- Azure Bastion
- Restricted source IP
- Just-in-time access where applicable

---

# 12. RDP and SSH

## Windows VM

**RDP → Port 3389**

```text
Your Computer
     ↓
RDP
     ↓
Windows Azure VM
```

## Linux VM

**SSH → Port 22**

```text
Your Computer
     ↓
SSH
     ↓
Linux Azure VM
```

---

# 13. Availability

For production workloads, VM availability is important.

## Availability Set

Helps distribute VMs across:

- Fault domains
- Update domains

## Availability Zones

Separate physical locations within an Azure region.

```text
Azure Region
     |
 ┌───┼────────┐
 ↓   ↓        ↓
AZ1  AZ2      AZ3
 |    |        |
VM1  VM2      VM3
```

---

# 14. VM Scale Sets (VMSS)

VM Scale Sets allow you to manage multiple VMs and scale them based on demand.

```text
Low Traffic
    ↓
2 VMs

High Traffic
    ↓
5 VMs
```

### Use VMSS for:

- High availability
- Auto scaling
- Large applications
- Variable traffic

---

# 15. Load Balancer with VMs

Multiple VMs can be placed behind a Load Balancer.

```text
              Internet
                  ↓
          Azure Load Balancer
                  ↓
        ┌─────────┼─────────┐
        ↓         ↓         ↓
      VM-01     VM-02     VM-03
```

The Load Balancer distributes traffic between VMs.

---

# 16. Monitoring

Monitoring helps a Cloud/DevOps Engineer understand:

- Is the VM healthy?
- Is CPU too high?
- Is memory usage increasing?
- Is disk performance poor?
- Is the application failing?
- Are there errors in the logs?
- Should we create an alert?

## 1. Azure Monitor

**Meaning:** Main monitoring platform for Azure resources.

### Use When:

You want an **overall view of Azure resources and infrastructure**.

### Example

```text
Azure VM
   ↓
Azure Monitor
   ↓
CPU / Memory / Disk / Network
   ↓
Check VM Health
```

> **Azure Monitor = Overall monitoring**

---

## 2. VM Insights

**Meaning:** Detailed monitoring for Virtual Machines.

### Use When:

You need to analyze or troubleshoot **VM performance**.

It helps with:

- CPU
- Memory
- Disk
- Network
- Processes
- Dependencies

### Example

```text
Website is Slow
      ↓
VM Insights
      ↓
Check CPU / Memory / Disk / Network
      ↓
Find Performance Issue
```

> **VM Insights = Detailed VM performance**

---

## 3. Log Analytics

**Meaning:** Tool used to search and analyze logs using **Kusto Query Language (KQL)**.

### Use When:

You need to **investigate an issue using logs**.

You can analyze:

- VM logs
- System logs
- Application logs
- Security logs
- Performance data
- Azure activity data

### Example

```text
User Cannot Login
       ↓
Log Analytics
       ↓
Search Logs using KQL
       ↓
Find Error
       ↓
Troubleshoot
```

> **Log Analytics = Search and analyze logs**

---

## 4. Azure Alerts

**Meaning:** Sends notifications when a defined condition occurs.

### Use When:

You want Azure to **automatically notify you about a problem**.

### Example

```text
CPU > 80%
    ↓
Azure Alert
    ↓
Notification
    ↓
Cloud Engineer
```

Other examples:

```text
Disk Space Low
      ↓
Alert

VM Unavailable
      ↓
Alert

CPU Too High
      ↓
Alert
```

> **Azure Alerts = Notify me when something goes wrong**

---

## Monitoring Tools — Quick Comparison

| Tool | Main Purpose | When to Use |
|---|---|---|
| **Azure Monitor** | Overall monitoring | Monitor Azure resources |
| **VM Insights** | VM performance | Troubleshoot VM performance |
| **Log Analytics** | Log analysis | Investigate errors/logs |
| **Azure Alerts** | Notifications | Automatically notify about problems |

### Easy Way to Remember

> **Monitor → Insights → Logs → Alert**

- **Monitor** = What is happening?
- **Insights** = How is my VM performing?
- **Logs** = Why did it happen?
- **Alerts** = Tell me when something goes wrong.

---

# 17. VM Backup

Use **Azure Backup** to protect important VM workloads.

```text
Azure VM
   ↓
Azure Backup
   ↓
Recovery Point
   ↓
Restore when required
```

Define:

- Backup frequency
- Retention
- RPO
- RTO

---

# 18. VM Security

Important security practices:

- Use strong authentication.
- Prefer SSH keys for Linux.
- Don't expose RDP/SSH publicly unless necessary.
- Use NSGs.
- Keep OS patched.
- Use Microsoft Defender for Cloud where appropriate.
- Use Managed Identity.
- Follow least privilege.
- Monitor login activity.
- Backup important VMs.

---

# 19. Managed Identity

Managed Identity allows an Azure VM/application to access Azure resources without storing passwords or access keys in the application.

```text
Azure VM
   ↓
Managed Identity
   ↓
Azure Storage
```

> **Managed Identity = Secure access to Azure resources without storing credentials in code.**

---

# 20. VM Pricing

VM cost depends on:

- VM Size
- Region
- Operating System
- Usage
- Disk
- Public IP
- Other attached services

### Common Pricing Options

| Pricing | Use |
|---|---|
| Pay-As-You-Go | Flexible / short-term |
| Reservations | Long-term predictable workloads |
| Spot VM | Interruptible workloads at lower cost |

### Total Cost

```text
Compute
+
Managed Disk
+
Public IP
+
Backup
+
Network
+
Other Services
```

---

# 21. VM States

Common VM states include:

- Running
- Stopped
- Deallocated
- Starting
- Restarting

### Important

**Stopped ≠ Deallocated**

When a VM is deallocated, compute allocation is released, so compute billing generally stops. However, attached resources such as disks can still incur charges.

---

# 22. Azure VM vs App Service

| Azure VM | App Service |
|---|---|
| IaaS | PaaS |
| Manage OS | Azure manages platform |
| More control | Less infrastructure management |
| Install custom software | Application-focused |
| More administration | Easier to operate |

### Simple Rule

> **Need a complete server → Azure VM**

> **Need to host a web application without managing the server → App Service**

---

# 23. Azure VM vs AKS

| Azure VM | AKS |
|---|---|
| Virtual server | Kubernetes service |
| Run applications directly | Run containerized applications |
| OS management required | Kubernetes manages container workloads |
| Good for traditional applications | Good for microservices |

---

# 24. Azure VM vs Azure Functions

| Azure VM | Azure Functions |
|---|---|
| IaaS | Serverless |
| Full virtual server | No server management |
| OS control | No OS management |
| Long-running workloads | Event-driven workloads |
| More administration | Less administration |

---

# 25. Common Cloud/DevOps Tasks with Azure VM

## VM Management

- Create VM
- Start VM
- Stop VM
- Restart VM
- Deallocate VM
- Delete VM
- Resize VM
- Change disks

## Administration

- RDP/SSH access
- Install software
- Configure IIS/Nginx
- Create users
- Manage services
- Check CPU/RAM
- Check disk space
- Check logs

## Networking

- Configure VNet
- Configure Subnet
- Configure NSG
- Configure Public/Private IP
- Troubleshoot connectivity
- Configure Load Balancer

## Security

- Patch OS
- Configure NSG
- Restrict RDP/SSH
- Configure Managed Identity
- Monitor login activity
- Use Defender for Cloud

## Monitoring

- Azure Monitor
- Log Analytics
- Alerts
- VM Insights
- CPU monitoring
- Disk monitoring
- Network monitoring

## Automation

- Azure CLI
- PowerShell
- Terraform
- Ansible
- Automation
- Infrastructure as Code (IaC)

---

# 26. Useful Azure CLI Commands

## Login

```bash
az login
```

## List VMs

```bash
az vm list -o table
```

## Start VM

```bash
az vm start --resource-group <resource-group> --name <vm-name>
```

## Stop VM

```bash
az vm stop --resource-group <resource-group> --name <vm-name>
```

## Deallocate VM

```bash
az vm deallocate --resource-group <resource-group> --name <vm-name>
```

## Restart VM

```bash
az vm restart --resource-group <resource-group> --name <vm-name>
```

## Show VM Details

```bash
az vm show --resource-group <resource-group> --name <vm-name>
```

## List VM Sizes

```bash
az vm list-sizes --location <location> -o table
```

---

# 27. Troubleshooting Flow

When an Azure VM is not working:

```text
VM Issue
   ↓
Is VM Running?
   ↓
Check CPU / RAM
   ↓
Check Disk Space
   ↓
Check Network
   ↓
Check NSG
   ↓
Check Public / Private IP
   ↓
Check RDP / SSH
   ↓
Check OS
   ↓
Check Application
   ↓
Check Logs
   ↓
Check Azure Monitor
```

---

# 28. Most Important Things for Cloud/DevOps

## Must Know ⭐⭐⭐

- Azure VM
- IaaS
- VM Sizes
- VM Images
- Managed Disks
- VNet
- Subnet
- NIC
- Private/Public IP
- NSG
- RDP
- SSH
- Azure Monitor
- Log Analytics
- Alerts
- Backup
- VM Scale Sets
- Load Balancer

## DevOps Skills ⭐⭐⭐

- Azure CLI
- PowerShell
- Terraform
- Ansible
- Automation
- Monitoring
- Troubleshooting
- Security
- Cost Optimization

---

# 29. Simple Production Architecture

```text
                         Internet
                            ↓
                     Load Balancer
                            ↓
                    ┌───────┴───────┐
                    ↓               ↓
                  VM-01           VM-02
                    ↓               ↓
                    └───────┬───────┘
                            ↓
                           VNet
                            ↓
                          Subnet
                            ↓
                     NSG + NIC + IP
                            ↓
                     Managed Disks
```

---

# 30. Final Revision

```text
Azure VM
   ↓
IaaS
   ↓
Virtual Server
   ↓
Windows / Linux
   ↓
CPU + RAM + Storage
   ↓
VNet + Subnet + NIC
   ↓
NSG + IP
   ↓
RDP / SSH
   ↓
Application
   ↓
Monitor + Backup
   ↓
Scale + Secure + Optimize
```

## ⭐ One-Line Interview Answer

> **Azure VM is an IaaS service that provides a virtual Windows or Linux server in Azure, giving engineers control over the operating system, applications, storage, and networking while Azure manages the underlying physical infrastructure.**
