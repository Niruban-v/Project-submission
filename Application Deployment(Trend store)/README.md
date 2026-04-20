📄 DevOps CI/CD Pipeline Application Deployment(Trend-Store)

Project Overview
This project demonstrates a complete end-to-end DevOps pipeline for deploying a production-ready web application using modern DevOps tools and practices.
The application is containerized using Docker, automated via Jenkins CI/CD pipeline, deployed on AWS EKS (Kubernetes), and monitored using Prometheus and Grafana.

Architecture
GitHub → Jenkins → Docker → DockerHub → Kubernetes (EKS) → LoadBalancer → User
                                              ↓
                                     Prometheus + Grafana

⚙️ Tools & Technologies Used
Version Control: GitHub
CI/CD: Jenkins
Containerization: Docker
Container Registry: DockerHub
Orchestration: Kubernetes (AWS EKS)
Cloud Provider: AWS
Monitoring: Prometheus & Grafana (Helm)

📁 Project Structure
trend-devops/
│── dist/                # Production build files (HTML, CSS, JS)
│── Dockerfile          # Docker image configuration
│── deployment.yaml     # Kubernetes Deployment
│── service.yaml        # Kubernetes Service (LoadBalancer)
│── Jenkinsfile         # CI/CD Pipeline
│── README.md           # Documentation

🔄 CI/CD Pipeline Flow
Code pushed to GitHub repository
Jenkins pipeline is triggered
Jenkins performs:
Clone repository
Build Docker image
Login to DockerHub
Push image to DockerHub
Deploy to Kubernetes
Kubernetes updates pods with new image
Application exposed via LoadBalancer
Monitoring enabled using Prometheus & Grafana

🐳 Docker Setup
Build Image
docker build -t niruban7/trend-app:latest .
Push to DockerHub
docker push niruban7/trend-app:latest

☸️ Kubernetes Deployment
Apply Deployment & Service
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
Verify
kubectl get pods
kubectl get svc
kubectl get nodes

🌐 Application Access

Application is exposed using a LoadBalancer service:

LoadBalancer URL:http://aaab014d8e2794f4eb4aac282b1bf3f9-978302595.ap-south-1.elb.amazonaws.com

📊 Monitoring Setup (Prometheus + Grafana)
Install using Helm
helm install monitoring prometheus-community/kube-prometheus-stack
Access Grafana
Service exposed via LoadBalancer / Port-forward
Default credentials:
Username: admin
Password: (retrieved via Kubernetes secret)
Monitoring Features
Node CPU & Memory usage
Pod metrics
Cluster health
Alerts capability

🎯 Key Achievements
✅ End-to-end CI/CD pipeline implemented
✅ Dockerized static web application
✅ Deployed on AWS EKS cluster
✅ Automated deployment using Jenkins
✅ Public access via LoadBalancer
✅ Monitoring using Prometheus & Grafana

🧠 Conclusion

This project demonstrates real-world DevOps practices including automation, containerization, orchestration, and monitoring, providing a strong foundation for scalable and reliable application deployment.
