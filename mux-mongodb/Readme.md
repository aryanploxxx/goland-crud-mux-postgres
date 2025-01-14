# Mux-MongoDB CRUD Application

This project demonstrates a CRUD (Create, Read, Update, Delete) application using Go, Gorilla Mux, and MongoDB. The application provides RESTful APIs to manage employee records in a MongoDB database.

## Setup

1. **Clone the repository:**

   ```sh
   git clone https://github.com/aryanploxxx/golang-crud.git
   cd mux-mongodb
   ```
2. Create a .env file
   ```sh
    touch .env

    MONGO_URI = "your-mongodb-uri"
    DB_NAME = "companydb"
    COLLECTION_NAME = "employees"
   ```
3. Install dependencies:

   ```sh
    go mod tidy
   ```
4. Run the application:

   ```sh
    go run main.go
   ```

## API Endpoints

### Health Check
- Endpoint: /health
- Method: GET
- Description: Checks if the server is running.
### Create Employee
- Endpoint: /employee
- Method: POST
- Description: Creates a new employee.
- Request Body:
   ```sh
   {
    "name": "John Doe",
    "department": "Engineering"
  }
  ```
### Create Many Employees
- Endpoint: /employees
- Method: POST
- Description: Creates multiple employees.
- Request Body:
   ```sh
    [
      {
        "name": "John Doe",
        "department": "Engineering"
      },
      {
        "name": "Jane Smith",
        "department": "Marketing"
      }
    ]
  ```
### Get Employee by ID
- Endpoint: /employee/{id}
- Method: GET
- Description: Retrieves an employee by ID.

### Get All Employees
- Endpoint: /employee
- Method: GET
- Description: Retrieves all employees.

### Update Employee by ID
- Endpoint: /employee/{id}
- Method: PUT
- Description: Updates an employee by ID.
- Request Body:
     ```sh
    {
      "name": "John Doe",
      "department": "Engineering"
    }
  ```

### Upsert Employee
- Endpoint: /employee/upsert
- Method: PUT
- Description: Inserts or updates an employee.
- Request Body:
  ```sh
     {
      "employee_id": "12345",
      "name": "John Doe",
      "department": "Engineering"
    }
  ```

### Update Many Employees
- Endpoint: /employees/update
- Method: PUT
- Description: Updates multiple employees based on a filter.
- Request Body:
   ```sh
     {
      "filter": {
        "department": "Engineering"
      },
      "update": {
        "$set": {
          "department": "Tech"
        }
      }
    }
  ```

### Bulk Write Employees
- Endpoint: /employees/bulk
- Method: POST
- Description: Performs bulk write operations.
- Request Body:
  ```sh
   [
      {
        "insertOne": {
          "document": {
            "name": "John Doe",
            "department": "Engineering"
          }
        }
      },
      {
        "updateOne": {
          "filter": { "employee_id": "12345" },
          "update": { "$set": { "department": "Tech" } }
        }
      }
  ]
  ```

### Delete Employee by ID
- Endpoint: /employee/{id}
- Method: DELETE
- Description: Deletes an employee by ID.

### Delete All Employees
- Endpoint: /employee
- Method: DELETE
- Description: Deletes all employees.





