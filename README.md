## Airbnb-clone-project

The Airbnb Clone Project is a comprehensive, real-world application designed to simulate the development of a robust booking platform like Airbnb. It involves a deep dive into full-stack development, focusing on backend systems, database design, API development, and application security. This project enables learners to understand complex architectures, workflows, and collaborative team dynamics while building a scalable web application.

## Learning objectives

This project is tailored to enhance your expertise in modern software development practices. By completing these tasks, learners will:

  1. Master collaborative team workflows using GitHub.
  2. Deepen their understanding of backend architecture and database design principles.
  3. Implement advanced security measures for API development.
  4. Gain proficiency in designing and managing CI/CD pipelines for efficient deployment.
  5. Strengthen their ability to document and plan complex software projects effectively.
  6. Develop an understanding of integrating technologies like Django, MySQL, and GraphQL in a unified ecosystem.

## Technology Stack

1. Django - framework used to build restful APIs
2. GraphQL - Allows for flexible and efficient querying of data.
3. PostreQL - A powerful relational database used for data storage.
4. Celery - For handling asynchronous tasks such as sending notifications or processing payments.
5. Redis - Used for caching and session management.
6. Docker - Used for containerization
7. Github Actions, Kubernetees and Nginx - Deployment and Automation
8. OpenAPI - API Documentation 

## Team Roles

| Role | Responsibilities |
|------|------------------|
| **Business Analyst** | Enriches a product development team with a profound understanding of business processes from various perspectives and the ability to shape up a software product that creates maximum business value.|
| **Product Owner** | They define a business strategy, shape up the product vision, make sure it satisfies customer needs, and manage a product backlog.|
| **Project Manager** | Responsible for distributing tasks across team members, planning work activities, and updating project status.|
| **Software Architect** | An expert-level software engineer who makes executive software design decisions on behalf of an app development team.|
| **Backend Developer** | Designs and implements RESTful and GraphQL APIs, defines database schemas, manages authentication and authorization, and develops business logic for bookings, payments, and reviews. |
| **Database Administrator (DBA)** | Designs the relational database schema, optimizes queries through indexing and normalization, manages backups, and ensures data integrity and scalability. |
| **DevOps Engineer** | Builds CI/CD pipelines, manages Docker containers and deployments, configures monitoring and logging, and ensures seamless scaling of backend services. |
| **QA Engineer** | Writes automated tests for APIs, validates endpoint correctness, performs performance testing, and ensures compliance with documentation and security standards. |

## Database Design
---

+ Users: Both guest and host
  Stores authentication credentials, profile information, and host/guest roles.  
  **Relationships:**  
  - One-to-Many with `Property` (a host can have many properties)  
  - One-to-Many with `Booking` (a user can have multiple bookings
    
    1. email - email of the user for authentication
    2. Phone number - linked to mobile payments
    3. Name - Name of the user
    4. isTenant(bool) - identifies if the user is a tenant or landlord 
+ Propery:
  Contains details about listings — title, description, price, location, amenities, etc.  
  **Relationships:**  
  - One-to-Many with `Booking`  
  - One-to-Many with `Review`
  
    1. Name - name of the property
    2. Location - where the property is located
    3. Reviews - a property can have reviews regarding the place
+ Bookings
  Manages reservation details including dates, guest info, and payment status.  
  **Relationships:**  
  - Many-to-One with `User` (guest)  
  - Many-to-One with `Property`
  
    1. Time of booking
    2. Duration of stay - how long a tenant is going to occupy the space
    3. Amount
+ Reviews
  Stores user ratings and feedback for properties.  
  **Relationships:**  
  - Many-to-One with `User`  
  - Many-to-One with `Property`

    1. Userid - used to tie a review to a user since a user can have multiple reviews
    2. Review - content of the review
+ Payments
  Tracks transaction details including payment amount, date, and status.  
  **Relationships:**  
  - One-to-One with `Booking`

    1. Time - time when the payment is made
    2. UserId - used to identify who has made the payment
    3. Confirmation code - For confiemation purposes

---

## API Security

The backend implements multiple layers of security to protect user data and system integrity.

### **Authentication & Authorization**
- **JWT Authentication:** Used for secure, stateless session management.
- **Role-Based Access Control (RBAC):** Different permissions for hosts and guests.
- **Token Expiry & Refresh Mechanism:** Ensures secure token lifecycle management.

### **Data Protection**
- **HTTPS Enforcement:** All communications use SSL/TLS encryption.
- **Input Validation & Sanitization:** Prevents SQL injection and XSS attacks.
- **Rate Limiting:** Protects APIs from abuse and brute-force attempts.

### **Best Practices**
- Secure password hashing using Django’s built-in `PBKDF2` algorithm.
- Environment variables for sensitive credentials (`.env`).
- Strict CORS policy for allowed frontend domains.

## CI/CD Pipeline

The CI/CD setup automates testing, linting, building, and deployment using **GitHub Actions** and **Docker**.

This helps in faster and more reliable development, improved code quality through automated testing, Rapid deployment and testing


### **Pipeline Workflow**
1. **Continuous Integration (CI)**
   - Triggered on every push or pull request.
   - Runs automated tests and linting.
   - Builds Docker image and verifies service health.

2. **Continuous Delivery (CD)**
   - Automatically deploys to staging environment on successful CI.
   - Manual approval required for production deployment.
   - Uses Docker Compose for multi-container orchestration (API, Redis, PostgreSQL).

3. **Monitoring & Logging**
   - Application logs captured via Django and Docker logging drivers.
   - Optional integration with tools like **Prometheus** and **Grafana** for performance metrics.








