<h1>Deployment and Prevention of Threats with Google Cloud NGFW Enterprise</h1>

<h2>Description</h2>
Deploy and prevent threats with Google Cloud NGFW Enterprise, a native Google Cloud service powered by Palo Alto Networks Threat Prevention technologies. This solution combines the scalability and flexibility of Google Cloud with the advanced security capabilities of Palo Alto Networks, providing deep traffic inspection, real-time threat detection, and automated protection against evolving cyber threats, all within your cloud environment.

Cloud NGFW Enterprise is a fully distributed firewall solution offering advanced protection to safeguard your Google Cloud workloads from both internal and external threats, such as intrusions, malware, spyware, and command-and-control attacks. The service operates by creating Google-managed zonal firewall endpoints that utilize packet interception technology to seamlessly capture and inspect workload traffic for deep packet analysis.
<br />

 <h2>Languages and Utilities Used</h2>

- <b>Access to Google Cloud Shell, or a local machine with a Terraform or gcloud installation</b>
- <b>A Google Cloud project to host the deployment.</b>
- <b>A Google Cloud billing project.</b>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IAM Roles</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: left;
        }
        th {
            background-color: #f2f2f2;
        }
        a {
            color: #007bff;
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <h2>IAM Roles</h2>
    <table>
        <thead>
            <tr>
                <th>Ability</th>
                <th>Level</th>
                <th>Roles</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Create/modify/view firewall endpoints, endpoint associations, security profiles, and security profile groups.</td>
                <td>Organization</td>
                <td>
                    <code>compute.networkAdmin</code><br>
                    <code>compute.networkUser</code><br>
                    <code>compute.networkViewer</code>
                </td>
            </tr>
            <tr>
                <td>Create/modify/view global network firewall policies and view effective rules for VPC networks and virtual machines.</td>
                <td>Project</td>
                <td>
                    <code>compute.securityAdmin</code><br>
                    <code>compute.networkAdmin</code><br>
                    <code>compute.networkViewer</code><br>
                    <code>compute.viewer</code><br>
                    <code>compute.instanceAdmin</code>
                </td>
            </tr>
        </tbody>
    </table>

    <h2>For more information, please see:</h2> 
    <ul>
        <li><a href="#" target="_blank">IAM Roles - Firewall Endpoints</a></li>
        <li><a href="#" target="_blank">IAM Roles - Firewall Endpoint Associations</a></li>
        <li><a href="#" target="_blank">IAM Roles - Security Profiles</a></li>
        <li><a href="#" target="_blank">IAM Roles - Global Network Firewall Policies</a></li>
    </ul>
</body>
</html>



