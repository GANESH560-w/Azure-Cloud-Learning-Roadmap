# Azure Fundamentals — SOP

## 1. Purpose

This SOP explains the fundamental concepts of Microsoft Azure that a Cloud Support Engineer, Cloud Engineer, or DevOps Engineer should understand before working with Azure services.

---

## 2. Azure Fundamentals Overview

### Main Topics

1. Microsoft Azure
2. Azure Tenant
3. Management Groups
4. Azure Subscription
5. Resource Groups
6. Azure Resources
7. Azure Regions
8. Availability Zones
9. Azure Resource Manager (ARM)
10. Azure Portal
11. Azure Resource Hierarchy

---

# 3. Microsoft Azure

## English Meaning

Microsoft Azure is Microsoft's cloud computing platform that provides services such as:

* Virtual Machines
* Networking
* Storage
* Databases
* Security
* Monitoring
* Backup
* Containers
* AI services

Companies can use Azure infrastructure without purchasing and maintaining all physical hardware themselves.

## Desi Marathi Explanation

Azure म्हणजे Microsoft ची **cloud platform**.

कंपनीला server, storage, database, networking किंवा backup infrastructure पाहिजे असल्यास प्रत्येक गोष्ट स्वतःच्या datacenter मध्ये खरेदी करण्याऐवजी Azure वर deploy करता येते.

### Real-Life Company Example

ABC Company ला website चालवण्यासाठी server पाहिजे.

Traditional infrastructure:

```text
Company
   ↓
Physical Server
   ↓
Storage
   ↓
Network
   ↓
Maintenance
```

Azure:

```text
Company
   ↓
Azure
   ↓
Virtual Machine
   ↓
Application
```

---

# 4. Azure Tenant

## English Meaning

An Azure tenant represents an organization's Microsoft Entra ID directory.

It manages the organization's identities, users, groups and applications.

## Desi Marathi Explanation

Tenant म्हणजे कंपनीचा **identity system** समजा.

उदाहरण:

```text
ABC Company
     |
     ↓
Azure Tenant
     |
     ├── Users
     ├── Groups
     ├── Applications
     └── Identity Management
```

### Company Use

Company मधील:

* Cloud Admin
* DevOps Engineer
* Developer
* Cloud Support Engineer

यांच्या identities आणि access management साठी Entra ID tenant वापरला जातो.

---

# 5. Management Groups

## English Meaning

Management Groups provide a way to organize and govern multiple Azure subscriptions.

## Desi Marathi Explanation

मोठ्या company कडे अनेक Azure subscriptions असतील तर त्यांना एकाच ठिकाणाहून govern करण्यासाठी Management Groups वापरतात.

### Example

```text
ABC Company
      |
      ↓
Management Group
      |
      ├── Production Subscription
      ├── Development Subscription
      ├── Testing Subscription
      └── Security Subscription
```

### Company Use

Management Groups च्या माध्यमातून organization-wide:

* Policies
* Governance
* Access control
* Compliance

manage करता येतात.

---

# 6. Azure Subscription

## English Meaning

An Azure Subscription is a management and billing boundary for Azure resources.

Resources are created inside a subscription.

## Desi Marathi Explanation

Subscription म्हणजे Azure मधील **billing आणि resource management boundary**.

### Example

```text
ABC Company
      |
      ├── Production Subscription
      ├── Development Subscription
      └── Testing Subscription
```

Company production आणि development resources वेगवेगळ्या subscriptions मध्ये ठेवू शकते.

### Important

Subscription आणि Resource Group वेगवेगळे आहेत.

Hierarchy:

```text
Subscription
      ↓
Resource Group
      ↓
Resources
```

---

# 7. Resource Group

## English Meaning

A Resource Group is a logical container used to organize related Azure resources.

## Desi Marathi Explanation

Resource Group म्हणजे **project चा folder** समजा.

### Example

