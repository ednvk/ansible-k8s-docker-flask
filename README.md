🚀 **Flask App CI/CD with Ansible, Docker, and Kubernetes**
This project demonstrates a complete CI/CD pipeline using Ansible to automate the building and deployment of a Flask-based Python web application using Docker and Kubernetes across separate servers.

🧱 **Project Structure**
ansible-k8s-docker-flat/
├── ansible/
│   ├── deploy.yml              # Ansible playbook for build and deploy
│   ├── inventory.ini           # Inventory file with docker & k8s hosts
│   └── vault.yml               # Encrypted DockerHub credentials (vault)
├── flask-app/
│   ├── app.py                  # Simple Flask app
│   ├── Dockerfile              # Dockerfile for containerizing the app
│   └── requirements.txt        # Python dependencies
├── k8s/
│   ├── deployment.yaml         # Kubernetes Deployment spec
│   └── service.yaml            # Kubernetes Service spec
└── README.md

🌐 **Workflow Summary**
1) Ansible control node connects to:
   🔧 Docker server to build & push the Docker image
   ☸️ Kubernetes server to deploy the app using YAML manifests

2) Docker image is built from flask-app/ and pushed to Docker Hub.

3) Kubernetes manifests are applied to deploy the app in a cluster.
