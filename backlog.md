# AppFolio Europe Sprint Backlog

## **Epic 1: Set up Database Schema & Models**
This Epic focuses on the foundational work to set up the database schema, relationships, and tables for the core entities.

### **User Story 1.1: Set Up Database & Migrations**
- **As a** developer,
- **I want** to set up the database connection and create initial migrations,
- **So that** I can build a foundation for the data model entities and their relationships.

**Acceptance Criteria**:
- Database connection is successfully established.
- Database migrations for core tables are created.
- Initial data for testing is inserted.

---

### **User Story 1.2: Create `Property`, `Tenant`, `Lease`, and `Country` Models**
- **As a** developer,
- **I want** to create the `Property`, `Tenant`, `Lease`, and `Country` models and define relationships,
- **So that** I can ensure the data model is aligned with the business needs.

**Acceptance Criteria**:
- `Property`, `Tenant`, `Lease`, and `Country` models are defined.
- Foreign key relationships between entities are established (e.g., `Tenant` to `Property`).
- Model validation is in place (e.g., email, rent amount).

---

## **Epic 2: Implement CRUD API for Property & Tenant**
This Epic focuses on creating the API endpoints for managing properties and tenants, which are key entities in the data model.

### **User Story 2.1: Implement `Property` CRUD APIs**
- **As a** developer,
- **I want** to implement API endpoints to manage properties (create, read, update, delete),
- **So that** users can interact with properties through the system.

**Acceptance Criteria**:
- API routes for `Property` CRUD operations are created (`POST`, `GET`, `PUT`, `DELETE`).
- API responses should include relevant status codes (e.g., `200 OK`, `201 Created`, `404 Not Found`).
- Test cases for API routes are written and pass successfully.

---

### **User Story 2.2: Implement `Tenant` CRUD APIs**
- **As a** developer,
- **I want** to implement API endpoints to manage tenants (create, read, update, delete),
- **So that** users can manage tenant data within the system.

**Acceptance Criteria**:
- API routes for `Tenant` CRUD operations are created (`POST`, `GET`, `PUT`, `DELETE`).
- API responses should include relevant status codes (e.g., `200 OK`, `201 Created`, `404 Not Found`).
- Test cases for API routes are written and pass successfully.

---

## **Epic 3: Implement CRUD API for Lease, Payment & Invoice**
This Epic deals with more complex entities like **Leases**, **Payments**, and **Invoices**, which will manage the contracts and financial transactions.

### **User Story 3.1: Implement `Lease` CRUD APIs**
- **As a** developer,
- **I want** to implement API endpoints to manage leases (create, read, update, delete),
- **So that** users can manage rental agreements between tenants and properties.

**Acceptance Criteria**:
- API routes for `Lease` CRUD operations are created (`POST`, `GET`, `PUT`, `DELETE`).
- API responses should include relevant status codes (e.g., `200 OK`, `201 Created`, `404 Not Found`).
- Test cases for API routes are written and pass successfully.

---

### **User Story 3.2: Implement `Payment` CRUD APIs**
- **As a** developer,
- **I want** to implement API endpoints to manage payments (create, read, update, delete),
- **So that** users can track and process rental payments made by tenants.

**Acceptance Criteria**:
- API routes for `Payment` CRUD operations are created (`POST`, `GET`, `PUT`, `DELETE`).
- API responses should include relevant status codes (e.g., `200 OK`, `201 Created`, `404 Not Found`).
- Payment information (amount, date, tenant, lease) is recorded correctly.
- Test cases for API routes are written and pass successfully.

---

### **User Story 3.3: Implement `Invoice` CRUD APIs**
- **As a** developer,
- **I want** to implement API endpoints to manage invoices (create, read, update, delete),
- **So that** users can track invoices generated for payments.

**Acceptance Criteria**:
- API routes for `Invoice` CRUD operations are created (`POST`, `GET`, `PUT`, `DELETE`).
- API responses should include relevant status codes (e.g., `200 OK`, `201 Created`, `404 Not Found`).
- Test cases for API routes are written and pass successfully.

---

## **Epic 4: Implement Maintenance Request & Service Provider**
This Epic focuses on creating APIs to handle tenant maintenance requests and managing service providers that will fulfill these requests.

### **User Story 4.1: Implement `Maintenance Request` CRUD APIs**
- **As a** developer,
- **I want** to implement API endpoints to manage maintenance requests,
- **So that** tenants can submit maintenance issues and track their status.

