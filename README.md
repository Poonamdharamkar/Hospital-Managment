
# Hospital Management REST API

This is a simple REST API for managing hospital and ventilator details. The API allows users to add, update, search, and delete ventilator and hospital information. The project is built using Node.js and Express and uses MongoDB as the database. The API is secured with JWT authentication.

## Features

- **User Authentication**: Secure login using JWT (JSON Web Tokens).
- **Hospital Management**: Retrieve and search hospital information.
- **Ventilator Management**: 
  - Retrieve all ventilators.
  - Search ventilators by status or hospital name.
  - Add, update, and delete ventilator records.
  
## Prerequisites

- **Node.js**: Ensure you have Node.js installed on your machine. You can download it from [here](https://nodejs.org/).
- **MongoDB**: Make sure MongoDB is installed and running. You can download it from [here](https://www.mongodb.com/).

## Project Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/Poonamdharamkar/Hospital-Managment.git
   ```

2. Navigate to the project directory:
   ```bash
   cd hospital-management-api
   ```

3. Install dependencies:
   ```bash
   npm install
   ```

4. Start the MongoDB server on your local machine:
   ```bash
   mongod
   ```

5. Update the MongoDB connection string in `index.js` if necessary:
   ```javascript
   const url = 'mongodb://127.0.0.1:27017';
   const dbName = 'hospitalmanagement';
   ```

6. Start the server:
   ```bash
   node server.js
   ```

## Endpoints

### Authentication

- **POST** `/login`  
  Logs in the user and provides a JWT token.
  - Request Body: 
    ```json
    {
      "username": "string",
      "password": "string"
    }
    ```
  - Response:
    ```json
    {
      "success": true,
      "message": "Authentication successful",
      "token": "your-token"
    }
    ```

### Hospital Endpoints

- **GET** `/hospitaldetails`  
  Retrieves all hospital details. Requires authentication.

- **POST** `/searchhospital`  
  Searches hospitals by name.
  - Query Param: `Name=HospitalName`

### Ventilator Endpoints

- **GET** `/ventilatordetails`  
  Retrieves all ventilator details. Requires authentication.

- **POST** `/searchventbystatus`  
  Searches ventilators by status.
  - Request Body:
    ```json
    {
      "status": "string"
    }
    ```

- **POST** `/searchventbyname`  
  Searches ventilators by hospital name.
  - Query Param: `name=HospitalName`

- **PUT** `/updateventilator`  
  Updates the status of a ventilator.
  - Request Body:
    ```json
    {
      "ventilatorId": "string",
      "status": "string"
    }
    ```

- **POST** `/addventilatorbyuser`  
  Adds a new ventilator record.
  - Request Body:
    ```json
    {
      "hId": "string",
      "ventilatorId": "string",
      "status": "string",
      "name": "string"
    }
    ```

- **DELETE** `/delete`  
  Deletes a ventilator record by ID.
  - Query Param: `ventilatorId=VentilatorID`

## Middleware

The API is protected using JWT authentication. The `checkToken` middleware verifies the token before granting access to the secured endpoints. 

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
