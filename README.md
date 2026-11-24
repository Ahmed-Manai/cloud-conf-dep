# cloud-conf-dep

The configuration repository for a small Spring Cloud setup: a Spring Cloud Config Server reads these files from Git and serves them to the other services when they start.

| File | Used by | Contents |
|------|---------|----------|
| `application.properties` | every service | Sample shared values (`x1`, `x2`, `x3`) used to check that configuration is served |
| `department.properties` | the department service | Port `8085`, MySQL datasource (`depart` database) and JPA/Hibernate settings, plus sample values |
| `eureka.properties` | the Eureka discovery server | Port `8761`, running as a standalone registry |

## Using it

Point the Config Server at this repository:

```properties
spring.cloud.config.server.git.uri=https://github.com/Ahmed-Manai/cloud-conf-dep
```

A service then gets its file by its `spring.application.name`, for example `department` or `eureka`.

The datasource settings are local development defaults. In a real deployment, pass the database credentials through environment variables or a secret store instead of committing them.

Related project: [Gestion-of-Departments-on-AWS](https://github.com/Ahmed-Manai/Gestion-of-Departments-on-AWS).
