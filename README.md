# Flowise with PostgreSQL Docker Setup

This repository provides a Docker Compose setup for running Flowise with PostgreSQL as the database backend. It is based on the original [Flowise project](https://github.com/FlowiseAI/Flowise).

Flowise is an open-source UI visual tool to build your customized LLM flow using LangchainJS.

## Prerequisites

- Docker
- Docker Compose

## Quick Start

1. Clone this repository:

   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Copy the `.env.example` file to create a new `.env` file in the root directory:

   ```bash
   cp .env.example .env
   ```

   This default configuration should work out of the box with PostgreSQL. However, feel free to adjust the settings in the `.env` file according to your specific requirements.

3. Start the containers:

   ```bash
   docker compose up -d
   ```

4. Access Flowise at [http://localhost:3000](http://localhost:3000) (or the port you specified in the `.env` file).

5. To stop the containers:

   ```bash
   docker compose down
   ```

## Configuration

### Environment Variables

The `.env` file should contain the following variables (adjust as needed):

```bash
PORT=3000
APIKEY_PATH=/root/.flowise
SECRETKEY_PATH=/root/.flowise
LOG_PATH=/root/.flowise/logs
BLOB_STORAGE_PATH=/root/.flowise/storage

DATABASE_TYPE=postgres
DATABASE_PORT=5432
DATABASE_HOST=flowise2_postgres
DATABASE_NAME=flowise2db
DATABASE_USER=postgres
DATABASE_PASSWORD=password

FLOWISE_USERNAME=user
FLOWISE_PASSWORD=1234
```

### PostgreSQL Configuration

This setup uses PostgreSQL instead of the default SQLite database. The `DATABASE_PATH` variable is not needed when using PostgreSQL.

### Persistent Storage

Persistent storage for Flowise is configured in the `docker-compose.yml` file. The `./storage_flowise` directory on the host is mounted to `/root/.flowise` in the Flowise container.

## Troubleshooting

If you encounter issues:

1. Check the logs:

   ```bash
   docker compose logs
   ```

2. Ensure all environment variables are correctly set in the `.env` file.

3. If you've recently changed database configurations, you may need to remove the existing volumes:

   ```bash
   docker compose down -v
   ```

   Then start the containers again.

4. Reference Files:
   This repository includes two additional files to help with troubleshooting:

   a. `docs/startup.log`:
      Contains the logs generated during the Docker Compose startup process. It can be helpful for diagnosing initialization issues or verifying that all services started correctly.

   b. `docs/tree_storage_flowise.txt`:
      Shows the directory structure of Flowise's persistent storage (excluding PostgreSQL data). It can be useful for understanding what files and directories Flowise creates and maintains.

   Note: The actual content of your Flowise storage may differ based on your usage and configuration.

5. If problems persist, check the [Flowise documentation](https://docs.flowiseai.com/) or seek help from the [Flowise community](https://discord.com/channels/1087698854775881778/1105430878101962826).

## Security

Remember to change the default username and password in the `.env` file for production use.

## Additional Resources

This project is based on the excellent work of the Flowise team and community. We extend our heartfelt gratitude to all contributors of the original Flowise project. Their innovation and dedication to the open-source community have provided us with this powerful and flexible tool.

Special thanks to:

- The Flowise development team for bringing us this outstanding open-source project.
- All contributors involved in Flowise development, testing, and documentation.
- Members of the Flowise community who generously share their knowledge and experience.

For more detailed information on Flowise configuration and usage, refer to the following resources:

- [Flowise Official Documentation](https://docs.flowiseai.com/)
- [Flowise GitHub Repository](https://github.com/FlowiseAI/Flowise)
- [Flowise Discord Community](https://discord.gg/jbaHfsRVBW)
