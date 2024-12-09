# Node.js CI/CD Pipeline

## Overview
This project sets up an automated pipeline for building, testing, and deploying a Node.js application using Docker and Kubernetes. The pipeline makes use of **GitHub Actions** to automatically run tests, build a Docker image, and deploy it to a local Kubernetes cluster managed by **Minikube**.

## Features
- **Automated Testing**: Runs tests every time a change is made to the code.
- **Docker Build**: Creates a Docker image of the app.
- **Kubernetes Deployment**: Automatically deploys the app to Kubernetes.
- **Slack Notifications**: Sends messages to Slack to notify you about the success or failure of the deployment.

## Steps to Set Up and Run the Project

### 1. Setting Up the Node.js Application
- We built a basic Node.js app that serves a "Hello World" message on a web page.

#### To run the app on your local machine:
1. Clone the project from GitHub:
   ```bash
   git clone <your-repo-url>
Go to the project folder:
cd my-node-app

Install the required packages:
npm install

Start the application:
npm start

The app should now be available at http://localhost:3000.

2. Dockerizing the Application
We created a Dockerfile to turn the app into a Docker container.
To build and run the Docker image:
Build the Docker image:
docker build -t <docker-hub-username>/my-node-app:v1.0.0 .

Run the Docker container:
docker run -p 3000:3000 <docker-hub-username>/my-node-app:v1.0.0


4. Deploying on Kubernetes with Minikube
Kubernetes helps in managing and scaling applications. We used Minikube to run Kubernetes locally.
To deploy the app:
Start Minikube:
minikube start

Apply the Kubernetes configuration:

kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml


Expose the app on your local machine:

kubectl port-forward svc/my-node-app-service 8080:80


Open your browser and go to http://localhost:8080 to see the app running.

6. Setting Up CI/CD with GitHub Actions
We created a GitHub Actions pipeline to automate testing, building, and deployment.

The pipeline does the following:
Test: Runs unit tests every time there is a pull request.
Build Docker Image: Builds a Docker image whenever there is a change to the code.
Push to Docker Hub: Uploads the Docker image to Docker Hub.
Deploy to Kubernetes: Deploys the new Docker image to Kubernetes.
The pipeline is set up in the .github/workflows/ci-cd.yml file.
