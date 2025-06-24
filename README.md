[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19828624&assignment_repo_type=AssignmentRepo)
# Express.js RESTful API Assignment

This assignment focuses on building a RESTful API using Express.js, implementing proper routing, middleware, error handling, and advanced features.

---

## Assignment Overview

You will:
1. Set up an Express.js server
2. Create RESTful API routes for a product resource
3. Implement custom middleware for logging, authentication, and validation
4. Add comprehensive error handling
5. Develop advanced features like filtering, pagination, search, and statistics

---

## Getting Started

1. Accept the GitHub Classroom assignment invitation
2. Clone your personal repository that was created by GitHub Classroom
3. Install dependencies:
   ```
   npm install
   ```
4. Run the server:
   ```
   npm start
   ```

---

## Files Included

- `Week2-Assignment.md`: Detailed assignment instructions
- `server.js`: Express.js server file with all routes and middleware
- `.env.example`: Example environment variables file

---

## Requirements

- Node.js (v18 or higher)
- npm or yarn
- Postman, Insomnia, or curl for API testing

---

## Environment Variables

Copy `.env.example` to `.env` and set your values:

```
API_KEY=my-secret-key
PORT=3000
```

---

## API Authentication

All endpoints require the following header:

```
x-api-key: my-secret-key
```

---

## API Endpoints

### Products

| Method | Endpoint                | Description                |
|--------|-------------------------|----------------------------|
| GET    | `/api/products`         | Get all products (supports filtering, pagination, search) |
| GET    | `/api/products/:id`     | Get a specific product by ID |
| POST   | `/api/products`         | Create a new product       |
| PUT    | `/api/products/:id`     | Update a product           |
| DELETE | `/api/products/:id`     | Delete a product           |

### Advanced

| Method | Endpoint                | Description                |
|--------|-------------------------|----------------------------|
| GET    | `/api/products-stats`   | Get product statistics (count by category) |

---

## Query Parameters

- `category` (string): Filter products by category
- `search` (string): Search products by name
- `page` (number): Page number for pagination (default: 1)
- `limit` (number): Items per page (default: 10)

**Example:**  
`GET /api/products?category=electronics&search=laptop&page=1&limit=5`

---

## Example Requests & Responses

### Get All Products

**Request:**
```
GET /api/products
x-api-key: my-secret-key
```

**Response:**
```json
{
  "total": 2,
  "page": 1,
  "limit": 10,
  "products": [
    {
      "id": "1",
      "name": "Laptop",
      "description": "High-performance laptop with 16GB RAM",
      "price": 1200,
      "category": "electronics",
      "inStock": true
    }
  ]
}
```

### Create a Product

**Request:**
```
POST /api/products
x-api-key: my-secret-key
Content-Type: application/json
```
```json
{
  "name": "Tablet",
  "description": "10-inch Android tablet",
  "price": 300,
  "category": "electronics",
  "inStock": true
}
```

**Response:**
```json
{
  "id": "generated-uuid",
  "name": "Tablet",
  "description": "10-inch Android tablet",
  "price": 300,
  "category": "electronics",
  "inStock": true
}
```

### Error Example

**Request:**  
`GET /api/products/invalid-id`

**Response:**
```json
{
  "error": "Product not found"
}
```

---

## Middleware Implemented

- **Logger:** Logs request method, URL, and timestamp
- **Authentication:** Checks for API key in headers
- **Validation:** Validates product data on create/update
- **Error Handling:** Global error handler with proper status codes

---

## How to Test

Use Postman, Insomnia, or curl.  
**Always include the header:**  
`x-api-key: my-secret-key`

**Example with curl:**
```sh
curl -H "x-api-key: my-secret-key" http://localhost:3000/api/products
```

---

## Submission

Your work will be automatically submitted when you push to your GitHub Classroom repository. Make sure to:

1. Complete all the required API endpoints
2. Implement the middleware and error handling
3. Document your API in the README.md
4. Include examples of requests and responses

---

## Resources

- [Express.js Documentation](https://expressjs.com/)
- [RESTful API Design Best Practices](https://restfulapi.net/)
- [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)