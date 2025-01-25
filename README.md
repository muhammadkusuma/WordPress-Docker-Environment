# WordPress Docker Environment

A simple setup to run WordPress locally using Docker and Docker Compose with a custom local domain.

## Features
- WordPress with the latest version
- MySQL as the database
- Persistent storage for WordPress files and database
- Custom local domain for easier development (`mylocalwordpress.local`)

---

## Prerequisites
- Docker (https://www.docker.com/)
- Docker Compose (included with Docker Desktop)
- Basic knowledge of editing the `hosts` file

---

## Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/muhammadkusuma/wordpress.git
cd wordpress
```

### 2. Edit Local Hosts File
Add the following line to your `hosts` file:
```
127.0.0.1 mylocalwordpress.local
```
- **Linux/Mac**: Edit `/etc/hosts`
- **Windows**: Edit `C:\Windows\System32\drivers\etc\hosts`

### 3. Start the Containers
Run the following command to start WordPress and MySQL:
```bash
docker compose up -d
```

### 4. Access WordPress
Open your browser and visit:
```
http://mylocalwordpress.local:8080
```

Follow the WordPress setup wizard.

---

## File Structure
```
.
├── docker-compose.yml  # Docker configuration file
├── wordpress/          # Persistent data for WordPress
└── README.md           # Project documentation
```

---

## Stopping and Cleaning Up
To stop the containers:
```bash
docker compose down
```

To remove all data (optional):
```bash
docker compose down -v
```

---

## Notes
- **Custom Domain**: If you prefer a different domain, update the `hosts` file and access WordPress accordingly.
- **Ports**: The setup uses port `8080`. You can change it in `docker-compose.yml` if needed.
- **SSL (Optional)**: Consider adding SSL for development using tools like [mkcert](https://github.com/FiloSottile/mkcert).

---

## Troubleshooting
1. **Port Conflict**: If `8080` is in use, change the port mapping in `docker-compose.yml`:
   ```yaml
   ports:
     - "8081:80" # Replace 8081 with an available port
   ```
2. **Database Connection Issues**: Ensure the `db` service is running and check `WORDPRESS_DB_*` environment variables in `docker-compose.yml`.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Author
Created by [M. WIRA ADE KUSUMA](https://github.com/muhammadkusuma).
