
# 🚀 Project 5: Containerize and Deploy Node.js App with Docker on AWS EC2

## 📌 Problem Statement

Traditional software deployments can be error-prone and complex. Docker enables packaging applications with all dependencies for consistent, scalable, and fast deployment. This project showcases how to containerize a simple Node.js app and deploy it using Docker on an AWS EC2 instance.

---

## 🎯 Objective

- Build and containerize a basic Node.js web app.
- Deploy it to an EC2 Ubuntu server using Docker.
- Access the app publicly through EC2’s IP and exposed port.

---

## 🛠️ Tech Stack

- Node.js + Express.js
- Docker
- AWS EC2 (Ubuntu)
- Git & GitHub

---

## 📁 Project Structure

```
cloud-project-5/
│
├── Dockerfile
├── package.json
├── index.js
├── dockerfile-output.txt         ← terminal log (optional)
└── docker-build-output.txt       ← build log (optional)
```

---

## ⚙️ Dockerfile (Highlights)

```Dockerfile
FROM node:18
WORKDIR /usr/src/app
COPY package.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

---

## 🚀 Deployment Steps

### ✅ Step 1: Launch EC2 Instance
- Ubuntu 20.04 or later
- Choose or create key pair (`.pem` file)
- Allow SSH and Custom TCP (e.g., port 9999) in security group

### ✅ Step 2: SSH into EC2 and install Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

### ✅ Step 3: Upload Project Files (from local to EC2)

```bash
scp -i "your-key.pem" -r ./cloud-project-5 ubuntu@<your-ec2-ip>:~/
```

### ✅ Step 4: Build Docker Image

```bash
cd ~/cloud-project-5
docker build -t node-docker-app .
```

### ✅ Step 5: Run Docker Container

```bash
docker run -d -p 9999:3000 node-docker-app
```

### ✅ Step 6: Open App in Browser

```
http://<your-ec2-ip>:9999
```

✅ Example:  
[http://13.232.90.108:9999](http://13.232.90.108:9999)

---

## 📸 Screenshot Suggestions

| Screenshot | Where to Capture |
|------------|------------------|
| ✅ EC2 Instance Dashboard | AWS Console → EC2 → Instances |
| ✅ Inbound Rules for port 9999 | EC2 → Security Group → Inbound Rules |
| ✅ Terminal: `cat Dockerfile` | Show Dockerfile content |
| ✅ Terminal: `docker build` | Show successful image build |
| ✅ Terminal: `docker ps` | Show running container and ports |
| ✅ Web Browser | Final deployed app in browser using public IP |

---

## ✅ Learning Outcomes

- Learned how to build and run Docker containers
- Understood port mapping and containerization
- Successfully deployed a backend app on EC2
- Gained confidence using Docker + AWS in real-world setups

---

## 🙌 Author

**Omm Sawant**  
Cloud Computing Internship — Project 5
# cloud-project-5
