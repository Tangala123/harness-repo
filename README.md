# harness-repo
<img width="1882" height="702" alt="image" src="https://github.com/user-attachments/assets/672327a0-5453-4383-a3ba-6a19a3feb882" />
<img width="1871" height="696" alt="image" src="https://github.com/user-attachments/assets/2d90f000-0556-48f9-bdcd-f6ec1fbfe583" />
<img width="1888" height="966" alt="image" src="https://github.com/user-attachments/assets/9f4933d0-51c9-4fdf-a900-cb74f34993eb" />
<img width="1336" height="705" alt="image" src="https://github.com/user-attachments/assets/8fb3be14-245e-4326-bc39-4ac0299b8c9b" />
<img width="1893" height="511" alt="image" src="https://github.com/user-attachments/assets/fab54028-afd5-4eec-98c4-f1093c368b76" />
<img width="1918" height="622" alt="image" src="https://github.com/user-attachments/assets/a2aab1e1-9a74-4425-b91b-d1734d202e22" />
<img width="1866" height="868" alt="image" src="https://github.com/user-attachments/assets/8a6d78e3-e112-4a24-82fa-c2baa9dc7a53" />
<img width="1795" height="735" alt="image" src="https://github.com/user-attachments/assets/fca7a769-e2c8-42e1-81b4-0d7386c1fa19" />
<img width="1658" height="923" alt="image" src="https://github.com/user-attachments/assets/1e5feb00-929a-4d07-b282-b4f67033f267" />

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


tep 1 — Create Namespace for Delegate
kubectl create namespace harness-delegate-ng


This ensures all delegate resources are isolated.

Step 2 — Prepare harness-delegate.yml

You already have this YAML (from Harness).

It contains:

Namespace

ClusterRoleBinding

Secret (DELEGATE_TOKEN)

Deployment

HPA (HorizontalPodAutoscaler)

CronJob for upgrades

If you need, you can download YAML from Harness Delegate docs.

Step 3 — Apply the YAML
kubectl apply -f harness-delegate.yml


Verify namespace resources:

kubectl get all -n harness-delegate-ng


You should see the deployment (initially ContainerCreating)

Secret, ConfigMap, CronJob, etc.

Step 4 — Watch Pod Status
kubectl get pods -n harness-delegate-ng -w


✅ Expected transitions:

ContainerCreating → Running

If you see ImagePullBackOff → check disk space (should be fixed now)

If ErrImagePull → check Docker registry access / credentials

Step 5 — Verify Delegate is Running
kubectl get pods -n harness-delegate-ng


Expected output:

NAME                                 READY   STATUS    RESTARTS   AGE
kubernetes-delegate-xxxxxx           1/1     Running   0          1m

Step 6 — Use Delegate in Harness Kubernetes Connector

Go to Harness → Project Settings → Connectors → New Connector → Kubernetes

Details:

Connectivity: “Use the credentials of a specific Harness Delegate”

Delegate: select kubernetes-delegate

Namespace: harness-delegate-ng (or leave blank for default)

Click Test Connection → Success

Click Save
