# Apache Docker Boilerplate

A professional, production-ready web starter kit using **Apache (httpd)** and **Docker**. This project is fully automated and designed to be highly customizable via environment variables.

## 🌟 Features
- **Apache (httpd)**: Industry-standard high-performance web server.
- **Docker Compose**: One-command orchestration for building and running.
- **Dynamic Paths**: Change your source code folder without touching the Dockerfile.
- **Environment Driven**: Fully configurable through a simple `.env` file.

---

## ⚙️ Configuration Guide

Follow these steps to customize your environment **before** launching the server.

### Step 1: The Environment File (`.env`)
The `.env` file acts as your control panel. You can modify the project behavior without touching the core code:

* **`HOST_PORT`**: The port you will type in your browser (e.g., `8080`). Change this if another app is already using that port on your machine.
* **`APP_PATH`**: **The local path to your website files.** By default, it points to `./app`. If you want to use a different folder for your HTML/CSS, update this path here.
* **`CONTAINER_NAME`**: The specific name that will appear in your Docker container list.
* **`IMAGE_NAME`**: The name used for the generated Docker image.

### Step 2: Source Code Setup
Place your web assets (HTML, CSS, JavaScript) inside the folder defined by `APP_PATH` (default is the `/app` folder).
* **Note**: Ensure your main file is named `index.html`, as Apache looks for this specific filename to serve your site.

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

1.  **Prerequisites**: Ensure **Docker** is installed and running.
2.  **Customization**: Edit the `.env` file to set your preferred ports and paths.
3.  **Run**: Execute `docker compose up -d`.
4.  **View**: Open **[http://localhost:8080](http://localhost:8080)** (or your custom port).

## 📂 Project Structure
```text
.
├── app/                # Default directory for your web files
├── .env                # Centralized configuration (Ports, Paths, Names)
├── .gitignore          # Git exclusion rules
├── docker-compose.yml  # Master orchestration file (bridges .env and Docker)
├── Dockerfile          # Custom Apache image recipe (using build args)
└── README.md           # Documentation

## 🛠 Useful Commands

| Action | Command |
| :--- | :--- |
| **Start server** | `docker compose up -d` |
| **Stop server** | `docker compose down` |
| **Rebuild after changes** | `docker compose up -d --build` |
| **View logs** | `docker compose logs -f` |
| **Check status** | `docker compose ps` |