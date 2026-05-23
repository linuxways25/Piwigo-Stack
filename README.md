This repository contains the multi-container configuration for deploying Piwigo, an open-source photo gallery software, using Docker Compose. The stack is architected to run Piwigo behind an Nginx reverse proxy with a MariaDB backend database, engineered for high performance and isolation.

🏗️ Architecture Overview
The application environment is split into distinct, isolated services:

Piwigo Application: The core PHP-driven photo gallery engine.

Nginx Proxy: Handles incoming web traffic, manages SSL/TLS termination (optional), and serves static assets efficiently.

MariaDB Database: High-performance relational database storage for photo metadata, user accounts, and configurations.

Redis Cache (Planned): In-memory data store to be integrated in future releases for session handling and database query caching to speed up high-traffic instances.
