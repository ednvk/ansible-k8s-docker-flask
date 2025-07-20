**🚀 Flask App CI/CD with Ansible, Docker, and Kubernetes**

This project demonstrates a complete CI/CD pipeline using Ansible to automate the building and deployment of a Flask-based Python web application using Docker and Kubernetes across separate servers.

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


**🌐 Workflow Summary**
1) Ansible control node connects to:

  🔧 Docker server to build & push the Docker image

  ☸️ Kubernetes server to deploy the app using YAML manifests

2) Docker image is built from flask-app/ and pushed to Docker Hub.

3) Kubernetes manifests are applied to deploy the app in a cluster.


**📦 Technologies Used**
Flask – Python micro web framework
Docker – Containerization
Docker Hub – Image registry
Ansible – Configuration management & automation
Kubernetes – Container orchestration
Ubuntu EC2 instances – Hosting environment (AWS)


**🔐 Secure DockerHub Credentials**
DockerHub credentials are stored securely using Ansible Vault:
ansible-vault create ansible/vault.yml
dockerhub_username: your_dockerhub_username
dockerhub_password: your_dockerhub_password_or_token

Use **--ask-vault-pass** when running the playbook.


**🚀 How to Run**
✅ Ensure passwordless SSH access to your Docker and K8s servers
✅ Ensure Docker is installed and logged in (docker login)
✅ Install required Ansible collections:
ansible-galaxy collection install community.docker kubernetes.core


**🔥 Run the playbook:**
cd ansible
ansible-playbook -i inventory.ini deploy.yml --ask-vault-pass


**✅ Sample Flask Output**
Once deployed, visit:
http://<K8S-Node-IP>:<NodePort>

**Expected output:**
🚀 Hello from Kubernetes with Ansible!


**🛡️ Best Practices**
Use t3.medium or higher instance types (Minikube requires 2+ vCPUs)
Never commit vault.yml with decrypted values
Use exclude: in Ansible copy tasks to skip .git, .swp, and vault.yml



Use source: build with build.path in community.docker.docker_image

📌 Author
Built by Vamsi Krishna
Feel free to fork, star, and contribute!
