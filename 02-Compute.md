# Azure Compute

## Definition

Azure Compute is a group of services in Microsoft Azure that provides **CPU, RAM, and processing power** to run applications, websites, and servers in the cloud.

---

## Simple Example

Suppose a company needs a server to run its application.

### Traditional Way

**Company → Buy Physical Server → Install OS → Run Application**

### Azure Way

**Company → Azure Compute → Create Server/Service → Run Application**

---

## Main Azure Compute Services

### 1. Azure Virtual Machine (VM)

- Provides a virtual server in the cloud.
- Supports **Windows and Linux**.
- Similar to **AWS EC2**.

### 2. Azure App Service

- Used to host **websites and web applications**.
- You don't need to manage the server directly.

### 3. Azure Functions

- Runs small pieces of code when an event occurs.
- It is a **Serverless** service.

### 4. Azure Kubernetes Service (AKS)

- Used to run and manage **containers with Kubernetes**.

### 5. Azure Virtual Machine Scale Sets (VMSS)

- Manages multiple VMs.
- Can automatically **increase or decrease VMs** according to demand.

---

## Easy Formula to Remember

**Azure Compute = Processing Power + Running Applications**

---

## AWS → Azure

| AWS Service | Azure Service |
|---|---|
| EC2 | Azure VM |
| Auto Scaling | VM Scale Sets |
| ECS / EKS | AKS |
| Lambda | Azure Functions |
| Elastic Beanstalk | App Service |

---

## One-Line Interview Answer

> **Azure Compute provides the processing power required to run applications, websites, servers, and workloads in the Azure Cloud.**