**Acceptance Criteria**:
- API routes for `Maintenance Request` CRUD operations are created (`POST`, `GET`, `PUT`, `DELETE`).
- API responses should include relevant status codes (e.g., `200 OK`, `201 Created`, `404 Not Found`).
- Maintenance requests are linked to tenants and properties.
- Test cases for API routes are written and pass successfully.

---

### **User Story 4.2: Implement `Service Provider` CRUD APIs**
- **As a** developer,
- **I want** to implement API endpoints to manage service providers,
- **So that** users can assign maintenance tasks to service providers and track their progress.

**Acceptance Criteria**:
- API routes for `Service Provider` CRUD operations are created (`POST`, `GET`, `PUT`, `DELETE`).
- API responses should include relevant status codes (e.g., `200 OK`, `201 Created`, `404 Not Found`).
- Service providers can be linked to specific maintenance requests.
- Test cases for API routes are written and pass successfully.

---

## **Epic 5: Final Testing & Deployment**
This Epic focuses on ensuring everything works as expected and deploying the system to a staging environment.

### **User Story 5.1: Perform Final API Testing**
- **As a** developer,
- **I want** to ensure all APIs are tested thoroughly before deployment,
- **So that** the system is free of bugs and meets requirements.

**Acceptance Criteria**:
- All API routes have been tested manually using **Postman** or **Swagger**.
- Test cases cover all CRUD operations for `Property`, `Tenant`, `Lease`, `Payment`, `Invoice`, `Maintenance Request`, and `Service Provider`.
- All tests pass without errors.

---

### **User Story 5.2: Implement Error Handling & Validation**
- **As a** developer,
- **I want** to implement proper error handling and validation for API endpoints,
- **So that** users get meaningful feedback and the system is more resilient to invalid inputs.

**Acceptance Criteria**:
- Validation errors (e.g., missing required fields, invalid email format) are returned with appropriate status codes (e.g., `400 Bad Request`).
- Internal errors (e.g., database issues) are captured with status code `500 Internal Server Error`.
- API responses include user-friendly error messages where applicable.

---

### **User Story 5.3: Deploy to Staging Environment**
- **As a** developer,
- **I want** to deploy the application to a staging environment,
- **So that** the system can be tested and reviewed before being put into production.

**Acceptance Criteria**:
- The application is deployed to a staging server (e.g., **Heroku**, **AWS**, **DigitalOcean**).
- The database is correctly set up with necessary migrations.
- All API endpoints are accessible and functional.

---

## **Epic 6: Documentation & Sprint Retrospective**
This Epic involves creating documentation for the APIs and performing a sprint retrospective to evaluate the work.

### **User Story 6.1: Document API Endpoints**
- **As a** developer,
- **I want** to document the API endpoints in a centralized location,
- **So that** the development team and stakeholders can understand the API usage.

**Acceptance Criteria**:
- API documentation is created using **Swagger**, **Postman**, or a similar tool.
- Each API route is documented with information about HTTP methods, request parameters, responses, and status codes.

---

### **User Story 6.2: Sprint Retrospective**
- **As a** Scrum Master,
- **I want** to hold a sprint retrospective meeting,
- **So that** the team can discuss what went well and areas for improvement.

**Acceptance Criteria**:
- Team members share feedback on the sprint.
- Actionable items for process improvement are documented.
- The retrospective concludes with actionable insights.

---

# **Summary of Backlog**

| **Epic**                                       | **User Stories**                                           | **Estimated Time**   |
|------------------------------------------------|------------------------------------------------------------|----------------------|
| **Epic 1**: Set up Database Schema & Models    | 1.1 Set up Database & Migrations<br>1.2 Create Core Models   | 1 hour               |
| **Epic 2**: Implement CRUD API for Property & Tenant | 2.1 Implement `Property` CRUD APIs<br>2.2 Implement `Tenant` CRUD APIs | 1 hour               |
| **Epic 3**: Implement CRUD API for Lease, Payment & Invoice | 3.1 Implement `Lease` CRUD APIs<br>3.2 Implement `Payment` CRUD APIs<br>3.3 Implement `Invoice` CRUD APIs | 1.5 hours            |
| **Epic 4**: Implement Maintenance Request & Service Provider | 4.1 Implement `Maintenance Request` CRUD APIs<br>4.2 Implement `Service Provider` CRUD APIs | 1 hour               |
| **Epic 5**: Final Testing & Deployment        | 5.1 Perform Final API Testing<br>5.2 Implement Error Handling & Validation<br>5.3 Deploy to Staging Environment | 1 hour               |
| **Epic 6**: Documentation & Sprint Retrospective | 6.1 Document API Endpoints<br>6.2 Sprint Retrospective      | 30 minutes           |
