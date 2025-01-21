# Enrollment API Automation Testing

## Overview

This collection automates CRUD operations for managing enrollments in the School Management System. It includes requests to create, retrieve, and delete enrollment records, along with test scripts for validation.

### Features

- **Dynamic Variables**: Captures the `EnrollmentID` dynamically from the `POST` response for use in subsequent requests.
- **Automated Assertions**:
  - Status codes.
  - Response structure and content.
- **Data-Driven Testing**: Supports bulk operations using Postman Collection Runner with CSV/JSON files.

---

## Requests in the Collection

### 1. **Enroll Student in Course**

- **Method**: `POST`
- **Endpoint**: `{{BaseURL}}{{EnrollmentEndpoint}}`
- **Headers**:
  - `Content-Type`: `application/json`
- **Body**:
  ```json
  {
    "studentId": "{{StudentID}}",
    "courseId": "{{CourseID}}",
    "enrollmentDate": "2025-06-30T09:00:00"
  }
  ```
- **Test Scripts**:
  - Validate status code is `201`.
  - Validate the response contains an `id`, `studentId`, `courseId`, and `enrollmentDate`.
  - Save `EnrollmentID` for use in subsequent requests.

---

### 2. **Get All Enrollments**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{EnrollmentEndpoint}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains an array of enrollment objects.

---

### 3. **Get Enrollments by Student ID**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{EnrollmentEndpoint}}/student/{{StudentID}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains enrollment records for the specific student.

---

### 4. **Get Enrollments by Course ID**

- **Method**: `GET`
- **Endpoint**: `{{BaseURL}}{{EnrollmentEndpoint}}/course/{{CourseID}}`
- **Test Scripts**:
  - Validate status code is `200`.
  - Validate the response contains enrollment records for the specific course.

---

### 5. **Delete Enrollment**

- **Method**: `DELETE`
- **Endpoint**: `{{BaseURL}}{{EnrollmentEndpoint}}/{{EnrollmentID}}`
- **Test Scripts**:
  - Validate status code is `204`.

---

## How to Run

### Using Postman:

1. Import the **Enrollment.postman_collection.json** into Postman.
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
   newman run Enrollment.postman_collection.json -e Development.postman_environment.json -g workspace.postman_globals.json
   ```
4. View results in the terminal or export them as a report:
   ```bash
   newman run Enrollment.postman_collection.json -e Development.postman_environment.json -g workspace.postman_globals.json -r html
   ```

---

## Results

- Screenshots:
  - Collection Runner summary.
  - Individual request responses.

---

## Folder Contents

- `Enrollment.postman_collection.json`: The Postman collection for Enrollment API.
- `screenshots/`: Screenshots showcasing test results and workflows.
- `reports/`: Newman execution reports in HTML/JSON format.
