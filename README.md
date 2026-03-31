# Config-Server (NextEvent Project)

Centralized Configuration Server for the NextEvent Microservices Ecosystem. This server acts as the "Single Source of Truth," providing externalized configuration to the Event, Participant, and Registration services, as well as the API Gateway and Service Registry

## Student Information

- Student Name: Sherul Dhanushka Fernando
- Student Number: 2301691014
- Slack Handle: https://ijse-eca-hdse-69-70.slack.com/team/U0AEH8NS9DW
- GCP Project ID: project-0ae0d75b-3979-4ebf-be9

## About

The Config-Server is a critical infrastructure component of the NextEvent system. It allows the entire ecosystem to be managed dynamically. Instead of hardcoding database credentials or service URLs inside each individual microservice JAR, this server serves those properties over HTTP.

## Tech Stack

| Technology | Details |
|---|---|
| Java | 25 |
| Spring Boot | 4.0.3 |
| Spring Cloud | 2025.1.0 |
| Spring Cloud Config Server | Native filesystem backend |
| Spring Boot Actuator | Health & management endpoints |

## How It Works

The Config-Server uses a **native filesystem** backend, loading configuration files from the classpath. All microservices bootstrap by importing their configuration from this server before starting up.

### Configuration Layout

```
src/main/resources/configurations/
├── application.yaml          # Shared config for all services (Eureka URL, logging)
├── platform/
│   ├── api-gateway.yaml      # Api-Gateway routes & CORS config
│   └── service-registry.yaml # Eureka server settings
└── services/
    ├── participant-service.yaml  # Participant-Service datasource (PostgreSQL)
    ├── event-service.yaml  # Event-Service datasource (MongoDB)
    └── registration-service.yaml # Registration-Service datasource (MySQL)
```

## Service Details

| Property | Value |
|---|---|
| Port | `9000` |
| Artifact ID | `Config-Server` |
| Group ID | `lk.ijse.eca` |

## Getting Started

Follow the lecture guidelines, refer to the lecture video for more information and how to get started correctly.

> **Important:** Config-Server must be started **first** before any other service, as all other services fetch their configuration from this server on startup.

```bash
./mvnw spring-boot:run
```

The server will be available at: `http://localhost:9000`

You can verify a service's configuration is being served correctly by visiting:
```
http://localhost:9000/{service-name}/default
```

## Need Help?

If you encounter any issues, feel free to reach out and start a discussion via the Slack workspace.
