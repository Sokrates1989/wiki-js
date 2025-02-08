# Wiki.js with Docker Compose

This repository provides a simple setup to run **Wiki.js** with **PostgreSQL** using **Docker Compose**.

## Prerequisites

Ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Setup Instructions

### 1. Clone the Repository
```sh
git clone https://github.com/your-repo/wiki-docker-setup.git
cd wiki-docker-setup
```

### 2. Configure Environment Variables

Copy the provided `.env.template` file to `.env` and update the necessary values:

```sh
cp .env.template .env
```

Modify `.env` as needed:
```
PORT=3000
```

### 3. Start the Services

Run the following command to start Wiki.js and PostgreSQL:

```sh
docker-compose up -d
```

This will:

- Start a **PostgreSQL 15** container for the Wiki.js database.
- Start a **Wiki.js** container that connects to the database.

### 4. Access Wiki.js

Once the containers are running, open your browser and visit:

```
http://localhost:3000
```

(Change the port if you've modified it in the `.env` file.)

### 5. Stopping the Services

To stop the containers, run:

```sh
docker-compose down
```

### 6. Persistent Storage

- The PostgreSQL database is stored in `./db_data`, ensuring data persistence across restarts.
- To completely remove all data, delete the `db_data` directory.

### 7. Logs & Troubleshooting

Check container logs:

```sh
docker-compose logs -f
```

Restart a specific service:

```sh
docker-compose restart wiki
```

---

## Notes

- Ensure **port 3000** (or the configured port) is not in use by another service.
- Use a **stronger password** instead of `wikijsrocks` in production.
- To upgrade Wiki.js, update the **Docker image version** in `docker-compose.yml` and restart the containers.

Enjoy your self-hosted Wiki! 🚀
