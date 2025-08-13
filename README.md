
# 🐳 DevOps Reverse Proxy Assignment

This project sets up a **Docker Compose-based microservice system** with:
- A Go backend service (`service_1`)
- A Python Flask backend service (`service_2`)
- An Nginx reverse proxy routing requests to the above services

---

## 🌐 What is Nginx?

**Nginx** is a high-performance web server and reverse proxy. In simple terms:

- It can serve static content (like HTML, CSS)
- It can **act as a gateway** that forwards client requests to internal services
- It's commonly used for **load balancing**, **security**, and **URL routing**

In this project, **Nginx works as a reverse proxy** — it listens on a single port (`8080`) and routes incoming requests to:
- the Go service (`/service1/...`)
- the Python Flask service (`/service2/...`)

---

##  Setup Instructions

1. **Clone or download the repository**
2. Make sure you have **Docker** and **Docker Compose** installed.
3. Run the project using:

```bash
docker-compose up --build
```

4. Test the endpoints:

```bash
# Go Service (Service 1)
http://localhost:8080/service1/hello
http://localhost:8080/service1/ping

# Python Flask Service (Service 2)
http://localhost:8080/service2/hello
http://localhost:8080/service2/ping
```

---

## How Routing Works

All requests go through **Nginx**, running in a container on port `8080`.

Nginx routes based on URL prefix:

| URL Path Prefix     | Service              |
|---------------------|----------------------|
| `/service1/*`       | Go App (`8001`)      |
| `/service2/*`       | Flask App (`8002`)   |

### Example:

- `GET /service1/hello` → Proxied to Go app's `/hello` endpoint  
- `GET /service2/ping` → Proxied to Flask app's `/ping`

---

## Bonus Implemented

- Health checks using `curl`
- Structured Nginx logging with timestamp, request path, and status
- Clean Dockerfile separation for each service and Nginx
- Single-command system startup

---

## 🛠 Tech Stack

- Go (service 1)
- Python Flask (service 2)
- Nginx (reverse proxy)
- Docker & Docker Compose

---

## Author

Ronit Thakur
