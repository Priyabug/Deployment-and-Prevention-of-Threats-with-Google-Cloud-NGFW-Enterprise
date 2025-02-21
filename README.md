<h1>Deployment and Prevention of Threats with Google Cloud NGFW Enterprise</h1>

<h2>Description</h2>
Deploy and prevent threats with Google Cloud NGFW Enterprise, a native Google Cloud service powered by Palo Alto Networks Threat Prevention technologies. This solution combines the scalability and flexibility of Google Cloud with the advanced security capabilities of Palo Alto Networks, providing deep traffic inspection, real-time threat detection, and automated protection against evolving cyber threats, all within your cloud environment.

Cloud NGFW Enterprise is a fully distributed firewall solution offering advanced protection to safeguard your Google Cloud workloads from both internal and external threats, such as intrusions, malware, spyware, and command-and-control attacks. The service operates by creating Google-managed zonal firewall endpoints that utilize packet interception technology to seamlessly capture and inspect workload traffic for deep packet analysis.
<br />

 <h2>Languages and Utilities Used</h2>

- <b>Access to Google Cloud Shell, or a local machine with a Terraform or gcloud installation.</b>
- <b>A Google Cloud project to host the deployment.</b>
- <b>A Google Cloud billing project.</b>


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

- <b>IAM Roles - Firewall Endpoints</b>
- <b>IAM Roles - Firewall Endpoint Associations</b>
- <b>IAM Roles - Security Profiles</b>
- <b>IAM Roles - Global Network Firewall Policies</b>

 <h2>Topology</h2>

  ![image](https://github.com/user-attachments/assets/8f76f78a-e4e7-4cd5-8b1f-71a6856923e4)

    <h2>Prepare for Deployment</h2>
    <ul>
        <li>
            <p>Open <a href="https://shell.cloud.google.com/" target="_blank">Google Cloud Shell</a> and enable the required APIs:</p>
            <pre>
gcloud services enable compute.googleapis.com
gcloud services enable networksecurity.googleapis.com
gcloud services enable firewallinsights.googleapis.com
            </pre>
        </li>
        <li>
            <p>Set environment variables for your deployment project and billing project:</p>
            <pre>
export PROJECT_ID=YOUR_PROJECT_ID
export BILLING_ID=YOUR_BILLING_PROJECT_ID
            </pre>
        </li>
        <li>
            <p>Set environment variables for your organization ID, deployment region, zone, and naming prefix:</p>
            <pre>
export ORG_ID=$(gcloud projects describe $PROJECT_ID --format=json | jq -r '.parent.id')
export REGION=us-central1
export ZONE=us-central1-a
export PREFIX=panw
            </pre>
        </li>
        <li>
            <p>Select a deployment option. Both options deploy identical environments:</p>
            <ul>
                <li><strong>Option 1:</strong> <a href="#">Deploy using Terraform</a></li>
                <ul>
                    <li>All of the cloud resources required for the tutorial are deployed using a single Terraform plan.</li>
                </ul>
                <li><strong>Option 2:</strong> <a href="#">Deploy using gcloud</a></li>
                <ul>
                    <li>Each cloud resource is deployed individually using <code>gcloud</code>.</li>
                </ul>
            </ul>
        </li>
    </ol>
</body>
</html>

<br>

## Deployment done using Terraform

1. In Cloud Shell, clone the repository and change directories to `/terraform`. 

    ```
    git clone https://github.com/PaloAltoNetworks/google-cloud-ngfw-tutorial
    cd google-cloud-ngfw-tutorial/terraform
    ```

2. Create a `terraform.tfvars` file.

    ```
    cp terraform.tfvars.example terraform.tfvars
    ```

3. Edit the `terraform.tfvars` file and set values for the following variables.

    | Key               | Value                                                   |
    | ----------------- | ------------------------------------------------------- |
    | `org_id`          | The organization ID of your Google Cloud organization.  |
    | `project_id`      | The deployment project ID.                              |
    | `billing_project` | The billing project for your Google Cloud organization. |
    | `region`          | The region for the deployment.                          |
    | `zone`            | The zone with `region` for the cloud resources.         |
    | `prefix`          | A unique string to prepend to the created resources.    |


2.  Initialize and apply the Terraform plan.

    ```
    terraform init
    terraform apply
    ```

    Enter `yes` to create the resources. 

4. Once the Terraform plan completes, proceed to [Prevent Threats with Cloud NGFW](#prevent-threats-with-cloud-ngfw).

<br>






