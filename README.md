# harness-repo
<img width="1882" height="702" alt="image" src="https://github.com/user-attachments/assets/672327a0-5453-4383-a3ba-6a19a3feb882" />

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
