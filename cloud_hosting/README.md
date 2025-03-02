# Cloud Hosting Setup

This directory contains the necessary files to set up cloud hosting for the FMD project using Terraform and Ansible.

## Terraform Setup

1. **main.tf**: This file contains the Terraform configuration to provision an AWS EC2 instance and create necessary files for Ansible.
2. **output.tf**: This file defines the outputs for the Terraform configuration.
3. **variables.tf**: This file contains the variable definitions used in the Terraform configuration.

### Steps to Deploy

1. Initialize Terraform:
   ```sh
   terraform init
   ```
2. Apply the Terraform configuration:
   ```sh
   terraform apply
   ```

## Ansible Setup

1. **ansible.cfg**: Configuration file for Ansible.
2. **playbook.yml**: Ansible playbook to set up the application on the EC2 instance.
3. **vars.yml**: Variables file used in the Ansible playbook.
4. **templates/**: Directory containing Jinja2 templates for Ansible.

### Steps to Run Ansible Playbook

1. Ensure the EC2 instance is running and the inventory file is created by Terraform.
2. Run the Ansible playbook:
   ```sh
   ansible-playbook -i inventory.ini ansible/playbook.yml
   ```

This will set up the backend and frontend applications on the EC2 instance and configure Nginx to serve the frontend.

## Jenkins Setup

1. **JenkinsFile**: This file contains the Jenkins pipeline configuration to automate the deployment process.

### Steps to Run Jenkins Job

1. Ensure Jenkins is set up and configured with the necessary credentials and environment variables.
2. Trigger the Jenkins job remotely from the frontend application.

This will automate the process of cloning the repository, downloading and extracting the ZIP file, running the Python script, and deploying the infrastructure using Terraform.

## Detailed Terraform, Ansible, and Jenkins Flow

### Terraform (main.tf)

The `main.tf` file is responsible for provisioning the necessary AWS infrastructure and preparing the environment for Ansible to configure the application. Here are the key components:

1. **AWS Provider Configuration**: Specifies the AWS region to use.
2. **EC2 Instance**: Provisions an EC2 instance using a specified AMI, instance type, and security group.
3. **Ansible Inventory File**: Creates an inventory file for Ansible with the public IP of the EC2 instance.
4. **Backend IP Route**: Generates a JavaScript file with the backend API base URL.
5. **Run Ansible Playbook**: Executes the Ansible playbook to configure the EC2 instance after it is provisioned.

### Ansible Playbook (playbook.yml)

The `playbook.yml` file contains tasks to set up the application on the EC2 instance. Here are the key tasks:

1. **Copy Backend Files**: Copies the generated backend files from the local machine to the EC2 instance.
2. **Restart FastAPI Service**: Restarts the FastAPI service to apply the new backend configuration.
3. **Install Frontend Packages**: Installs the necessary npm packages for the frontend application.
4. **Create Frontend API Route File**: Generates the API route file for the frontend application.
5. **Copy Frontend Files**: Copies the generated frontend files from the local machine to the EC2 instance.
6. **Build Frontend**: Builds the frontend application using npm.
7. **Copy Built Frontend to Nginx**: Copies the built frontend files to the Nginx directory on the EC2 instance.
8. **Restart Nginx Service**: Restarts the Nginx service to serve the new frontend application.

### Jenkins Pipeline (JenkinsFile)

The `JenkinsFile` contains the pipeline configuration to automate the deployment process. Here are the key stages:

1. **Clone Repository**: Clones the repository to the Jenkins workspace.
2. **Download and Extract ZIP**: Downloads and extracts the ZIP file containing the project files.
3. **Run Python Script**: Runs the Python script to generate the necessary files.
4. **Run Terraform**: Deploys the infrastructure using Terraform.
5. **Get Terraform Output**: Retrieves the public IP of the EC2 instance.

## Flow of the Programs

1. **Frontend** triggers the Jenkins job remotely.
2. **Jenkins** automates the process of cloning the repository, downloading and extracting the ZIP file, running the Python script, and deploying the infrastructure using Terraform.
3. **Terraform** provisions the AWS infrastructure and prepares the environment for Ansible.
4. **Ansible** configures the EC2 instance by copying the necessary files, installing dependencies, and setting up the services.
5. The **backend** application is set up and the FastAPI service is restarted.
6. The **frontend** application is built and deployed to the Nginx server.
7. The Nginx service is restarted to serve the new frontend application.

This flow ensures that the application is properly set up and configured on the EC2 instance, ready to be accessed and used.
