# FMD Project

## Project Overview

FMD (Forge Model Deploy) is a comprehensive solution designed to streamline the process of managing and deploying projects. It provides a user-friendly interface for uploading, managing, and deploying projects, along with robust backend support and cloud hosting capabilities.

## Features

- **User Authentication**: Secure login and registration system.
- **Project Management**: Upload, view, and manage projects with ease.
- **Profile Management**: Update personal information and profile pictures.
- **Deployment**: Deploy projects to the cloud seamlessly.
- **File Storage**: Organized file storage structure for user-specific directories.
- **API Documentation**: Interactive API documentation using Swagger UI.
- **Error Handling**: Consistent error response format.
- **JSON File Database**: Simple file-based database for development purposes.

## Flow of the Programs

1. After user uploads the project, **Frontend** triggers the Jenkins job remotely.
2. **Jenkins** automates the process of cloning the repository, downloading and extracting the ZIP file, running the Python script, and deploying the infrastructure using Terraform.
3. **Terraform** provisions the AWS infrastructure and prepares the environment for Ansible.
4. **Ansible** configures the EC2 instance by copying the necessary files, installing dependencies, and setting up the services.
5. The **backend** application is set up and the FastAPI service is restarted.
6. The **frontend** application is built and deployed to the Nginx server.
7. The Nginx service is restarted to serve the new frontend application.

This flow ensures that the application is properly set up and configured on the EC2 instance, ready to be accessed and used.

## Technologies Used

### Terraform

- Terraform is an open-source infrastructure as code software tool that allows users to define and provision data center infrastructure using a high-level configuration language. It supports multiple cloud providers and services, enabling consistent and reproducible infrastructure deployments. 

- In this project, Terraform is used to automate the provisioning of AWS resources, such as EC2 instances, VPCs, and security groups. This ensures that the infrastructure is set up in a consistent and repeatable manner, reducing the risk of human error and making it easier to manage and scale the environment.

### Ansible

- Ansible is an open-source automation tool that provides simple and powerful automation for configuration management, application deployment, and task automation. It uses a declarative language to describe system configurations and orchestrate complex workflows. 

- In this project, Ansible is used to configure the provisioned AWS infrastructure, including installing necessary software packages, copying configuration files, and setting up services like Nginx and FastAPI. This ensures that the environment is consistently configured and ready for application deployment, reducing manual intervention and speeding up the deployment process.

### Jenkins

- Jenkins is an open-source automation server that enables developers to build, test, and deploy their applications in a continuous integration and continuous delivery (CI/CD) pipeline. It supports a wide range of plugins to integrate with various tools and services. 

- In this project, Jenkins is used to automate the CI/CD pipeline, including cloning the repository, running build scripts, and triggering Terraform and Ansible tasks. This ensures that the application is continuously tested and deployed, providing faster feedback and reducing the time to market.

### Express

- Express is a minimal and flexible Node.js web application framework that provides a robust set of features for building web and mobile applications. It simplifies the development of server-side applications by providing a set of built-in middleware and routing capabilities. 

- In this project, Express is used to build the backend API, handling user authentication, project management, and file uploads. It provides a RESTful API for the frontend to interact with, enabling seamless communication between the frontend and backend components of the application.

### React

- React is a JavaScript library for building user interfaces, developed and maintained by Facebook. It allows developers to create reusable UI components and manage the state of their applications efficiently. React uses a virtual DOM to optimize rendering performance, making it suitable for building complex and interactive user interfaces. 

- In this project, React is used to build the frontend of the FMD application, providing a user-friendly interface for users to interact with the application. It includes components for user authentication, project management, and file uploads, ensuring a smooth and responsive user experience.


## Summary

1. **Terraform**: Used to provision the AWS infrastructure, such as EC2 instances, required for the application.
2. **Ansible**: Used to configure the provisioned infrastructure, including installing dependencies and setting up services.
3. **Jenkins**: Used to automate the CI/CD pipeline, including cloning the repository, running scripts, and triggering Terraform and Ansible tasks.
4. **Express**: Used to build the backend API, handling user authentication, project management, and file uploads.
5. **React**: Used to build the frontend UI, providing components for user authentication, project management, and more.


## Getting Started

1. Clone the repository.
2. Follow the setup instructions for the frontend, backend, and cloud hosting.
3. Start using the FMD application to manage and deploy your projects.
