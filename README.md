# RigMagic UserProfiles Microservice

A FastAPI-based microservice for managing user profiles, roles, and related data for the RigMagic platform. This service supports both customer and trade users, with extensible models and secure JWT-based authentication.

## Features
- FastAPI RESTful API
- JWT authentication (Auth.js compatible)
- Customer and Trade user support
- SQLite database (easy to swap for other backends)
- Dockerized for easy deployment
- CI/CD with linting, formatting, and tests via GitHub Actions

## API Endpoints

| Method | Endpoint                        | Description                       |
|--------|----------------------------------|-----------------------------------|
| GET    | `/users/me`                     | Get current user's profile        |
| GET    | `/users/{user_id}`              | Get a user by ID                  |
| POST   | `/users/`                       | Create a new user                 |
| PUT    | `/users/{user_id}`              | Update a user                     |
| DELETE | `/users/{user_id}`              | Delete a user                     |
| GET    | `/users/`                       | List all users                    |
| POST   | `/users/{user_id}/add_yacht`    | Add a yacht to a user             |
| GET    | `/health`                       | Health check                      |

## Quickstart

### Local Development

1. **Install dependencies:**
   ```bash
   python3 -m pip install -r requirements.txt
   ```
2. **Run the app:**
   ```bash
   uvicorn src.app:app --reload
   ```
3. **API docs:** Visit [http://localhost:8000/docs](http://localhost:8000/docs)

### Docker

1. **Build the image:**
   ```bash
   docker build -t rigmagic-userprofiles .
   ```
2. **Run with Docker Compose:**
   ```bash
   docker-compose up --build
   ```

### Environment Variables
- `AUTH_JS_SECRET`: Secret key for JWT validation (default: `your_authjs_secret`)

## Database
- Uses SQLite by default (`src/data.db`).
- To persist data outside the container, Docker Compose mounts `./data`.

## CI/CD
- GitHub Actions workflow runs on every push/PR:
  - Linting with flake8
  - Formatting check with black
  - Tests with pytest

## Testing
- Add tests in the `tests/` directory.
- Run tests locally:
  ```bash
  pytest
  ```

## Contributing
1. Fork the repo and create a feature branch.
2. Ensure code passes linting and tests (`black`, `flake8`, `pytest`).
3. Open a pull request with a clear description.

## License
MIT
