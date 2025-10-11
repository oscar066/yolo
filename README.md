# Yolo E-Commerce Application (Containerized)

This repository contains the source code for the Yolo E-Commerce application, a full-stack web platform. The primary goal of this project was to containerize the application's microservices (frontend, backend, and database) using Docker and Docker Compose for a seamless, reproducible, and production-ready deployment.

The entire containerization process, including architectural decisions, debugging, and best practices, is detailed in the `explanation.md` file.

## Technology Stack

*   **Frontend:** React.js
*   **Backend:** Node.js, Express.js
*   **Database:** MongoDB
*   **Containerization:** Docker, Docker Compose
*   **Web Server:** Nginx (for serving the production frontend)

---

## Prerequisites

Before you begin, ensure you have the following installed on your system:

*   **Git:** To clone the repository.
*   **Docker Desktop:** This includes both the Docker Engine and Docker Compose, which are required to build and run the application.

---

## Getting Started

1.  **Clone the repository** to your local machine:
    ```bash
    git clone https://github.com/oscar066/yolo.git
    ```

2.  **Navigate into the project directory:**
    ```bash
    cd yolo
    ```

---

## Running the Application

The entire application stack (frontend, backend, database) is orchestrated with a single Docker Compose command.

1.  **Build and Run the Containers:**
    From the root directory of the project, run the following command:
    ```bash
    docker-compose up --build
    ```
    *   `--build`: This flag tells Docker Compose to build the images from the `Dockerfile`s before starting the containers. This is essential for applying your latest changes.

2.  **Verification:**
    You will see logs from all three services (`oscar-yolo-client`, `oscar-yolo-backend`, and `app-mongo`). The application is ready when the backend log shows a successful connection to the database.

    **Running in the Background (Detached Mode):**
    For a cleaner terminal, you can run the application in detached mode:
    ```bash
    docker-compose up -d --build
    ```
    The containers will run in the background. You can view logs anytime with `docker-compose logs -f`.

---

## Accessing the Services

Once the containers are running, you can access the different parts of the application:

*   **Frontend Website:**
    *   Navigate to **`http://localhost`** in your web browser.
    *   *(This corresponds to port 80, which is the default for Nginx).*

*   **Backend API:**
    *   The API is running and accessible at `http://localhost:5000`.

*   **Database:**
    *   The MongoDB database is running and can be connected to at `mongodb://localhost:27017` using a client like MongoDB Compass.

---

## Stopping the Application

1.  **If running in the foreground:**
    *   Press `Ctrl + C` in the terminal where the containers are running.

2.  **The Recommended Method (stops and removes containers):**
    *   Run the following command from the project root:
        ```bash
        docker-compose down
        ```

3.  **To Stop and Remove the Database Volume:**
    *   If you want to completely reset the database and start fresh, use the `-v` flag. **Warning: This will delete all data in your database.**
        ```bash
        docker-compose down -v
        ```

## Project Screenshots 

**Frontend Running Locally**
![Frontend](screenshots/screen1.png)

![Frontend](screenshots/screen-before-adding-product.png)

![Frontend](screenshots/screen-after-adding-product.png)

![Frontend](screenshots/footer.png)



