# Apache, SQL and PHPMyAdmin Docker Boilerplate

A professional, production-ready web starter kit using **Apache**, **PHP**, and **MySQL**. This project is fully automated and designed to be highly customizable via environment variables.

## 🌟 Features
- **PHP 8.2 & Apache**: Industry-standard high-performance dynamic web server.
- **MySQL 8.0**: Persistent database storage using Docker volumes.
- **PHPMyAdmin**: Web-based interface for easy database management with auto-login enabled.
- **Docker Compose**: One-command orchestration for building and running.
- **Dynamic Paths**: Change your source code folder without touching the Dockerfile.
- **Environment Driven**: Fully configurable through a simple `.env` file.

---

## ⚙️ Configuration Guide

Follow these steps to customize your environment **before** launching the server.

### Step 1: The Environment File (`.env`)
The `.env` file acts as your control panel. You can modify the project behavior without touching the core code:

* **`COMPOSE_PROJECT_NAME`**: Defines the prefix for all your project containers.
* **`HOST_PORT`**: The port you will type in your browser (e.g., `8080`) to access your website.
* **`APP_PATH`**: **The local path to your website files.** By default, it points to `./app`.
* **`CONTAINER_NAME`**: The specific name that will appear in your Docker container list for the web server.
* **`IMAGE_NAME` & `IMAGE_TAG`**: Define how your generated web image is named and versioned.
* **`DB_ROOT_PASSWORD`**: Master password for the MySQL root user.
* **`DB_NAME`, `DB_USER`, `DB_PASSWORD`**: Your specific database credentials.
* **`PMA_HOST_PORT`**: The port used to access PHPMyAdmin (default: `8081`).

### Step 2: Source Code Setup
Place your web assets (PHP, HTML, CSS, JavaScript) inside the folder defined by `APP_PATH` (default is the `./app` folder).
* **Note**: Ensure your main file is named `index.php` or `index.html`.

### Step 3: Deployment
Once your configuration is set, use the following commands to manage your project:

* **Initial Launch**: 
    ```bash
    docker compose up -d
    ```
* **Applying Changes**: If you modify the `.env` file or the `Dockerfile`, you must tell Docker to rebuild the image to take those changes into account:
    ```bash
    docker compose up -d --build
    ```

---

## 🚀 Quick Start Summary

1.  **Clone this specific branch**:
    ```bash
    git clone -b feature/full-stack [https://github.com/Maanaaa/hello-docker-web.git](https://github.com/Maanaaa/hello-docker-web.git) .
    ```
2.  **Prerequisites**: Ensure **Docker** is installed and running.
3.  **Customization**: Edit the `.env` file to set your preferred ports, paths, and database credentials.
4.  **Run**: Execute `docker compose up -d`.
5.  **View Website**: Open **[http://localhost:8080](http://localhost:8080)**.
6.  **View Database**: Open **[http://localhost:8081](http://localhost:8081)** (Auto-login enabled).

## 📂 Project Structure
```text
.
├── app/                # Default directory for your web files (PHP/HTML)
├── .env                # Centralized configuration (Ports, DB credentials, Paths)
├── .gitignore          # Git exclusion rules
├── docker-compose.yml  # Master orchestration file
├── Dockerfile          # Custom PHP + Apache image recipe
└── README.md           # Documentation
```

## 🛠 Useful Commands

| Action | Command |
| :--- | :--- |
| **Start all services** | `docker compose up -d` |
| **Stop & Remove containers** | `docker compose down` |
| **Rebuild & Refresh stack** | `docker compose up -d --build` |
| **Check live logs** | `docker compose logs -f` |
| **Check container status** | `docker compose ps` |
| **Reset Database** (Warning: Wipes all data) | `docker compose down -v` |
| **Access MySQL container** | `docker exec -it hello_docker_web_db bash` |
