# Course API Automation Testing

## Overview

This collection automates CRUD operations for managing courses in the School Management System. It includes requests to create, retrieve, update, and delete course records, along with test scripts for validation.

### Features

- **Dynamic Variables**: Captures the `CourseID` dynamically from the `POST` response for use in subsequent requests.
- **Automated Assertions**:
  - Status codes.
  - Response structure and content.
- **Data-Driven Testing**: Supports bulk operations using Postman Collection Runner with CSV/JSON files.

---

## Requests in the Collection

### 1. **Create Course**

- **Method**: `POST`
- **Endpoint**: `{{BaseURL}}{{CourseEndpoint}}`
- **Headers**:
  - `Content-Type`: `application/json`
- **Body**:
  ```json
  {
    "name": "Java Zero to Hero",
    "description": "The best Java course you have ever needed",
    "teacherId": "{{TeacherID}}"
  }
  ```
- **Test Scripts**:
  - Validate status code is `201`.
  - Validate the response contains `id`, `name`, `description`, and `teacherId`.
  - Save `CourseID` for use in subsequent requests.

---

### 2. **Get All Courses**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{CourseEndpoint}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains an array of course objects.

---

### 3. **Get Course by ID**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{CourseEndpoint}}/{{CourseID}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains `id`, `name`, `description`, and `teacherId`.

---

### 4. **Update Course**

- **Method**: `PUT`
- **Endpoint**: `{{BaseURL}}{{CourseEndpoint}}/{{CourseID}}`
- **Body**:
  ```json
  {
    "name": "Python Zero to Hero",
    "description": "The best Python course that you have ever needed",
    "teacherId": "{{TeacherID}}"
  }
  ```
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains updated `id`, `name`, `description`, and `teacherId`.

---

### 5. **Delete Course**

- **Method**: `DELETE`
- **Endpoint**: `{{BaseURL}}{{CourseEndpoint}}/{{CourseID}}`
- **Test Scripts**:
  - Validate status code is `204`.

---

## How to Run

### Using Postman:

1. Import the **Course.postman_collection.json** into Postman.
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
   newman run Course.postman_collection.json -e Development.postman_environment.json -g workspace.postman_globals.json
   ```
4. View results in the terminal or export them as a report:
   ```bash
   newman run Course.postman_collection.json -e Development.postman_environment.json -g workspace.postman_globals.json -r html
   ```

---

## Results

- Screenshots:
  - Collection Runner summary.
  - Individual request responses.

---

## Folder Contents

- `Course.postman_collection.json`: The Postman collection for Course API.
- `screenshots/`: Screenshots showcasing test results and workflows.
- `reports/`: Newman execution reports in HTML/JSON format.
