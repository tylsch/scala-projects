# Shopping Cart Project
This project is based on the [Implementing Microservices with Akka](Implementing Microservices with Akka) tutorial by Lightbend with the following modifications:

- Upgraded library dependencies to latest versions
- Uses Red Panda instead of Apache Kafka for message broker
- Defines a separate database schema for Akka Persistence tables

## Running the sample code

### Database Setup

From the akka directory, run the following command:
```shell
docker-compose up -d
```
Create the PostgresSQL tables from the SQL script located inside the ddl-scripts at the root of the project:
```shell
docker exec -i akka-postgres-db-ecommerce-1 psql -U admin ecommerce -t < shopping-cart-service/ddl-scripts/create_tables.sql
```

### Running Application

1. Start a first node:

    ```
    sbt -Dconfig.resource=local1.conf run
    ```

2. (Optional) Start another node with different ports:

    ```
    sbt -Dconfig.resource=local2.conf run
    ```

3. Check for service readiness

    ```
    curl http://localhost:9101/ready
    ```
