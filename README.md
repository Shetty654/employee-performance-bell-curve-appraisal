# Employee Performance Bell Curve Appraisal System

## Description
This is a Spring Boot application that calculates employee performance based on the bell curve method. The app allows you to input employee ratings, calculate actual and standard percentages, and suggest employees whose ratings need revision based on the deviation.

## Installation Instructions

1. Clone this repository:

2. Navigate to the project directory:

3. Install dependencies (make sure you have JDK 11+ and Maven installed):

4. Run the application:

The app will run on `http://localhost:8080`.

## Usage Instructions

Once the application is running, you can use the following endpoints:

### 1. **Add Employee**
- **Endpoint**: `POST /api/public/employees`
- **Request Body**:
  ```json
  {
    "employeeName": "John Doe",
    "rating": "OUTSTANDING"
  }
  ```
- **Response**:
  ```json
  {
    "employeeId": 1,
    "employeeName": "John Doe",
    "rating": "OUTSTANDING"
  }
  ```

### 2. **Get All Employees**
- **Endpoint**: `GET /api/public/employees`
- **Query Params**:
  - `pageNumber`: (Optional) Page number for pagination (default: 0)
  - `pageSize`: (Optional) Number of employees per page (default: 10)
  - `sortBy`: (Optional) Sort by field (default: "employeeName")
  - `sortOrder`: (Optional) Sort order (default: "ASC")
- **Response**:
  ```json
  {
    "employees": [
      {
        "employeeId": 1,
        "employeeName": "John Doe",
        "rating": "OUTSTANDING"
      },
      {
        "employeeId": 2,
        "employeeName": "Jane Smith",
        "rating": "VERY_GOOD"
      }
    ],
    "totalEmployees": 2,
    "totalPages": 1
  }
  ```

### 3. **Calculate Bell Curve**
- **Endpoint**: `POST /api/public/calculate-bell-curve`
- **Response** (If revisions are required):
  ```json
  {
    "message": "Bell curve calculation completed. Employees to revise:",
    "success": true,
    "data": [
      {
        "employeeId": 2,
        "employeeName": "Jane Smith",
        "rating": "VERY_GOOD"
      },
      {
        "employeeId": 5,
        "employeeName": "Charlie Williams",
        "rating": "LOW_PERFORMER"
      }
    ]
  }
  ```
## Sample SQL Queries

Here are some sample SQL queries you can use to insert data into the database and test the application:

### 1. **Insert Employees**

To add some employees to the database:

```sql
INSERT INTO employee (EMPLOYEE_ID, EMPLOYEE_NAME, RATING)
VALUES (1, 'John Doe', 'OUTSTANDING');

INSERT INTO employee (EMPLOYEE_ID, EMPLOYEE_NAME, RATING)
VALUES (2, 'Jane Smith', 'VERY_GOOD');

INSERT INTO employee (EMPLOYEE_ID, EMPLOYEE_NAME, RATING)
VALUES (3, 'Alice Johnson', 'GOOD');

INSERT INTO employee (EMPLOYEE_ID, EMPLOYEE_NAME, RATING)
VALUES (4, 'Bob Brown', 'NEEDS_IMPROVEMENT');

INSERT INTO employee (EMPLOYEE_ID, EMPLOYEE_NAME, RATING)
VALUES (5, 'Charlie Williams', 'LOW_PERFORMER');

INSERT INTO appraisal (GOOD_PERCENTAGE, LOW_PERFORMER_PERCENTAGE, NEEDS_IMPROVEMENT_PERCENTAGE, OUTSTANDING_PERCENTAGE, VERY_GOOD_PERCENTAGE)
VALUES (25.0, 10.0, 15.0, 20.0, 30.0);

## Technologies Used
- **Spring Boot**: For building the REST API.
- **Java**: For backend logic.
- **H2 Database** (or your preferred DB): For storing employee data.
- **Maven**: For dependency management.
- **Lombok**: For boilerplate code reduction.
- **JPA/Hibernate**: For database interaction.

## Contributing
Feel free to fork this project and submit pull requests. Ensure to follow standard Git workflow.
