# Zangoh_project
**URL**: https://zangohaisupervisor.netlify.app/

# Zangoh AI Agent Supervisor Workstation

This project is a web-based workstation for human supervisors to monitor, intervene in, and improve AI customer service agents.

## Architecture

The application is built with a microservices architecture, containerized using Docker. The services include:

-   **Frontend:** A React-based single-page application that provides the user interface for the supervisor workstation. It runs on port 3000.
-   **Backend:** A Node.js/Express server that handles business logic, API requests, and communication with the database and other services. It runs on port 8080.
-   **MongoDB:** The primary database for storing conversations, agent configurations, and other application data.
-   **Qdrant:** A vector database used for knowledge base retrieval and similarity searches.
-   **Ollama:** A service for running large language models locally.

### Architectural Diagram

```
+----------------+      +-----------------+      +-----------------+
|   Frontend     |----->|     Backend     |----->|    MongoDB      |
| (React @ 3000) |      | (Node.js @ 8080)|      | (Database)      |
+----------------+      +-----------------+      +-----------------+
                          |
                          |      +-----------------+
                          +----->|     Qdrant      |
                          |      | (Vector DB)     |
                          |      +-----------------+
                          |
                          |      +-----------------+
                          +----->|     Ollama      |
                                 | (LLM Service)   |
                                 +-----------------+
```

## Setup and Running Instructions

### Prerequisites

-   Docker
-   Docker Compose

### Running the Application

1.  **Start the environment:**
    Open your terminal in the project root directory and run the following command to start all the services in the background. This command uses the `docker-compose.yaml` file located in the `test-agent` directory.

    ```bash
    docker-compose -f test-agent/docker-compose.yaml up -d
    ```

2.  **Verify services:**
    Check that all services are running correctly:

    ```bash
    docker ps
    ```
    You should see containers for `zangoh-supervisor-frontend`, `zangoh-supervisor-backend`, `zangoh-mongodb`, `zangoh-qdrant`, and `zangoh-ollama`.

3.  **Access the application:**
    Once the services are running, you can access the application in your web browser at:

    -   **Frontend:** [http://localhost:3000](http://localhost:3000)
    -   **Backend API Docs:** [http://localhost:8080/api-docs](http://localhost:8080/api-docs)

### Stopping the Application

To stop the services, run:

```bash
docker-compose -f test-agent/docker-compose.yaml down
