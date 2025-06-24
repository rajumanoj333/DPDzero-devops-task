### 🧪 **DevOps Intern Assignment: Nginx Reverse Proxy + Docker**

## 🚀 Project Overview

This project demonstrates a simple microservices setup using Docker Compose. It features:

- **Two backend services** (one in Go, one in Python/Flask), each running in its own container.
- An **Nginx reverse proxy** (also containerized) that routes requests based on URL path prefix.
- All services accessible via a single port (`localhost:8080`).

---

## 📁 Project Structure

```
.
├── docker-compose.yml
├── nginx
│   └── default.conf
├── service_1
│   ├── main.go
│   └── Dockerfile
├── service_2
│   ├── app.py
│   └── Dockerfile
└── README.md
```

---

## ⚙️ Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone 
   cd 
   ```

2. **Build and Start All Services**
   ```bash
   docker-compose up --build
   ```

3. **Test the Endpoints**
   Open a new terminal and run:
   ```bash
   curl http://localhost:8080/service1/ping
   curl http://localhost:8080/service2/ping
   curl http://localhost:8080/service1/hello
   curl http://localhost:8080/service2/hello
   ```

   **Expected Responses:**
   - `/service1/ping` → `{"status":"ok","service":"1"}`
   - `/service2/ping` → `{"status":"ok","service":"2"}`
   - `/service1/hello` → `{"message":"Hello from Service 1"}`
   - `/service2/hello` → `{"message":"Hello from Service 2"}`

4. **Stop All Services**
   ```bash
   docker-compose down
   ```

---

## 🌐 Routing Explained

- **Nginx** listens on port `8080`.
- Requests to `/service1/*` are routed to the Go backend (`service_1`).
- Requests to `/service2/*` are routed to the Flask backend (`service_2`).
- This routing is defined in [`nginx/default.conf`](nginx/default.conf).

---

## 🩺 Health Checks

- Both backend services have health checks defined in `docker-compose.yml` using their `/ping` endpoints.
- You can verify health status with:
  ```bash
  docker ps
  ```
  Look for `healthy` in the `STATUS` column.

---

## 📜 Logging

- Nginx logs each incoming request with timestamp and path.
- View logs with:
  ```bash
  docker-compose logs nginx
  ```

---

## 🏗️ Tech Stack

- **Go** (service_1)
- **Python/Flask** (service_2)
- **Nginx** (reverse proxy)
- **Docker & Docker Compose**

---

## 🏅 Bonus Features

- Health checks for both backend services.
- Clean, modular Docker setup.
- Easy, single-command startup.

---

## 📦 How Routing Works

| Path Prefix    | Routed To      | Example Response                        |
|----------------|---------------|-----------------------------------------|
| `/service1/*`  | Go service    | `{"status":"ok","service":"1"}`         |
| `/service2/*`  | Flask service | `{"status":"ok","service":"2"}`         |

---

## 📝 Notes

- Nginx runs **inside a Docker container** (not on host).
- Uses Docker’s **bridge networking** (default in Compose).
- All services are accessible via **localhost:8080**.

---

## 💡 Tips

- To see logs for a specific service:
  ```bash
  docker-compose logs service_1
  docker-compose logs service_2
  ```
- To follow logs live:
  ```bash
  docker-compose logs -f nginx
  ```

---

## 📚 References

- [Docker Compose Documentation](https://docs.docker.com/compose/)
- [Nginx Documentation](https://nginx.org/en/docs/)

---

> **Ready to go!**  
> Just run `docker-compose up --build` and access all services through Nginx on port 8080.

---

**Replace `` and `` with your actual repository details.**  
This README covers all your assignment requirements and is ready for submission or sharing!

[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/55408003/ac073a19-0ca9-4772-9477-d2ce14f774ad/main.go
[2] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/55408003/fc45a278-abcf-4a2f-b968-d8f6d9546b14/app.py
[3] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/55408003/24194d04-ebea-44f1-9ca4-c5f5b73262f2/pyproject.toml
