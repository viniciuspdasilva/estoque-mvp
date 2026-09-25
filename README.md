# Inventory MVP Orchestrator

This repository orchestrates the Inventory Management MVP, consisting of a FastAPI backend and a static HTML/JS frontend. It uses Docker Compose to manage the services, including a PostgreSQL database.

## Project Structure

- `ecommerce-inventory-api/`: FastAPI backend service.
- `estoque-mvp-estatico/`: Static frontend service (HTML, CSS, JS) served by Nginx.
- `docker-compose.yml`: Docker orchestration for the entire stack.

## Tech Stack

- **Backend:** Python 3.10, FastAPI, SQLAlchemy, Uvicorn.
- **Database:** PostgreSQL (for production/Docker), SQLite (default in local code).
- **Frontend:** HTML5, CSS3, JavaScript (ES6+), Bootstrap 5, Nginx.
- **Orchestration:** Docker, Docker Compose.

## Requirements

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- (Optional) Python 3.10+ (for local backend development)

## Setup and Run

### Using Docker (Recommended)

To start the entire stack:

```powershell
docker-compose up --build
```

The services will be available at:
- **Frontend:** [http://localhost](http://localhost)
- **Backend API:** [http://localhost:8000](http://localhost:8000)
- **API Documentation:** [http://localhost:8000/docs](http://localhost:8000/docs)

### Local Development

#### Backend
1. Navigate to `ecommerce-inventory-api/`.
2. Create a virtual environment: `python -m venv venv`.
3. Activate it: `.\venv\Scripts\activate`.
4. Install dependencies: `pip install -r requirements.txt`.
5. Run the API: `uvicorn src.main:app --reload`.

#### Frontend
Open `estoque-mvp-estatico/index.html` directly in a browser or serve it using a simple HTTP server.

## Scripts

- `docker-compose up`: Starts all services.
- `docker-compose down`: Stops and removes containers.
- `uvicorn src.main:app --reload`: Starts the backend with hot-reload (local development).

## Environment Variables

The backend service in Docker is configured with the following environment variables (see `docker-compose.yml`):

| Variable | Description | Default |
|----------|-------------|---------|
| `DB_HOST` | Database host name | `postgres-db` |
| `DB_PORT` | Database port | `5432` |
| `DB_NAME` | Database name | `estoque_db` |
| `DB_USER` | Database user | `postgres` |
| `DB_PASSWORD` | Database password | `postgrespassword` |
| `DB_DDL` | DDL strategy | `none` |

**Note:** The current Python implementation in `database.py` defaults to SQLite (`sqlite:///./estoque.db`). TODO: Update `database.py` to use environment variables for PostgreSQL connection when running in production.

## Tests

- **TODO:** Implement automated tests for backend and frontend.
- Existing files in `venv` are third-party library tests.

## License

This project is licensed under the terms found in `ecommerce-inventory-api/LICENSE`.