```text
RG-Production-Web
       |
       ├── Virtual Machine
       ├── Storage Account
       ├── VNet
       ├── Public IP
       └── Load Balancer
```

### Company Use

Production website साठी:

```text
RG-PROD-WEB
```

Development environment साठी:

```text
RG-DEV-WEB
```

Testing environment साठी:

```text
RG-TEST-WEB
```

यामुळे Cloud Support team ला resources शोधणे आणि manage करणे सोपे होते.

---

# 8. Azure Resources

## English Meaning

A resource is an individual Azure service or component that you create and manage.

## Examples

* Virtual Machine
* Storage Account
* Virtual Network
* Public IP
* Load Balancer
* Azure SQL Database
* Key Vault

## Desi Marathi Explanation

Resource म्हणजे Azure मधील **actual service/object**.

Example:

```text
Resource Group
      |
      ├── VM
      ├── VNet
      ├── Storage
      ├── Database
      └── Public IP
```

वरील प्रत्येक item हा एक Azure resource आहे.

---

# 9. Azure Region

## English Meaning

An Azure Region is a geographical location where Azure datacenter infrastructure is deployed.

## Desi Marathi Explanation

Region म्हणजे Azure चा **geographical location**.

उदाहरण:

```text
India
 |
 ├── Central India
 └── South India
```

### Why Region Is Important

Region निवडताना विचारात घेतले जाते:

* User location
* Network latency
* Data residency
* Compliance
* Availability
* Cost
* Service availability

### Company Example

India मधील users साठी application deploy करताना company India region consider करू शकते.

---

# 10. Availability Zones

## English Meaning

Availability Zones are physically separate locations within an Azure region that provide redundancy and high availability.

### Basic Structure

```text
Azure Region
     |
     ├── Zone 1
     ├── Zone 2
     └── Zone 3
```

## Desi Marathi Explanation

एका region मध्ये वेगवेगळ्या physical locations असतात.

एका location मध्ये hardware किंवा infrastructure problem झाला तरी दुसऱ्या zone मध्ये workload available ठेवता येतो, जर architecture तसे design केले असेल.

### Company Example

```text
Production Application
        |
        ├── VM → Zone 1
        ├── VM → Zone 2
        └── VM → Zone 3
```

यामुळे application ची availability वाढवता येते.

---

# 11. Azure Resource Manager (ARM)

## English Meaning

Azure Resource Manager is the management layer used to deploy and manage Azure resources.

Azure Portal, Azure CLI, PowerShell and APIs can be used to manage resources through Azure Resource Manager.

## Desi Marathi Explanation

ARM म्हणजे Azure मधील **resource management layer**.

आपण:

* VM create करतो
* VNet create करतो
* Storage create करतो
* Resource delete करतो
* Access manage करतो

हे operations ARM management layer मार्फत handle केले जातात.

### Example

```text
Admin
  |
  ├── Azure Portal
  ├── Azure CLI
  └── PowerShell
          |
          ↓
Azure Resource Manager
          |
          ├── VM
          ├── VNet
          ├── Storage
          └── Database
```

---

# 12. Azure Portal

## English Meaning

Azure Portal is the web-based graphical interface used to create, configure, monitor and manage Azure resources.

## Desi Marathi Explanation

Azure Portal म्हणजे Azure चा **GUI / Control Panel**.

Cloud Support Engineer Azure Portal मधून:

* VM status check करू शकतो
* CPU/Memory monitoring करू शकतो
* NSG check करू शकतो
* Storage check करू शकतो
* Logs पाहू शकतो
* Backup status check करू शकतो
* Alerts पाहू शकतो

---

# 13. Azure Resource Hierarchy

This is one of the most important Azure Fundamentals concepts.

```text
Microsoft Entra Tenant
        |
        ↓
Management Groups
        |
        ↓
Subscriptions
        |
        ↓
Resource Groups
        |
        ↓
Resources
```

## Desi Marathi Meaning

