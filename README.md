Digital Banking Microservices Platform
A Java and Spring Boot-based digital banking backend designed with a microservices architecture. The project demonstrates how banking capabilities such as user management, account operations, fund transfers, and transaction processing can be organized into independently developed services and exposed through REST APIs.

Developer: Dheeraj B
GitHub: @Dheeraj531
Project Overview
The goal of this project is to explore the design and integration of backend services for a digital banking application. It uses Spring Boot and related Spring technologies to separate banking responsibilities into services, with shared infrastructure for request routing and service discovery.
Key Features
- User Management: APIs for user registration and user-related operations.
- Account Management: Account creation and account-related operations.
- Fund Transfers: Service endpoints for initiating and reviewing transfers between accounts.
- Transaction Processing: Transaction lookup and deposit/withdrawal operations where supported by the implementation.
- API Gateway: A centralized entry point for routing client requests to backend services.
- Service Discovery: Service registry for registering and discovering microservices.
- Database Integration: MySQL persistence configured for the individual services.
- Authentication Integration: Keycloak and Spring Security configuration for authentication and authorization.
- API Testing: Postman collection/resources for testing available endpoints.
Feature availability and configuration can vary by service. Refer to the implementation and service-specific documentation before relying on an endpoint.

Technology Stack
Category	Technologies
Language	Java 17
Backend Framework	Spring Boot
Microservices	Spring Cloud
API Development	REST APIs
Persistence	Spring Data JPA, Hibernate
Database	MySQL
Security	Spring Security, Keycloak
Build Tool	Maven
API Testing	Postman
Source Control	Git, GitHub


Check each service's pom.xml for the exact dependency versions.
Architecture
                      Client / Consumer
                              |
                              v
                         API Gateway
                              |
              +---------------+----------------+
              |               |                |
              v               v                v
         User Service   Account Service   Transaction Service
              |               |                |
              v               v                v
         MySQL DB         MySQL DB          MySQL DB
                              ^
                              |
                      Fund Transfer Service

             Service Registry / Discovery
             Keycloak + Spring Security
This diagram is a high-level conceptual view. Actual service routes, database boundaries, ports, and dependencies should be confirmed from the configuration files in the repository.
Project Structure
.
├── API-Gateway/
├── Account-Service/
├── Fund-Transfer/
├── Sequence-Generator/
├── Service-Registry/
├── Transaction-Service/
├── User-Service/
├── docs/
├── postman_collection/
└── README.md
Each service has its own source code and Maven configuration. Some services may also contain their own README and API documentation.
Prerequisites
Install the following before running the project:
- JDK 17
- Maven
- MySQL
- Keycloak, if using the configured authentication flow
- Git
- Postman (optional)
Getting Started
1. Clone the repository
git clone https://github.com/Dheeraj531/digital-banking-microservices.git
cd digital-banking-microservices
2. Configure the services
For each microservice:
1. Open src/main/resources/application.properties or application.yml.
2. Configure the MySQL connection URL, database name, username, and password.
3. Configure the service registry and API Gateway URLs/ports.
4. Configure Keycloak realm, client, and authentication settings if required.
5. Keep credentials in environment variables or local configuration excluded from Git.
Create the databases required by the services. Use the service configuration and documentation to determine the correct database names and connection settings.
3. Build and run
Open a terminal in an individual service directory and run:
mvn clean install
mvn spring-boot:run
Start infrastructure and services in the order required by their dependencies. A typical sequence is:
1. MySQL and Keycloak
2. Service Registry
3. Sequence Generator
4. User, Account, Transaction, and Fund Transfer services
5. API Gateway
The actual startup order and ports may vary. Run each service in a separate terminal or through your IDE. There may not be a single root-level command that starts every service.
4. Test the APIs
1. Start the required services.
2. Import the available Postman collection from postman_collection/.
3. Update the base URL and authentication settings for your local environment.
4. Send requests and inspect the responses.
Consult each service's README and API documentation for available endpoints and required request bodies.
5. Run tests
From a service directory, run:
mvn test
Tests may require database and authentication services to be configured and running.
Security Considerations
- This is an educational/demo project, not a certified production banking platform.
- Never commit passwords, API keys, access tokens, private keys, or real customer information.
- Use test data and sandbox credentials only.
- Review authorization, validation, error handling, auditability, and transaction consistency before extending the system.
- Apple Pay, Google Pay, Samsung Pay, Fitbit Pay, Visa/Mastercard tokenization, Temenos T24, LDAP, and Thales/Gemalto integrations are not claimed as implemented unless corresponding working code and approved provider access are present.
Future Enhancements
Possible improvements include:
- Automated unit and integration testing
- Docker Compose for local multi-service setup
- CI/CD workflows
- Centralized logging, monitoring, and distributed tracing
- Improved audit logging and transaction consistency
- Additional role-based authorization and security hardening
- Integration with payment providers using approved sandbox environments
Author
Dheeraj B
GitHub: Dheeraj531
Acknowledgements
This repository is based on or adapted from the Spring Boot Microservices Banking Application by Kartik1502. Any reuse or redistribution must comply with the original repository's license or permission from its author. See the source repository for its original documentation and attribution requirements.
