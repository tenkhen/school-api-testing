# School API Testing

## Overview

This repository demonstrates comprehensive API testing for a School Management System. It covers both **manual testing** and **automation testing**, showcasing CRUD operations for core entities like Teachers, Students, Courses, Classes, and Enrollments. The testing process includes detailed documentation, organized collections, and dynamic reporting to highlight proficiency in API testing.

---

## Creator

This testing framework and all related documentation were created by [**Khenrab Dorjee Lama**](https://khenrab.io). It is designed to showcase robust API testing practices using Postman and Newman.

### Related Repository

This testing suite is based on the **School API**, which is available on GitHub:
[School API Repository](https://github.com/tenkhen/school-api)

---

## Folder Structure

### 1. **Automation Testing**

#### Path: `automation-testing`

This folder contains automated API tests using Postman and Newman.

- **Subfolders**:

  - `postman-collections/`

    - Contains individual folders for each entity:

      - **Class**: Includes CRUD operation collections, reports, screenshots, and a README.
      - **Course**: Includes CRUD operation collections, reports, screenshots, and a README.
      - **Enrollment**: Includes CRUD operation collections, reports, screenshots, and a README.
      - **Student**: Includes CRUD operation collections, reports, screenshots, and a README.
      - **Teacher**: Includes CRUD operation collections, reports, screenshots, and a README.

    - **Contents of Each Folder**:
      - `README.md`: Documentation for the respective API.
      - `*.postman_collection.json`: Postman collection for the entity.
      - `reports/`: Newman reports (HTML and JSON formats).
      - `screenshots/`: Screenshots of CRUD operation responses.

  - `postman-environments/`
    - Contains Postman environment files:
      - `Production.postman_environment.json`
      - `Development.postman_environment.json`
      - `workspace.postman_globals.json`

---

### 2. **Manual Testing**

#### Path: `manual-testing`

This folder showcases manual API testing, including test cases and corresponding resources.

- **Subfolders**:

  - `test-cases/`

    - Excel files documenting detailed test cases for each entity:
      - `Teacher-Test-Cases.xlsx`
      - `Student-Test-Cases.xlsx`
      - `Enrollment-Test-Cases.xlsx`
      - `Course-Test-Cases.xlsx`
      - `Class-Test-Cases.xlsx`

  - `postman-environments/`

    - Contains environment files for manual testing:
      - `Production.postman_environment.json`
      - `Development.postman_environment.json`
      - `workspace.postman_globals.json`
    - `screenshots/`: Screenshots of the environment configurations.

  - `postman-collections/`
    - Contains individual folders for each entity:
      - **Class**: Postman collection JSON file and screenshots for manual testing.
      - **Course**: Postman collection JSON file and screenshots for manual testing.
      - **Enrollment**: Postman collection JSON file and screenshots for manual testing.
      - **Student**: Postman collection JSON file and screenshots for manual testing.
      - **Teacher**: Postman collection JSON file and screenshots for manual testing.

---

## How to Navigate

### Automation Testing

1. Navigate to `automation-testing/postman-collections/`.
2. Select an entity folder (e.g., `Teacher`).
3. Refer to the `README.md` for details about:
   - How to run the collection using Postman or Newman.
   - Description of requests and test scripts.
4. View execution results in the `reports/` folder and screenshots in the `screenshots/` folder.

### Manual Testing

1. Navigate to `manual-testing/test-cases/` to review Excel files documenting test cases.
2. Open `manual-testing/postman-collections/` for individual folders containing:
   - Postman collection JSON files.
   - Screenshots of manual test executions.
3. Use `manual-testing/postman-environments/` for environment details and screenshots.

---

## How to Run Automation Tests

### Prerequisites

1. Install [Node.js](https://nodejs.org/).
2. Install Newman:
   ```bash
   npm install -g newman
   ```
3. Install Newman HTML Reporter:
   ```bash
   npm install -g newman-reporter-html
   ```

### Steps

1. Navigate to the desired collection folder under `automation-testing/postman-collections/`.
2. Run the Newman command:
   ```bash
   newman run <CollectionFile>.postman_collection.json \
       -e <EnvironmentFile>.postman_environment.json \
       -g <workspace>.postman_globals.json \
       -r cli,html --reporter-html-export <ReportOutputPath>
   ```
3. Example for Teacher:
   ```bash
   newman run Teacher.postman_collection.json \
       -e Production.postman_environment.json \
       -g workspace.postman_globals.json \
       -r cli,html --reporter-html-export ./reports/teacher_report.html
   ```

---

## Linking Individual README Files

Each API entity has its own README for detailed documentation:

- [Class API](automation-testing/postman-collections/Class/README.md)
- [Course API](automation-testing/postman-collections/Course/README.md)
- [Enrollment API](automation-testing/postman-collections/Enrollment/README.md)
- [Student API](automation-testing/postman-collections/Student/README.md)
- [Teacher API](automation-testing/postman-collections/Teacher/README.md)

---

## Contact

For any questions or feedback, reach out to **[Khenrab Dorjee Lama](mailto:tenkhen@gmail.com)**.
