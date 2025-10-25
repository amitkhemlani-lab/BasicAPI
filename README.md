# BasicAPI - Customer Management System

A simple CRUD API built with Express.js and MongoDB to manage customer data.

## Features

- Create new customers
- Retrieve all customers
- Retrieve a single customer by ID
- Update customer information
- Delete customers
- Input validation
- Error handling

## Tech Stack

- Node.js
- Express.js
- MongoDB
- Mongoose ODM

## Installation

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the root directory based on `.env.example`:
   ```
   PORT=3000
   MONGODB_URI=mongodb://localhost:27017/basicapi
   ```

4. Make sure MongoDB is running on your system

5. Start the server:
   ```bash
   npm start
   ```

   For development with auto-reload:
   ```bash
   npm run dev
   ```

## API Endpoints

### Base URL
```
http://localhost:3000
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Welcome message and API info |
| POST | `/api/customers` | Create a new customer |
| GET | `/api/customers` | Get all customers |
| GET | `/api/customers/:id` | Get a customer by ID |
| PUT | `/api/customers/:id` | Update a customer |
| DELETE | `/api/customers/:id` | Delete a customer |

### Customer Schema

```json
{
  "firstName": "string (required)",
  "lastName": "string (required)",
  "email": "string (required, unique)",
  "phone": "string",
  "address": {
    "street": "string",
    "city": "string",
    "state": "string",
    "zipCode": "string",
    "country": "string"
  },
  "status": "string (active/inactive, default: active)"
}
```

## Example Usage

### Create a Customer
```bash
curl -X POST http://localhost:3000/api/customers \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com",
    "phone": "555-1234",
    "address": {
      "street": "123 Main St",
      "city": "New York",
      "state": "NY",
      "zipCode": "10001",
      "country": "USA"
    }
  }'
```

### Get All Customers
```bash
curl http://localhost:3000/api/customers
```

### Get a Customer by ID
```bash
curl http://localhost:3000/api/customers/{customer_id}
```

### Update a Customer
```bash
curl -X PUT http://localhost:3000/api/customers/{customer_id} \
  -H "Content-Type: application/json" \
  -d '{
    "phone": "555-5678",
    "status": "inactive"
  }'
```

### Delete a Customer
```bash
curl -X DELETE http://localhost:3000/api/customers/{customer_id}
```

## Response Format

### Success Response
```json
{
  "success": true,
  "message": "Operation successful",
  "data": { ... }
}
```

### Error Response
```json
{
  "success": false,
  "message": "Error message"
}
```

## License

ISC
