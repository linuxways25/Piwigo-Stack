This repository contains the multi-container configuration for deploying Piwigo, an open-source photo gallery software, using Docker Compose. The stack is architected to run Piwigo behind an Nginx reverse proxy with a MariaDB backend database, engineered for high performance and isolation.

**🏗️ Architecture Overview**
The application environment is split into distinct, isolated services:

Piwigo Application: The core PHP-driven photo gallery engine.

Nginx Proxy: Handles incoming web traffic, manages SSL/TLS termination (optional), and serves static assets efficiently.

MariaDB Database: High-performance relational database storage for photo metadata, user accounts, and configurations.

Redis Cache (Planned): In-memory data store to be integrated in future releases for session handling and database query caching to speed up high-traffic instances.


**📁 Project Directory Structure**
piwigo-stack/
│
├── docker-compose.yml
├── .env
│
├── gallery/                    # Photo & media library storage
│
├── piwigo-config/              # Piwigo custom configs & overrides
│
├── mariadb-config/             # MariaDB custom configs (custom.cnf)
│
├── nginx/
│   └── default.conf            # Reverse proxy configuration
│
├── redis/
│   └── redis.conf              # Redis tuning & cache configs
│
├── prometheus/
│   └── prometheus.yml          # Prometheus scrape configuration
│
├── grafana/
│   ├── provisioning/
│   └── dashboards/
│
├── monitoring/
│   ├── cadvisor/
│   └── node-exporter/
│
└── logs/
    ├── nginx/
    ├── piwigo/
    └── prometheus/

**🛠️ Technology Stack:** 
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

**Monitoring & Observability Stack**

Piwigo environment can become much more production-ready by integrating a complete monitoring and observability stack.

This setup gives you:

📊 Real-time metrics
📦 Container monitoring
🖥️ Server monitoring
🚨 Alerting capability
📈 Beautiful dashboards
🔍 Better troubleshooting visibility

**Core Application Stack**

Container	              Purpose
Piwigo	            Photo management application
MariaDB	            Database backend
Redis               Cache/session acceleration
NGINX               Reverse proxy
Docker Networks	    Secure container communication

**📊 Monitoring & Observability Stack**

Component	              Role
Prometheus:	        Metrics collection & scraping
Grafana:	            Dashboards & visualization
Node Exporter:	    Linux host metrics
cAdvisor:	        Docker container metrics


**🌐 Recommended Docker Networks**

I have created a separate monitoring network that is a very good production-style approach.

**Suggested Networks**
    Network	                            Purpose
piwigo-network: 	            App containers communication
monitoring-network: 	        Monitoring stack communication

