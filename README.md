# 🐳 Three-Tier Web Application using Docker

- This project demonstrates a complete **Three-Tier Web Application** architecture using **Docker containers**.
- The architecture includes a **front-end (NGINX)**, **application server (Tomcat)**, and **back-end database (MySQL)** – all orchestrated using **Docker and Docker Compose**.

---

## 🔧 Architecture Overview

A standard **three-tier application** broken into:

1. **Presentation Layer (Frontend):**
   - NGINX as a reverse proxy
   - Serves static content and routes requests to the application layer

2. **Application Layer (Backend):**
   - Tomcat (Java app) 
   - Handles business logic and API processing

3. **Data Layer (Database):**
   - MySQL container
   - Stores and manages data persistently using volumes

---

## 📦 Technologies Used

- **Docker** & **Docker Compose**
- **NGINX** – Web server and reverse proxy
- **Tomcat** – Application logic layer
- **MySQL** – Relational database
- **Linux Shell Scripting** – Automation and setup
- **Custom Docker Networks & Volumes**

---

## 📁 Project Structure

```
three-tier-using-docker/
│
├── docker-compose.yml         # Orchestrates all services
├── nginx/
│   └── default.conf           # NGINX reverse proxy config
├── app/
│   └── index.jsp              # App server code (Java or HTML)
├── db/
│   └── init.sql               # Initial database script (optional)
└── README.md                  # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites
- Docker & Docker Compose installed
- Git installed (to clone this repo)



## 🔍 Troubleshooting

- Ensure ports `80`, `3306`, and ``8080`` ports are not used by other services.
- Check logs using:
  ```bash
  docker-compose logs -f
  ```

---

## 📚 Learning Highlights

- Building and linking Docker containers for multi-tier architecture
- NGINX as a reverse proxy and load balancer
- Isolated Docker networks for secure communication between tiers
- Persistent MySQL storage using volumes

---

## 🙋‍♀️ Author

**Tejaswini Shirke**  
GitHub: [Tejaswini2704](https://github.com/Tejaswini2704)

---

## 🙌 Connect with Me

If you like this project or have any questions, feel free to connect:

👤 **Tejaswini**  
- 🔗 [LinkedIn Profile](https://www.linkedin.com/in/tejaswini-shirke-85aa3a27a)
- 🔗 [GitHub](https://github.com/Tejaswini2704)  
- 📧 shirketejaswini10@gmail.com 
## ⭐ Like it?

If you found this helpful, star the repository and share it with your network!
