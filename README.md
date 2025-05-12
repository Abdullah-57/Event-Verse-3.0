# Event-Verse-3.0 MERN Application with Kubernetes and Minikube

All new and improved Event-Verse-3.0 MERN Web App with support of Docker and Kubernetes for easy deployment. This project demonstrates a MERN (MongoDB, Express.js, React.js, Node.js) application deployed using Kubernetes and Minikube.

## Prerequisites

Ensure the following tools are installed on your machine:

- Docker
- Minikube
- kubectl
- Node.js 18+
- MongoDB Atlas account (for the database)

## Project Structure

```plaintext
.
├── frontend/                   # React frontend application
├── backend/                    # Node.js backend application
├── k8s/                        # Kubernetes configuration files
│   ├── frontend-deployment.yaml
│   ├── backend-deployment.yaml
│   ├── frontend-service.yaml
│   ├── backend-service.yaml
│   └── mongo.yaml
└── .github/
    └── workflows/
        └── deploy.yml
```

## Local Development

### Start the Frontend

```bash
cd frontend
npm install
npm run dev
```

### Start the Backend

```bash
cd backend
npm install
npm start
```

## Docker Build

Replace `your-dockerhub-username` with your Docker Hub username in the commands below.

### Build Frontend Image

```bash
cd frontend
docker build -t your-dockerhub-username/mern-frontend:latest .
```

### Build Backend Image

```bash
cd backend
docker build -t your-dockerhub-username/mern-backend:latest .
```

## Kubernetes Deployment

### Start Minikube

```bash
minikube start
```

### Create Namespace

```bash
kubectl create namespace scd-project
```

### Create MongoDB Secret

Replace `your-mongodb-uri` with your MongoDB Atlas connection string.

```bash
kubectl create secret generic mongodb-secret --namespace scd-project --from-literal=uri=your-mongodb-uri
```

### Deploy the Application

```bash
cd k8s
kubectl apply -f frontend-deployment.yaml
kubectl apply -f backend-deployment.yaml
kubectl apply -f frontend-service.yaml
kubectl apply -f backend-service.yaml
kubectl apply -f mongo.yaml
```

### Access the Application

```bash
minikube service frontend-service -n scd-project
```

## GitHub Actions Setup

1. Add the following secrets to your GitHub repository (Settings &gt; Secrets and variables &gt; Actions):

   - `DOCKER_USERNAME`: Your Docker Hub username
   - `DOCKER_PASSWORD`: Your Docker Hub password or access token
   - `MONGODB_URI`: Your MongoDB Atlas connection string

2. Set up a self-hosted runner on the machine where Minikube is running. Follow the instructions in your repository’s Settings &gt; Actions &gt; Runners.

3. Push your code to the `main` branch to trigger the deployment.

## Monitoring

### Check Pod Status

```bash
kubectl get pods -n scd-project
```

### Check Services

```bash
kubectl get services -n scd-project
```

### Check Deployments

```bash
kubectl get deployments -n scd-project
```

## Troubleshooting

### View Pod Logs

Replace `<pod-name>` with the name of the pod (obtained from `kubectl get pods -n mern-app`).

```bash
kubectl logs <pod-name> -n scd-project
```

### Describe Resources

```bash
kubectl describe pod <pod-name> -n scd-project
kubectl describe service <service-name> -n scd-project
```

## Cleanup

### Delete the Deployment

```bash
kubectl delete -f k8s/
```

### Delete the Namespace

```bash
kubectl delete namespace scd-project
```

### Stop Minikube

```bash
minikube stop
```