# 🚀 Deployment and Prevention of Threats with Google Cloud NGFW Enterprise

## ✨ Description

Deploy and prevent threats with **Google Cloud NGFW Enterprise**, a native Google Cloud service powered by **Palo Alto Networks Threat Prevention** technologies. This solution combines the scalability and flexibility of Google Cloud with the advanced security capabilities of Palo Alto Networks, providing:
- **Deep traffic inspection**
- **Real-time threat detection**
- **Automated protection** against evolving cyber threats, all within your cloud environment.

**Cloud NGFW Enterprise** is a fully distributed firewall solution offering advanced protection to safeguard your Google Cloud workloads from both **internal** and **external threats**, such as:
- Intrusions
- Malware
- Spyware
- Command-and-control attacks

The service operates by creating Google-managed zonal firewall endpoints that utilize **packet interception technology** to seamlessly capture and inspect workload traffic for **deep packet analysis**.

---

## 💻 Languages and Utilities Used

- **Access to Google Cloud Shell**, or a local machine with a **Terraform** or **gcloud** installation.
- A **Google Cloud project** to host the deployment.
- A **Google Cloud billing project**.

---

## 🔐 IAM Roles

| **Ability** | **Level** | **Roles** |
| --- | --- | --- |
| Create/modify/view firewall endpoints, endpoint associations, security profiles, and security profile groups. | Organization | compute.networkAdmin, compute.networkUser, compute.networkViewer |
| Create/modify/view global network firewall policies and view effective rules for VPC networks and virtual machines. | Project | compute.securityAdmin, compute.networkAdmin, compute.networkViewer, compute.viewer, compute.instanceAdmin |

For more information, please see:
- [IAM Roles - Firewall Endpoints](#)
- [IAM Roles - Firewall Endpoint Associations](#)
- [IAM Roles - Security Profiles](#)
- [IAM Roles - Global Network Firewall Policies](#)

---

## 🌍 Topology

 
*  ![image](https://github.com/user-attachments/assets/8f76f78a-e4e7-4cd5-8b1f-71a6856923e4)

---

## 🔧 Setup Instructions

# Prepare for Deployment

Enable the required APIs, retrieve the deployment files, and configure the environment variables.

# 🚀 Deployment Guide  

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cloud Shell Tutorial</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 20px;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        code {
            background-color: #f4f4f4;
            padding: 5px 10px;
            border-radius: 5px;
            font-size: 1.1em;
        }
        pre {
            background-color: #f4f4f4;
            padding: 10px;
            border-radius: 5px;
            overflow-x: auto;
            font-size: 1.1em;
        }
        .section-title {
            font-size: 1.2em;
            font-weight: bold;
            margin-top: 20px;
        }
        ul {
            list-style-type: none;
        }
        li {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

    <h1>Cloud Shell Tutorial</h1>

    <p><strong>Open Google Cloud Shell</strong> and enable the required APIs:</p>

    <pre><code>gcloud services enable compute.googleapis.com
gcloud services enable networksecurity.googleapis.com
gcloud services enable firewallinsights.googleapis.com</code></pre>

    <div class="section-title">Set environment variables for your deployment project and billing project:</div>

    <pre><code>export PROJECT_ID=YOUR_PROJECT_ID
export BILLING_ID=YOUR_BILLING_PROJECT_ID</code></pre>

    <div class="section-title">Set environment variables for your organization ID, deployment region, zone, and naming prefix:</div>

    <pre><code>export ORG_ID=$(gcloud projects describe $PROJECT_ID --format=json | jq -r '.parent.id')
export REGION=us-central1
export ZONE=us-central1-a
export PREFIX=panw</code></pre>

    <div class="section-title">Select a deployment option. Both options deploy identical environments:</div>

    <ul>
        <li><strong>Option 1:</strong> Deploy using Terraform</li>
        <p>All of the cloud resources required for the tutorial are deployed using a single Terraform plan.</p>
        <li><strong>Option 2:</strong> Deploy using gcloud</li>
        <p>Each cloud resource is deployed individually using <code>gcloud</code>.</p>
    </ul>

</body>
</html>


