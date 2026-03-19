# Dockerized-Application-Deployment-Node.js-Docker-VirtualBox-
 This project demonstrates how to containerize and deploy a simple Node.js application using Docker in a Linux (Ubuntu) environment hosted on VirtualBox. The goal is to simulate a real-world DevOps workflow by packaging an application into a portable container and running it consistently across environments.

 ##  Objectives

* Containerize a Node.js application using Docker
* Build and manage Docker images
* Deploy and run containers in a Linux environment
* Expose application services via port mapping
* Validate application accessibility and portability

---

##  Environment Setup

* **Platform:** VirtualBox
* **OS:** Ubuntu Server 22.04
* **Container Engine:** Docker
* **Application:** Node.js

---

##  Application Code

### app.js

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  res.end('Hello from Docker on VirtualBox!');
});

server.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

---

## Dockerfile

```Dockerfile
FROM node:18

WORKDIR /app

COPY . .

RUN npm install

EXPOSE 3000

CMD ["node", "app.js"]
```

---

##  Steps Implemented

### 1. Installed Docker

```bash
sudo apt install docker.io -y
```

### 2. Started and Enabled Docker

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### 3. Built Docker Image

```bash
docker build -t docker-app .
```

### 4. Ran Docker Container

```bash
docker run -d -p 3000:3000 docker-app
```

---

##  Accessing the Application

1. Retrieve VM IP address:

```bash
ip a
```

2. Open in browser:

```
http://<VM-IP>:3000
```

---

##  Verification

Check running containers:

```bash
docker ps
```

---

##  Container Management

Stop container:

```bash
docker stop <container_id>
```

Restart container:

```bash
docker restart <container_id>
```

Remove container:

```bash
docker rm -f <container_id>
```

---

##  Restart Policy

To ensure availability:

```bash
docker run -d -p 3000:3000 --restart unless-stopped docker-app
```

---

##  Testing & Validation

* Verified application accessibility via browser
* Tested container restart and redeployment
* Confirmed consistent behavior across runs

---

##  Results

* Successfully containerized a Node.js application
* Built reusable Docker images
* Deployed application in a Linux environment
* Ensured consistent and reliable application execution

---

##  Key Concepts Learned

* Docker images and containers
* Application containerization
* Port mapping and networking
* Container lifecycle management
* Deployment consistency