```text
Tenant
= Company Identity

Management Group
= Multiple subscriptions manage करण्याची level

Subscription
= Billing + Management Boundary

Resource Group
= Project/Resource Container

Resource
= Actual Azure Service
```

---

# 14. Complete Company Example

Consider:

**ABC E-Commerce Company**

### Step 1 — Tenant

```text
ABC E-Commerce
      ↓
Microsoft Entra Tenant
```

### Step 2 — Management Group

```text
Azure Tenant
      ↓
Production Management Group
```

### Step 3 — Subscription

```text
Production Management Group
      |
      ↓
Production Subscription
```

### Step 4 — Resource Group

```text
Production Subscription
      |
      ↓
RG-PROD-WEB
```

### Step 5 — Resources

```text
RG-PROD-WEB
      |
      ├── Virtual Machine
      ├── VNet
      ├── Storage Account
      ├── Load Balancer
      ├── Public IP
      ├── Azure SQL
      └── Key Vault
```

---

# 15. Cloud Support Engineer — Troubleshooting Flow

When a client reports:

> "Production VM is not accessible."

Follow this basic flow:

```text
1. Identify Subscription
          ↓
2. Identify Resource Group
          ↓
3. Identify VM
          ↓
4. Check VM Status
          ↓
5. Check Region / Availability
          ↓
6. Check Network Interface
          ↓
7. Check Private/Public IP
          ↓
8. Check NSG
          ↓
9. Check Route Table
          ↓
10. Check VPN / Gateway if applicable
          ↓
11. Check Azure Monitor
          ↓
12. Check Logs
          ↓
13. Troubleshoot / Resolve
```

---

# 16. Important Azure Fundamentals Interview Questions

### Q1. What is Azure?

Azure is Microsoft's cloud computing platform that provides compute, networking, storage, database, security, monitoring and other cloud services.

### Q2. What is a Tenant?

A tenant represents an organization's Microsoft Entra ID directory and identity boundary.

### Q3. What is a Subscription?

A subscription is a management and billing boundary for Azure resources.

### Q4. What is a Resource Group?

A Resource Group is a logical container used to organize related Azure resources.

### Q5. What is an Azure Region?

A region is a geographical location containing Azure datacenter infrastructure.

### Q6. What is an Availability Zone?

An Availability Zone is a physically separate location within an Azure region designed to provide redundancy and high availability.

### Q7. What is Azure Resource Manager?

ARM is Azure's management layer used to deploy and manage Azure resources.

### Q8. What is the difference between Subscription and Resource Group?

**Subscription:** Higher-level management and billing boundary.

**Resource Group:** Logical container inside a subscription for related resources.

### Q9. What is the Azure resource hierarchy?

```text
Management Groups
       ↓
Subscriptions
       ↓
Resource Groups
       ↓
Resources
```

The Microsoft Entra tenant is the organization's identity directory and is associated with the Azure environment.

---

# 17. Quick Revision

| Concept               | Simple Meaning                             |
| --------------------- | ------------------------------------------ |
| **Azure**             | Microsoft's Cloud Platform                 |
| **Tenant**            | Company's identity directory               |
| **Management Group**  | Organizes multiple subscriptions           |
| **Subscription**      | Billing and management boundary            |
| **Resource Group**    | Container for related resources            |
| **Resource**          | Actual Azure service                       |
| **Region**            | Geographical Azure location                |
| **Availability Zone** | Separate physical location inside a region |
| **ARM**               | Azure resource management layer            |
| **Azure Portal**      | Web GUI for Azure                          |

---

# 18. Golden Rule to Remember

```text
TENANT
   ↓
MANAGEMENT GROUP
   ↓
SUBSCRIPTION
   ↓
RESOURCE GROUP
   ↓
RESOURCE
```

For your **Cloud Support Engineer / Cloud Engineer / DevOps Engineer** preparation, understand this hierarchy first. Then move to **Compute → Networking → Storage → Identity → Security → Monitoring**.
