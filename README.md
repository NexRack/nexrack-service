# NexRack Service - Rack Booking System

NexRack is a robust rack booking system built with Quarkus, designed to efficiently manage and organize rack resources.

## Project Setup

### Prerequisites
- Docker and Docker Compose
- Java 21 (for local development)
- Maven (for local development)

### Running with Docker Compose

The easiest way to get started is using our development Docker Compose setup:

```shell script
docker-compose -f docker-compose-dev.yaml up -d
```

This will start:
- **nexrack-quarkus**: Main application service (accessible via NGINX at http://localhost:8080/nexrack/)
- **nexrack-db**: PostgreSQL database (accessible at localhost:15432)
- **nexrack-nginx**: Web server/reverse proxy (port 8080)
- **nexrack-autoheal**: Container health monitoring service
- **nexrack-pgadmin**: PostgreSQL admin interface (accessible at http://localhost:8080/pgadmin/)

### URL Structure

The application uses the following URL structure:
- Main application: http://localhost:8080/nexrack/
- PgAdmin: http://localhost:8080/pgadmin/
- Health check: http://localhost:8080/nexrack/q/health/

### Environment Configuration

The database is pre-configured with:
- Database name: `nexrack_db`
- Username: `nexrack_admin`
- Password: `nexrack_admin_password`

PgAdmin is pre-configured with:
- Email: `nexrack@admin.com`
- Password: `nexrack_admin_password`

## Running in Development Mode

For local development without Docker:

```shell script
./mvnw quarkus:dev
```

This starts the application in dev mode with live coding enabled at http://localhost:8080.
Access the Dev UI at http://localhost:8080/q/dev/.

## Architecture Overview

NexRack consists of several interconnected components:

1. **Quarkus Backend**: RESTful API services handling business logic
2. **PostgreSQL Database**: Persistence layer for storing rack, booking, and user data
3. **NGINX**: Reverse proxy for routing requests and serving static content
4. **Health Monitoring**: Health checks and auto-healing for high availability

## API Documentation

When running in dev mode, access the Swagger UI at http://localhost:8080/q/swagger-ui/ to explore and test available endpoints.

When running with Docker Compose, access the Swagger UI at http://localhost:8080/nexrack/q/swagger-ui/.

## Building and Packaging

Package the application:

```shell script
./mvnw package
```

For an über-jar:

```shell script
./mvnw package -Dquarkus.package.jar.type=uber-jar
```

## Related Guides

- Hibernate ORM ([guide](https://quarkus.io/guides/hibernate-orm)): Define your persistent model with Hibernate ORM and Jakarta Persistence
- REST ([guide](https://quarkus.io/guides/rest)): A Jakarta REST implementation utilizing build time processing and Vert.x
- Flyway ([guide](https://quarkus.io/guides/flyway)): Handle your database schema migrations
- WebSockets Client ([guide](https://quarkus.io/guides/websockets)): Client for WebSocket communication channel
- WebSockets Next ([guide](https://quarkus.io/guides/websockets-next-reference)): Implementation of the WebSocket API with enhanced efficiency and usability
- REST Jackson ([guide](https://quarkus.io/guides/rest#json-serialisation)): Jackson serialization support for Quarkus REST
- Hibernate ORM with Panache ([guide](https://quarkus.io/guides/hibernate-orm-panache)): Simplify your persistence code for Hibernate ORM
- SmallRye Health ([guide](https://quarkus.io/guides/smallrye-health)): Monitor service health
- JDBC Driver - PostgreSQL ([guide](https://quarkus.io/guides/datasource)): Connect to the PostgreSQL database via JDBC JDBC Driver - PostgreSQL ([guide](https://quarkus.io/guides/datasource)): Connect to the PostgreSQL database via JDBC JDBC Driver - PostgreSQL ([guide](https://quarkus.io/guides/datasource)): Connect to the PostgreSQL database via JDBC