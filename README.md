Certainly! Here's the updated README-style file with the note added:

---

# KontaPro API Documentation

Welcome to the KontaPro API documentation. This API provides endpoints to manage store accounts, products, stocks, sales, and user authentication for your business needs.

## Base URL

The base URL for accessing KontaPro API endpoints is:

```
https://easesystemtech.com/kontapro-api/
```

## Endpoints

### 1. Store Accounts

**Create Store Account**

- **Method:** POST
- **URL:** `/store-accounts`
- **Description:** Creates a new store account.

  **Request Body Example:**
  ```json
  {
    "name": "string",
    "address": "string",
    "phone": "string",
    "email": "string"
  }
  ```

  **Response Example:**
  ```json
  {
    "storeId": "string",
    "name": "string",
    "address": "string",
    "phone": "string",
    "email": "string"
  }
  ```

**Retrieve Store Account**

- **Method:** GET
- **URL:** `/store-accounts/{storeId}`
- **Description:** Retrieves information about a specific store account identified by `storeId`.

  **Response Example:**
  ```json
  {
    "storeId": "string",
    "name": "string",
    "address": "string",
    "phone": "string",
    "email": "string"
  }
  ```

**Temporary Signup Process**

- **Method:** POST
- **URL:** `/store-accounts/processSignup`
- **Description:** Temporary endpoint allowing users to sign up for an account. This endpoint is a temporary fix.

  **Request Body Example:**
  ```json
  {
    "store-owner": "string",
    "account-password": "string",
    "owner-contact-number": "string"
  }
  ```

  **Response Example:**
  ```json
  {
    "id": "string",
    "username": "string"
  }
  ```

### 2. Store Stocks

**Retrieve Stock Levels**

- **Method:** GET
- **URL:** `/store-accounts.php/{storeId}`
- **Description:** Retrieves the stock levels of all products for the store identified by `storeId`.

  **Response Example:**
  ```json
  [
    {
      "productId": "string",
      "name": "string",
      "description": "string",
      "price": "number",
      "stockLevel": "number"
    },
    {
      "productId": "string",
      "name": "string",
      "description": "string",
      "price": "number",
      "stockLevel": "number"
    },
    ...
  ]
  ```

**Search Stock Levels**

- **Method:** GET
- **URL:** `/store-accounts.php/{storeId}{$searchKeyWord}`
- **Description:** Retrieves the stock levels of products that match the `searchKeyWord` for the store identified by `storeId`.

  **Response Example:**
  ```json
  [
    {
      "productId": "string",
      "name": "string",
      "description": "string",
      "price": "number",
      "stockLevel": "number"
    },
    {
      "productId": "string",
      "name": "string",
      "description": "string",
      "price": "number",
      "stockLevel": "number"
    },
    ...
  ]
  ```

### 3. Store Products

**Create Product**

- **Method:** POST
- **URL:** `/products.php`
- **Description:** Creates a new product for a store.

  **Request Body Example:**
  ```json
  {
    "storeId": "string",
    "name": "string",
    "description": "string",
    "price": "number",
    "stockLevel": "number"
  }
  ```

  **Response Example:**
  ```json
  {
    "productId": "string",
    "storeId": "string",
    "name": "string"
  }
  ```

**Retrieve Products**

- **Method:** GET
- **URL:** `/products.php/{storeId}`
- **Description:** Retrieves a list of all products available in a specific store identified by `storeId`.

  **Response Example:**
  ```json
  [
    {
      "productId": "string",
      "storeId": "string",
      "name": "string",
      "description": "string",
      "price": "number",
      "stockLevel": "number"
    },
    {
      "productId": "string",
      "storeId": "string",
      "name": "string",
      "description": "string",
      "price": "number",
      "stockLevel": "number"
    },
    ...
  ]
  ```

**Update Product**

- **Method:** PUT
- **URL:** `/products.php/{storeId}`
- **Description:** Updates details of an existing product in the store such as name, description, price, and stock level.

  **Request Body Example:**
  ```json
  {
    "storeId": "string",
    "productId": "string",
    "name": "string",
    "description": "string",
    "price": "number",
    "stockLevel": "number"
  }
  ```

  **Response Example:**
  ```json
  {
    "status": "success",
    "message": "Product updated successfully"
  }
  ```

### 4. Store Sales

**Create Sales Record**

- **Method:** POST
- **URL:** `/sales.php`
- **Description:** Creates a new sales record for a store.

  **Request Body Example:**
  ```json
  {
    "storeId": "string",
    "products": [
      {
        "productId": "string",
        "quantity": "number"
      },
      {
        "productId": "string",
        "quantity": "number"
      },
      ...
    ],
    "totalPrice": "number",
    "date": "string"
  }
  ```

  **Response Example:**
  ```json
  {
    "salesId": "string",
    "storeId": "string",
    "products": [
      {
        "productId": "string",
        "quantity": "number"
      },
      {
        "productId": "string",
        "quantity": "number"
      },
      ...
    ],
    "totalPrice": "number",
    "date": "string"
  }
  ```

**Retrieve Sales Records**

- **Method:** GET
- **URL:** `/sales.php/{storeId}{$productId}{$productId}`
- **Description:** Retrieves sales records for a store identified by `storeId` for the products identified by `productId`.

  **Response Example:**
  ```json
  [
    {
      "salesId": "string",
      "storeId": "string",
      "products": [
        {
          "productId": "string",
          "quantity": "number"
        },
        {
          "productId": "string",
          "quantity": "number"
        },
        ...
      ],
      "totalPrice": "number",
      "date": "string"
    },
    {
      "salesId": "string",
      "storeId": "string",
      "products": [
        {
          "productId": "string",
          "quantity": "number"
        },
        {
          "productId": "string",
          "quantity": "number"
        },
        ...
      ],
      "totalPrice": "number",
      "date": "string"
    },
    ...
  ]
  ```

---

This README-style document provides comprehensive information about each endpoint in the KontaPro API, including request body examples and response structures. Use this guide to understand how to interact with the API effectively for managing store operations and sales. Adjust parameters and utilize appropriate HTTP methods (`POST`, `GET`, `PUT`) as per your application's requirements. Replace placeholders (`{storeId}`, `{productId}`, etc.) with actual values when making API requests.

**Note:** The `/store-accounts/processSignup` endpoint is a temporary solution to allow users to sign up for accounts. It is subject to change or removal in future updates.
