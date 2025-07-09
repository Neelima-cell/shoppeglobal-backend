# ShoppyGlobe E-commerce Backend

A Node.js and Express.js backend for the ShoppyGlobe e-commerce application.

## Features

- Product management with MongoDB
- Shopping cart functionality
- User authentication using JWT
- Input validation and error handling
- RESTful API design

## Prerequisites

- Node.js (v14 or higher)
- MongoDB (v4 or higher)
- npm or yarn package manager

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Neelima-cell/shoppeglobal-backend.git
cd shoppeglobal-backend
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory with the following content:
```
PORT=5000
MONGO_URI=mongodb://localhost:27017/shoppyglobe
JWT_SECRET=your_jwt_secret_key_here
NODE_ENV=development
```

4. Start the server:
```bash
npm run dev
```

## API Documentation

### Authentication Routes

#### Register User
- **POST** `/register`
- **Body:**
```json
{
  "name": "string",
  "email": "string",
  "password": "string"
}
```

#### Login User
- **POST** `/login`
- **Body:**
```json
{
  "email": "string",
  "password": "string"
}
```
- **Response:** JWT token

### Product Routes

#### Get All Products
- **GET** `/products`
- **Response:** List of products

#### Get Single Product
- **GET** `/products/:id`
- **Response:** Product details

### Cart Routes (Protected - Requires JWT)

#### Add to Cart
- **POST** `/cart`
- **Body:**
```json
{
  "productId": "string",
  "quantity": "number",
  "price": "number"
}
```

#### Update Cart Item
- **PUT** `/cart/:productId`
- **Body:**
```json
{
  "quantity": "number"
}
```

#### Remove from Cart
- **DELETE** `/cart/:productId`

## Error Handling

The API implements comprehensive error handling:
- Validation errors
- Authentication errors
- Database errors
- Not found errors

## Testing

Use Thunder Client or Postman to test the APIs. Import the provided collection for testing.

## Database Schema

### Product Schema
- name (String, required)
- price (Number, required)
- description (String, required)
- stockQuantity (Number, required)
- imageUrl (String, required)
- category (String, required)
- createdAt (Date)
- updatedAt (Date)

### Cart Schema
- user (ObjectId, ref: 'User')
- items: Array of:
  - product (ObjectId, ref: 'Product')
  - quantity (Number)
  - price (Number)
- totalAmount (Number)
- createdAt (Date)
- updatedAt (Date)

## Repository

GitHub Repository: [https://github.com/Neelima-cell/shoppeglobal-backend](https://github.com/Neelima-cell/shoppeglobal-backend) 