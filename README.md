SWE Microservices Project

This project is a distributed microservices system built with Spring Boot, Docker, Kubernetes, and Tilt. Each service is maintained in its own repository under a shared GitHub organization and deployed together using Kubernetes.

Organization

All repositories are now managed under the GitHub organization:

SWE-PictureDictionary

Repositories

Each service is separated into its own repository within the organization:

UI
https://github.com/SWE-PictureDictionary/swe-ui

Edge Service (API Gateway)
https://github.com/SWE-PictureDictionary/swe-edge-service

Config Repository
https://github.com/SWE-PictureDictionary/swe-config-repo

Config Service
https://github.com/SWE-PictureDictionary/swe-config-service

Content Access
https://github.com/SWE-PictureDictionary/swe-content-access

Content Manager
https://github.com/SWE-PictureDictionary/swe-content-manager

Event Processor
https://github.com/SWE-PictureDictionary/swe-event-processor

Progress Access
https://github.com/SWE-PictureDictionary/swe-progress-access

Progress Manager
https://github.com/SWE-PictureDictionary/swe-progress-manager

Completion Engine
https://github.com/SWE-PictureDictionary/swe-completion-engine

Kubernetes Infrastructure
https://github.com/SWE-PictureDictionary/swe-infra

Running the Project (Tilt - Recommended)

1. Clone the infrastructure repository
git clone https://github.com/SWE-PictureDictionary/swe-infra
cd swe-infra

2. Install Ingress Controller

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml

3. Start Tilt
tilt up

This will:

- Build all services
- Deploy them to Kubernetes
- Start a local development environment

3. Access the application

Open your browser and go to:

http://localhost/

(No port forwarding needed)

Making Changes

Tilt enables faster development without manually restarting everything.

Modify a service

Go to the service repository (e.g., swe-ui) and make your changes.

Reload a specific service

tilt trigger ui

(Replace "ui" with any service name)

This will:

- Rebuild only that service
- Redeploy it automatically

Alternative: Running with Kubernetes (Manual)

1. Deploy all services
kubectl apply -f .

2. Restart deployments (pull latest images)
kubectl rollout restart deployment

3. Check pod status
kubectl get pods

Wait until all pods show Running.

4. Access the application
kubectl port-forward svc/ui 8000:80

Then open in your browser:

http://localhost:8000/

Development Workflow

Each microservice is developed in its own repository within the organization.

Clone and work within the specific service you want to modify.

Test locally (Tilt recommended).

After making changes:

- Verify the service works locally
- Push changes to the corresponding repository
- Ensure CI/CD workflows pass (if configured)

Use tilt trigger <service> for quick reloads.

Configuration

Configuration is handled through:

Config Repository
https://github.com/SWE-PictureDictionary/swe-config-repo

Config Service
https://github.com/SWE-PictureDictionary/swe-config-service
