# Class API Automation Testing

## Overview

This collection automates CRUD operations for managing classes in the School Management System. It includes requests to create, retrieve, update, and delete class records, along with test scripts for validation.

### Features

- **Dynamic Variables**: Captures the `ClassID` dynamically from the `POST` response for use in subsequent requests.
- **Automated Assertions**:
  - Status codes.
  - Response structure and content.
- **Data-Driven Testing**: Supports bulk operations using Postman Collection Runner with CSV/JSON files.

---

## Requests in the Collection

### 1. **Create Class**

- **Method**: `POST`
- **Endpoint**: `{{BaseURL}}{{ClassEndpoint}}`
- **Headers**:
  - `Content-Type`: `application/json`
- **Body**:
  ```json
  {
    "courseId": "{{CourseID}}",
    "room": "{{ClassRoom}}",
    "schedule": "2024-12-30T09:00:00"
  }
  ```
- **Test Scripts**:
  - Validate status code is `201`.
  - Validate the response contains `id`, `courseId`, `room`, and `schedule`.
  - Save `ClassID` for use in subsequent requests.

---

### 2. **Get All Classes**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{ClassEndpoint}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains an array of class objects.

---

### 3. **Get Class by ID**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{ClassEndpoint}}/{{ClassID}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains `id`, `courseId`, `room`, and `schedule`.

---

### 4. **Update Class**

- **Method**: `PUT`
- **Endpoint**: `{{BaseURL}}{{ClassEndpoint}}/{{ClassID}}`
- **Body**:
  ```json
  {
    "courseId": "{{CourseID}}",
    "room": "Lab 401",
    "schedule": "2025-02-15T09:00:00"
  }
  ```
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains updated `id`, `courseId`, `room`, and `schedule`.

---

### 5. **Delete Class**

- **Method**: `DELETE`
- **Endpoint**: `{{BaseURL}}{{ClassEndpoint}}/{{ClassID}}`
- **Test Scripts**:
  - Validate status code is `204`.

---

## How to Run

### Using Postman:

1. Import the **Class.postman_collection.json** into Postman.
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
   newman run Class.postman_collection.json -e Development.postman_environment.json -g workspace.postman_globals.json
   ```
4. View results in the terminal or export them as a report:
   ```bash
   newman run Class.postman_collection.json -e Development.postman_environment.json -g workspace.postman_globals.json -r html
   ```

---

## Results

- Screenshots:
  - Collection Runner summary.
  - Individual request responses.

---

## Folder Contents

- `Class.postman_collection.json`: The Postman collection for Class API.
- `screenshots/`: Screenshots showcasing test results and workflows.
- `reports/`: Newman execution reports in HTML/JSON format.
