# Event-Verse-3.0 MERN Application with Kubernetes and Minikube

All new and improved **Event-Verse-3.0**, a comprehensive event management system built with the MERN stack (MongoDB, Express.js, React.js, Node.js) and deployed using Docker and Kubernetes with Minikube. This project streamlines event organization and attendee engagement for various events like conferences, concerts, and corporate gatherings.

---

🌐 Project Overview
------------------

**EventVerse** is an all-in-one platform designed to manage the event lifecycle, connecting attendees, organizers, vendors, and sponsors. Inspired by platforms like Eventbrite, it offers features such as event creation, ticket management, attendee tracking, and analytics, with third-party integrations for payment gateways and social logins.

### Objectives
🔹 Provide a scalable, user-friendly platform for event management.  
🔹 Enable seamless interaction between attendees, organizers, vendors, and sponsors.  
🔹 Support event planning, ticketing, resource management, and post-event feedback.  

### Technologies Used
🔹 **Frontend**: React.js (v18.x or later)  
🔹 **Backend**: Node.js (v16.x or later), Express.js  
🔹 **Database**: MongoDB Atlas  
🔹 **Deployment**: Docker, Kubernetes, Minikube  
🔹 **CI/CD**: GitHub Actions  

---

🎉 Modules and Features
----------------------

### Attendee Module
- **User Registration & Login**: Secure sign-up with name, email, and preferences.  
- **Event Search & Booking**: Filter events by date, location, or type, and book tickets.  
- **Event Dashboard**: Track registered events, view schedules, and access details.  
- **Tickets & Check-In**: Download e-tickets and use QR-code-based check-in.  
- **Feedback & Ratings**: Submit post-event feedback and view past interactions.  
- **Profile Management**: Update personal details and event preferences.  

### Organizer Module
- **Registration & Event Creation**: Create and manage events with details like title, description, and ticket types.  
- **Ticket & Sales Management**: Set ticket categories, pricing, and monitor availability.  
- **Attendee Management**: Track attendees, communicate, and respond to queries.  
- **Resource & Vendor Management**: Assign resources and manage vendor contracts.  
- **Event Analytics**: Monitor ticket sales, attendee feedback, and engagement metrics.  

### Admin Module
- **User & Organizer Management**: Approve accounts and monitor activities.  
- **Event Approval & Category Management**: Approve events and manage categories.  
- **Reports & Analytics**: Generate reports on event metrics and platform growth.  
- **Feedback Moderation**: Ensure compliance and resolve disputes.  

### Vendor & Sponsor Module
- **Registration & Profile Setup**: Create detailed business profiles.  
- **Service & Sponsorship Bidding**: Bid for event contracts or sponsorships.  
- **Contract & Payment Management**: Track contracts and payment statuses.  
---

🛠️ Prerequisites
---------------

- Docker  
- Minikube  
- kubectl  
- Node.js (v18.x or later)  
- MongoDB Atlas account  

---

📁 Project Structure
-------------------

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

---

💻 Local Development
-------------------

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

---

🐳 Docker Build
--------------

Replace `your-dockerhub-username` with your Docker Hub username.

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

---

☸️ Kubernetes Deployment
-----------------------

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

---

🤖 GitHub Actions Setup
----------------------

- Add secrets to your GitHub repository (Settings > Secrets and variables > Actions):  
  🔹 `DOCKER_USERNAME`: Your Docker Hub username  
  🔹 `DOCKER_PASSWORD`: Your Docker Hub password or access token  
  🔹 `MONGODB_URI`: Your MongoDB Atlas connection string  
- Set up a self-hosted runner (Settings > Actions > Runners).  
- Push to the `main` branch to trigger deployment.

---

📊 Monitoring
------------

- **Check Pod Status**:  
  ```bash
  kubectl get pods -n scd-project
  ```
- **Check Services**:  
  ```bash
  kubectl get services -n scd-project
  ```
- **Check Deployments**:  
  ```bash
  kubectl get deployments -n scd-project
  ```

---

🛠️ Troubleshooting
-----------------

- **View Pod Logs**:  
  ```bash
  kubectl logs <pod-name> -n scd-project
  ```
- **Describe Resources**:  
  ```bash
  kubectl describe pod <pod-name> -n scd-project
  kubectl describe service <service-name> -n scd-project
  ```

---

🗑️ Cleanup
----------

- **Delete the Deployment**:  
  ```bash
  kubectl delete -f k8s/
  ```
- **Delete the Namespace**:  
  ```bash
  kubectl delete namespace scd-project
  ```
- **Stop Minikube**:  
  ```bash
  minikube stop
  ```

---


## 👨‍💻 Contributors
- **Abdullah Daoud (22I-2626)**  
- **Usman Ali (22I-2725)**  
- **Faizan Rasheed (22I-2734)**

---

## ⚖️ License
This project is for **academic and personal skill development purposes only**.  
Reuse is allowed for **learning and research** with proper credit.

---
