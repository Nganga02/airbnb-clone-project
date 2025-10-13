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
2. GraphQL - Database
3. PostreQL - Database
4. Docker - Used for containerization

## Team Roles

## Database Design
Users: Both tenants and landlords
  1. email - email of the user for authentication
  2. Phone number - linked to mobile payments
  3. Name - Name of the user
  4. isTenant(bool) - identifies if the user is a tenant or landlord 
Propery:
  1. Name - name of the property
  2. Location - where the property is located
  3. Reviews - a property can have reviews regarding the place
Bookings
  1. Time of booking
  2. Duration of stay - how long a tenant is going to occupy the space
  3. Amount
Reviews
  1. Userid - used to tie a review to a user since a user can have multiple reviews
  3. review - content of the review
Payments
  1. Time - time when the payment is made
  2. UserId - used to identify who has made the payment
  3. Confirmation code - For confiemation purposes


