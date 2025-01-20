# Teachers API Automation Testing

## Overview

This collection automates CRUD operations for managing teachers in the School Management System. It includes requests to create, retrieve, update, and delete teacher records, along with test scripts for validation.

### Features

- **Dynamic Variables**: Captures the `TeacherID` dynamically from the `POST` response for use in subsequent requests.
- **Automated Assertions**:
  - Status codes.
  - Response structure and content.
- **Data-Driven Testing**: Supports bulk operations using Postman Collection Runner.

---

## Requests in the Collection

### 1. **Create Teacher**

- **Method**: `POST`
- **Endpoint**: `{{baseURL}}/api/teachers`
- **Headers**:
  - `Content-Type`: `application/json`
- **Body**:
  ```json
  {
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com",
    "specialization": "Java"
  }
  ```
- **Test Scripts**:
  - Validate status code is `201`.
  - Validate the response contains an `id`.
  - Save `TeacherID` for use in subsequent requests.

---

### 2. **Get All Teachers**

- **Method**: `GET`
- **Endpoint**: `{{baseURL}}/api/teachers`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response is an array of teacher objects.

---

### 3. **Get Teacher by ID**

- **Method**: `GET`
- **Endpoint**: `{{baseURL}}/api/teachers/{{TeacherID}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains the teacher’s details.

---

### 4. **Update Teacher**

- **Method**: `PUT`
- **Endpoint**: `{{baseURL}}/api/teachers/{{TeacherID}}`
- **Body**:
  ```json
  {
    "firstName": "John Updated",
    "lastName": "Doe Updated",
    "email": "john.updated@example.com",
    "specialization": "Java"
  }
  ```
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains updated teacher details.

---

### 5. **Delete Teacher**

- **Method**: `DELETE`
- **Endpoint**: `{{baseURL}}/api/teachers/{{TeacherID}}`
- **Test Scripts**:
  - Validate status code is `204`.

---

## How to Run

### Using Postman:

1. Import the **Teacher.postman_collection.json** into Postman.
2. Select the environment (e.g., `Development` or `Production`).
3. Run individual requests manually or use the Collection Runner for batch execution.

### Using Newman:

1. Install Newman globally:
   ```bash
   npm install -g newman
   ```
2. Install Newman Reporter:
   ```bash
   npm install -g newman-reporter-html
   ```
3. Execute the collection:
   ```bash
   newman run Teacher.postman_collection.json -e Development.postman_environment.json -g workspace.postman_globals.json
   ```
4. View results in the terminal or export them as a report:
   ```bash
   newman run Teacher.postman_collection.json -e Development.postman_environment.json -g workspace.postman_globals.json -r html
   ```

---

## Folder Contents

- `Teacher.postman_collection.json`: The Postman collection for Teachers API.
- `screenshots/`: Screenshots showcasing test results and workflows.
- `reports/`: Newman execution reports in HTML/JSON format.
