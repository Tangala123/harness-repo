# harness-repo
<img width="1882" height="702" alt="image" src="https://github.com/user-attachments/assets/672327a0-5453-4383-a3ba-6a19a3feb882" />
<img width="1871" height="696" alt="image" src="https://github.com/user-attachments/assets/2d90f000-0556-48f9-bdcd-f6ec1fbfe583" />

Steps to Create a GitHub Connector in Harness
Step 1: Navigate to Connectors
Log in to Harness.
Select your Organization and Project.
Go to Project Settings → Connectors.
Click New Connector.
Select GitHub.
Step 2: Overview
Enter a Connector Name (e.g., github-connector).
(Optional) Add a description.
Click Continue.
Step 3: Details
URL Type: Select Repository.
Connection Type: Select HTTP.
GitHub Repository URL:
https://github.com/Tangala123/harness-repo.git
Click Continue.
Step 4: Credentials
Select HTTP Credentials.
Username: Your GitHub username (e.g., Tangala123).
Password: Select the secret GITHUB_PAT.
Click Continue.
Step 5: Select Connectivity Mode
Choose Connect through Harness Platform.
Click Continue.
Step 6: Delegates Setup
No delegate is required for GitHub connectivity.
Click Continue.
Step 7: Connection Test
Click Test Connection.
Verify the status shows Success.
Click Save.
Usage
This GitHub connector allows Harness to:
Clone the repository during CI pipelines
Fetch Kubernetes manifests during CD stages
✅ Best Practices
Use Repository-level access instead of Account-level access
Prefer GitHub App for enterprise environments
Store tokens securely using Harness Secrets

Steps to Create a Docker Registry Connector (Docker Hub) in Harness
Step 1: Navigate to Docker Registry Connector

Log in to Harness.

Select your Organization and Project.

Go to Project Settings → Connectors.

Click New Connector.

Select Docker Registry.

Step 2: Overview

Enter a Connector Name (e.g., dockerhub-connector).

(Optional) Add a description.

Click Continue.

Step 3: Details

Registry Type / Provider: Select Docker Hub.

Docker Registry URL:

https://registry.hub.docker.com


(If the URL field appears, this is the correct value.)

Authentication Type: Username and Password.

Username: Your Docker Hub username.

Password: Select the secret DOCKERHUB_TOKEN.

Click Continue.

Step 4: Select Connectivity Mode

Choose Connect through Harness Platform.

Click Continue.

Why?

Docker Hub is publicly accessible.

No delegate is required.

Recommended for CI pipelines.

Step 5: Connection Test

Click Test Connection.

Ensure the test result shows Success.

Click Save.

Usage

This Docker Registry connector allows the CI pipeline to:

Build Docker images

Push images securely to Docker Hub

✅ Best Practices

Use Docker Hub Access Tokens, not passwords

Store tokens in Harness Secrets

Avoid using the latest tag in production
