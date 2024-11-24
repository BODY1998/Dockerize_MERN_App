# 3 Tier Web App containerization

This project consists of a full-stack application that includes a frontend, backend, and MongoDB database, all managed through Docker containers using Docker Compose.

## Project Structure

The application is composed of the following services:

- **Frontend**: React-based frontend application
- **Backend**: Node.js backend API
- **MongoDB**: NoSQL database

## Prerequisites

Make sure you have the following installed on your system:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Getting Started

Follow these steps to set up and run the project:

1. **Clone the repository**:
    ```bash
    git clone https://github.com/BODY1998/nodejs_app_containerization.git
    cd nodejs_app_containerization
    ```

2. **Build and start the application**:
    Use Docker Compose to build and start the containers:
    ```bash
    docker-compose up --build
    ```

3. **Access the application**:
    - Frontend: The React application will be available at [http://localhost:3000](http://localhost:3000).
    - Backend: The Node.js API can be accessed at [http://localhost:3001](http://localhost:3001).
    - MongoDB: The database is exposed on port `27017`.

## Services Overview

### Frontend

- **Build Context**: `./frontend`
- **Port Mapping**: `3000:3000`
- **Environment Variable**: 
    - `REACT_APP_API_URL=http://localhost:3001/api`
- **Depends on**: Backend

### Backend

- **Build Context**: `./backend`
- **Port Mapping**: `3001:3001`
- **Environment Variable**: 
    - `MONGO_URL=mongodb://mongo:27017/mydatabase`
- **Depends on**: MongoDB

### MongoDB

- **Image**: Official MongoDB image from Docker Hub
- **Port Mapping**: `27017:27017`
- **Volume**: Data is stored in a Docker volume `mongo-data` to persist the database between container restarts.

## Stopping the Application

To stop the running containers:

```bash
docker-compose down
```
This will stop and remove the containers but will preserve the data stored in the `mongo-data` volume.

Volumes
-------

-   `mongo-data`: This volume is used by MongoDB to persist database data.

Additional Notes
----------------

-   Ensure that the environment variables in both frontend and backend are configured correctly to connect them.
-   If any changes are made to the codebase, re-run the `docker-compose up --build` command to rebuild the services.

License
-------

This project is licensed under the MIT License.
