# 🐳 Node.js + Nginx Load Balancer (Dockerized)

This project demonstrates a simple **containerized infrastructure** using:

- Multiple Node.js instances
- Nginx as a reverse proxy + load balancer
- Docker Compose orchestration

Everything runs inside Docker — no need to install Nginx locally.

---

## 📦 Architecture

```
Client
  ↓
Nginx (Reverse Proxy)
  ↓
Node Cluster
 ├── app1
 ├── app2
 └── app3
```

Nginx distributes incoming requests between three Node.js instances using round-robin load balancing.

---

## 🚀 Features

- Fully dockerized setup
- Reverse proxy with Nginx
- Load balancing across multiple Node apps
- Scalable architecture
- No local Nginx installation required
- Production-like infrastructure pattern

---

## 📁 Project Structure

```
.
├── server.js
├── index.html
├── package.json
├── Dockerfile
├── Dockerfile.nginx
├── nginx.conf
└── docker-compose.yml
```

---

## 🧠 How It Works

Each Node.js container serves the same HTML page but identifies itself via an environment variable:

```
APP_NAME=App1
APP_NAME=App2
APP_NAME=App3
```

Nginx routes incoming requests to one of these instances.

When refreshing the page multiple times, you'll see different instances handling requests (check logs).

---

## ▶️ Running the Project

### 1. Build and start containers

```bash
docker-compose up --build
```

---

### 2. Access the app

Open:

```
http://localhost:8080
```

Nginx will forward traffic to one of the Node.js instances.

---

### 3. Check logs (optional)

To see load balancing in action:

```bash
docker-compose logs -f
```

You should see responses like:

```
Request served by App1
Request served by App2
Request served by App3
```

---

## 🛑 Stopping the Project

To stop and remove containers:

```bash
docker-compose down
```

To remove everything (containers + volumes):

```bash
docker-compose down -v
```

---

## 📈 Scaling

You can easily scale the Node cluster:

```bash
docker-compose up --scale app1=2 --scale app2=2 --scale app3=2
```

Just remember to update the Nginx upstream block if needed.

---

## 🎯 Purpose

This project is intended for:

- Learning reverse proxy concepts
- Understanding container networking
- Practicing load balancing
- Simulating production-like setups locally

---

## 📄 License

MIT
