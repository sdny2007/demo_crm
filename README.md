Portfolio End Mission

Overview
This project uses the demo-crm application, which allows users to add customer profiles and display them on a webpage.

⚠️ Important: Run Terraform Before the Workflow
Before running the workflow, make sure to deploy the infrastructure using Terraform. Use the "Terraform_EKS" folder to set up the environment.

RUN Terraform:
aws configure (Access key file)
terraform init (terraform directory)
terraform apply -var-file=terraform.tfvars

Workflow Process
Job 1 - CI Process
Starts by checking the application's health.
Connects the application to the database and verifies that a customer profile can be successfully added and retrieved (POST & GET requests).
Pushes the correct image to Amazon ECR with the tag latest (Note: Versioning is not implemented).
Job 2 - CD Process
Deploys the relevant services for the EKS environment.
Deploys the following components:
Nginx Ingress (Deployment with 2 replicas)
MongoDB (StatefulSet with 2 replicas)
Demo-CRM application (Deployment with 2 replicas)



Deleting the Environment
Use the following commands to clean up the environment:

helm uninstall my-ingress-nginx
helm uninstall mongo-db
kubectl delete deployment demo-crm
kubectl delete svc service-db
kubectl delete svc service-app
kubectl delete ingress ingress-app
kubectl delete svc my-ingress-nginx-controller
kubectl delete svc service-app
