# User Access Management System

This is a Spring Boot project that provides a user access management system using PostgreSQL as the database. This README provides step-by-step instructions on setting up the project locally and running it. 
![image](https://github.com/user-attachments/assets/d2710243-bd07-45b1-9ad0-19f9bc2fbf13)
![image](https://github.com/user-attachments/assets/4eb454d4-b934-4585-bd37-9953fb00aa13)
![image](https://github.com/user-attachments/assets/3185de77-a41e-4347-a52b-88fa5f74a216)
![image](https://github.com/user-attachments/assets/743266f6-4e51-4fed-ae08-f0061a4c19a5)
![image](https://github.com/user-attachments/assets/30095901-dbce-4e16-8670-b4505b106cb0)
![image](https://github.com/user-attachments/assets/9626d803-e2c6-4697-a015-b69b442fd21f)
![image](https://github.com/user-attachments/assets/3590bb59-c94a-4f22-8aca-63c5b81c20ec)
![image](https://github.com/user-attachments/assets/6666e5f5-db9d-41be-a2c5-063a77eafdcd)
![image](https://github.com/user-attachments/assets/b35b6091-7f1c-423f-86d1-a1ab2025459d)











## Project Repository
GitHub repository: [https://github.com/Pradip19861/user-access-management.git](https://github.com/Pradip19861/user-access-management.git)

---

## Table of Contents

- [Requirements](#requirements)
- [Getting Started](#getting-started)
- [Database Setup](#database-setup)
- [Running the Application](#running-the-application)
- [Application Endpoints](#application-endpoints)
- [Configuration](#configuration)
- [Contributing](#contributing)

---

## Requirements

Ensure that you have the following installed:

- [Java 11](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) or newer
- [Maven](https://maven.apache.org/download.cgi)
- [PostgreSQL](https://www.postgresql.org/download/)

---

## Getting Started

1. **Clone the repository:**

   ```bash
   git clone https://github.com/Pradip19861/user-access-management.git
   cd user-access-management
   ```

2. **Build the project using Maven:**

   ```bash
   mvn clean install
   ```

---

## Database Setup

The application requires a PostgreSQL database to store data. Follow these steps to set up the PostgreSQL database.

1. **Open PostgreSQL and create a database:**

   ```sql
   CREATE DATABASE user_access_db;
   ```

2. **Create a user with permissions:**

   ```sql
   CREATE USER user_access_user WITH PASSWORD 'yourpassword';
   ALTER ROLE user_access_user SET client_encoding TO 'utf8';
   ALTER ROLE user_access_user SET default_transaction_isolation TO 'read committed';
   ALTER ROLE user_access_user SET timezone TO 'UTC';
   GRANT ALL PRIVILEGES ON DATABASE user_access_db TO user_access_user;
   ```

3. **Update the `application.properties` file:**

   Go to `src/main/resources/application.properties` and set the following properties:

   ```properties
   # PostgreSQL Database configuration
   spring.datasource.url=jdbc:postgresql://localhost:5432/user_access_db
   spring.datasource.username=user_access_user
   spring.datasource.password=yourpassword

   # JPA and Hibernate
   spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   ```

---

## Running the Application

1. **Start PostgreSQL:**

   Ensure that your PostgreSQL server is running.

2. **Run the Spring Boot application:**

   Use the following command to start the application:

   ```bash
   mvn spring-boot:run
   ```

3. **Access the application:**

   The application runs on port `8080` by default. You can access it at:

   ```
   http://localhost:8080
   ```

   To change the port, update the `application.properties` file:

   ```properties
   server.port=your_custom_port
   ```

---

## Application Endpoints

Below are some sample endpoints for managing users (these may vary based on your actual implementation):

- **GET** `/api/users` - Retrieve all users
- **POST** `/api/users` - Create a new user
- **GET** `/api/users/{id}` - Get user details by ID
- **PUT** `/api/users/{id}` - Update user by ID
- **DELETE** `/api/users/{id}` - Delete user by ID

---

## Configuration

The application uses the default Spring Boot configurations with a few modifications for PostgreSQL setup. Other settings, such as server port or logging level, can be configured in the `application.properties` file.

For advanced configuration options, please consult the [Spring Boot documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html).

---

## Contributing

If you'd like to contribute, please fork the repository and make changes as you'd like. Pull requests are warmly welcomed.

---

## License

This project is licensed under the MIT License.

---

### Troubleshooting

If you encounter any issues:

1. Ensure PostgreSQL is running and the database is properly set up.
2. Double-check the database configuration in `application.properties`.
3. Make sure the correct dependencies are installed by running `mvn dependency:resolve`.

Happy coding!
