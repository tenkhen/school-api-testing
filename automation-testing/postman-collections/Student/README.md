# Students API Automation Testing

## Overview

This collection automates CRUD operations for managing students in the School Management System. It includes requests to create, retrieve, update, and delete student records, along with test scripts for validation.

### Features

- **Dynamic Variables**: Captures the `StudentID` dynamically from the `POST` response for use in subsequent requests.
- **Automated Assertions**:
  - Status codes.
  - Response structure and content.
- **Data-Driven Testing**: Supports bulk operations using Postman Collection Runner.

---

## Requests in the Collection

### 1. **Create Student**

- **Method**: `POST`
- **Endpoint**: `{{BaseURL}}{{StudentEndpoint}}`
- **Headers**:
  - `Content-Type`: `application/json`
- **Body**:
  ```json
  {
    "firstName": "Khenrab",
    "lastName": "Lama",
    "email": "khenrab@khenrab.io",
    "dateOfBirth": "2000-11-24"
  }
  ```
- **Test Scripts**:
  - Validate status code is `201`.
  - Validate the response contains an `id`.
  - Save `StudentID` for use in subsequent requests.

---

### 2. **Get All Students**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{StudentEndpoint}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response is an array of student objects.

---

### 3. **Get Student by ID**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{StudentEndpoint}}/{{StudentID}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains the student’s details.

---

### 4. **Update Student**

- **Method**: `PUT`
- **Endpoint**: `{{BaseURL}}{{StudentEndpoint}}/{{StudentID}}`
- **Body**:
  ```json
  {
    "firstName": "Tenzin",
    "lastName": "Jampa",
    "email": "tenzin.jampa@tenjam.io",
    "dateOfBirth": "1990-01-27"
  }
  ```
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains updated student details.

---

### 5. **Delete Student**

- **Method**: `DELETE`
- **Endpoint**: `{{BaseURL}}{{StudentEndpoint}}/{{StudentID}}`
- **Test Scripts**:
  - Validate status code is `204`.

---

### 6. **Pagination**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{StudentEndpoint}}/page?page={{PageNumber}}&size={{PageSize}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains paginated student data.

---

### 7. **Search by First Name**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{StudentEndpoint}}/search?name=Michael`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains students with the matching first name.

---

## How to Run

### Using Postman:

1. Import the **Student.postman_collection.json** into Postman.
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
   newman run Student.postman_collection.json -e Development.postman_environment.json -g workspace.postman_globals.json
   ```
4. View results in the terminal or export them as a report:
   ```bash
   newman run Student.postman_collection.json -e Development.postman_environment.json -g workspace.postman_globals.json -r html
   ```

---

## Results

- Screenshots:
  - Collection Runner summary.
  - Individual request responses.

---

## Folder Contents

- `Student.postman_collection.json`: The Postman collection for Students API.
- `screenshots/`: Screenshots showcasing test results and workflows.
- `reports/`: Newman execution reports in HTML/JSON format.
