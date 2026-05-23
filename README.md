This repository contains the multi-container configuration for deploying Piwigo, an open-source photo gallery software, using Docker Compose. The stack is architected to run Piwigo behind an Nginx reverse proxy with a MariaDB backend database, engineered for high performance and isolation.

🏗️ Architecture Overview
The application environment is split into distinct, isolated services:

Piwigo Application: The core PHP-driven photo gallery engine.

Nginx Proxy: Handles incoming web traffic, manages SSL/TLS termination (optional), and serves static assets efficiently.

MariaDB Database: High-performance relational database storage for photo metadata, user accounts, and configurations.

Redis Cache (Planned): In-memory data store to be integrated in future releases for session handling and database query caching to speed up high-traffic instances.


📁 Project Directory Structure
piwigo-stack/
├── docker-compose.yml
├── .env                    # System hidden folder which stores passwords and environment vars
├── gallery/                # Your local photo & media library folder
├── piwigo-config/         # Custom database configs (e.g., custom.cnf)
├── mariadb-config/          # <-- Your local Piwigo configuration overrides & DB credentials
├── nginx/
│   └── default.conf        # Reverse proxy routing rules
└── redis/
    └── redis.conf          # Custom Redis configurations (optional)

🛠️ Technology Stack: 
This project implements a multi-container architecture using a modern, high-performance web-serving stack:

Core Application Layer| Piwigo (Latest): The open-source, PHP-based photo gallery application engine managing user sessions, albums, permissions, and media plugins.
PHP-FPM: Handles fast dynamic server-side processing for the Piwigo backend inside the application layer.  

Infrastructure & Orchestration|
Docker: Used to containerize each architectural component into isolated, reproducible, lightweight environments.
Docker Compose: Orchestrates multi-container execution, managing service networking, persistent volumes, environment variables, and startup sequences.

Performance & Routing (Reverse Proxy)| Nginx: Serving as an edge reverse proxy and web server. It handles incoming traffic, manages secure SSL/TLS termination, and directly caches static image payloads to reduce application load.  

Storage & Caching Layer|
MariaDB: A relational SQL database system used to store and manage critical metadata, gallery configurations, user tables, and tags.
Redis: An in-memory, key-value data store utilized for object caching, helping speed up recurring database queries and accelerating album load times.  
