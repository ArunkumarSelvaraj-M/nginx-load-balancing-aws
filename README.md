# NGINX Load Balancing on AWS EC2

## 📌 Overview
This project demonstrates **NGINX Load Balancing** using multiple algorithms on an **AWS EC2 instance**. The load balancer distributes traffic among backend servers using different strategies like:
- **Round Robin**
- **Least Connections**
- **IP Hash**
- **Weighted Load Balancing**

## Load balancing algorithms
Load balancing algorithms are used to distribute incoming network traffic across multiple servers to ensure no single server is overwhelmed. Here are some common load balancing algorithms:

**1. Static Load Balancing Algorithms**
These do not consider the current load of servers; they follow predefined rules.

- **Round Robin:** Requests are distributed sequentially to each server in the pool.
- **Weighted Round Robin:** Assigns a weight to each server, with higher-weighted servers getting more requests.
- **IP Hashing:** Uses a hash function based on the client’s IP address to direct traffic to a specific server.

**2. Dynamic Load Balancing Algorithms**
These consider the current load of servers before distributing traffic.

- **Least Connections:** Sends traffic to the server with the fewest active connections.
- **Least Response Time:** Directs traffic to the server with the lowest response time.
- **Least Bandwidth:** Chooses the server consuming the least network bandwidth.
- **Weighted Least Connections:** Similar to Least Connections but considers server capacity (weight).

**3. Adaptive Load Balancing Algorithms**
These use machine learning or predictive analytics.

- **Resource-Based (Adaptive):** Monitors server health and adjusts traffic accordingly.
- **Load-Based (Dynamic Ratio):** Continuously updates server performance metrics to optimize traffic distribution.

**4. Other Advanced Algorithms**

- **URL Hashing:** Routes requests based on the URL hash to maintain session consistency.
- **Geolocation-Based:** Directs users to the nearest data center based on geographic location.

## 🛠️ Technologies Used
- **NGINX** (as a Reverse Proxy and Load Balancer)
- **AWS EC2** (Ubuntu instance)
- **Python HTTP Server** (as backend servers)
- **Git & GitHub** (for version control)

---

## ⚡ Setup Guide

### **1️⃣ Install NGINX on EC2**
Run these commands on your EC2 instance (Ubuntu):
```sh
sudo apt update
sudo apt install nginx git -y
```

### **2️⃣ Clone and Configure NGINX Load Balancing**
Copy the nginx.conf file to /etc/nginx/:
```sh
sudo git clone https://github.com/ArunkumarSelvaraj-M/nginx-load-balancing-aws.git
cd nginx-load-balancing-aws/
sudo cp nginx.conf /etc/nginx/nginx.conf
```

Test and restart NGINX:
```sh
sudo nginx -t
sudo systemctl restart nginx
```

### **3️⃣ Start Backend Servers**
On your EC2 instance, start simple backend servers:
```sh
cd nginx-load-balancing-aws/services/service-1 && python3 -m http.server 8081 &
cd nginx-load-balancing-aws/services/service-2 && python3 -m http.server 8082 &
cd nginx-load-balancing-aws/services/service-3 && python3 -m http.server 8083 &
```

### **4️⃣ Verify Load Balancing**
Run:
```sh
curl http://your-ec2-public-ip:80/round_robin
curl http://your-ec2-public-ip:80/least_conn
curl http://your-ec2-public-ip:80/ip_hash
curl http://your-ec2-public-ip:80/weighted
```

### **🚀 Deployment on AWS**

- Step 1: Launch an EC2 instance (Ubuntu)
- Step 2: Install NGINX, Git and Python
- Step 3: Clone this repo and configure NGINX
- Step 4: Start backend servers
- Step 5: Test load balancing using curl or a browser

### **🔥 Future Enhancements**

- Implement Auto Scaling with AWS.
- Add SSL/TLS with Let's Encrypt.
- Deploy Dockerized NGINX and Backends.

### **🤝 Contributing**
Feel free to submit issues and pull requests to improve this project.
