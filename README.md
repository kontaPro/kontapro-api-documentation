### kontapro POS API ENDPOINT REFERENCE DOCUMENTATION

This document provides comprehensive details of the API endpoints available in the kontapro POS system. Each endpoint is described with its method, URL, parameters, request body (where applicable), and response format.

---

#### 1. Sales Endpoint

**Endpoint URL:** `https://easesystemtech.com/kontapro-api/sales.php`

**Description:** Manage sales data within the POS system.

##### Fetch Weekly Sales Details

- **Method:** GET
- **Operation:** Retrieve sales details for a specific week.
- **Parameters:**
  - `store_id` (string): The ID of the store.
  - `first_day_of_week` (string): The start date of the week (YYYY-MM-DD).
  - `last_day_of_week` (string): The end date of the week (YYYY-MM-DD).

**Request Example:**
```http
GET https://easesystemtech.com/kontapro-api/sales.php?store_id=121&first_day_of_week=2023-05-20&last_day_of_week=2023-05-26
```

**Response Example:**
```json
{
  "status": true,
  "weekly_sales": [
    {
      "product_name": "Product 1",
      "total_unit_sold": 10,
      "total_gross_sales": 100,
      "sold_at": "2023-05-20"
    },
    {
      "product_name": "Product 2",
      "total_unit_sold": 5,
      "total_gross_sales": 50,
      "sold_at": "2023-05-21"
    }
  ],
  "total_gross_sales_of_week": 150
}
```

##### Fetch Daily Sales Details

- **Method:** GET
- **Operation:** Retrieve sales details for a specific day.
- **Parameters:**
  - `store_id` (string): The ID of the store.
  - `date_sale` (string): The date of the sales (YYYY-MM-DD).

**Request Example:**
```http
GET https://easesystemtech.com/kontapro-api/sales.php?store_id=121&date_sale=2023-06-14
```

**Response Example:**
```json
{
  "status": true,
  "daily_sales": [
    {
      "product_name": "Product 1",
      "total_unit_sold": 5,
      "total_gross_sales": 50
    },
    {
      "product_name": "Product 2",
      "total_unit_sold": 3,
      "total_gross_sales": 30
    }
  ],
  "gross_sales_for_the_day": 80
}
```

##### Submit Sales Data

- **Method:** POST
- **Operation:** Submit sales data.
- **Request Body:**
  ```json
  {
    "store_id": "121",
    "sales": [
      {
        "product_id": "1",
        "units_sold": 2,
        "total_sales": 20
      },
      {
        "product_id": "2",
        "units_sold": 3,
        "total_sales": 30
      }
    ]
  }
  ```

**Response Example:**
```json
{
  "status": true,
  "message": "Sales data submitted successfully"
}
```

---

#### 2. Products Endpoint

**Endpoint URL:** `https://easesystemtech.com/kontapro-api/products.php`

**Description:** Manage the product catalogue within the POS system.

##### Fetch Product Catalogue

- **Method:** GET
- **Operation:** Retrieve the list of products in the store's catalogue.
- **Parameters:**
  - `store_id` (string): The ID of the store.

**Request Example:**
```http
GET https://easesystemtech.com/kontapro-api/products.php?store_id=121
```

**Response Example:**
```json
{
  "status": true,
  "product_catalogue": [
    {
      "product_id": "1",
      "product_name": "Product 1",
      "product_price": 10
    },
    {
      "product_id": "2",
      "product_name": "Product 2",
      "product_price": 20
    }
  ]
}
```

##### Add Product to Catalogue

- **Method:** POST
- **Operation:** Add a new product to the store's catalogue.
- **Request Body:**
  ```json
  {
    "store_id": "121",
    "product_name": "Product 1",
    "barcode": "123456789012",
    "price": "10.00",
    "opening_stock": "50"
  }
  ```

**Response Example:**
```json
{
  "status": true,
  "message": "Product added successfully"
}
```

---

#### 3. Stocks Endpoint

**Endpoint URL:** `https://easesystemtech.com/kontapro-api/stocks.php`

**Description:** Manage stock details within the POS system.

##### Fetch Stock Details

- **Method:** GET
- **Operation:** Retrieve the stock details for the store.
- **Parameters:**
  - `store_id` (string): The ID of the store.

**Request Example:**
```http
GET https://easesystemtech.com/kontapro-api/stocks.php?store_id=121
```

**Response Example:**
```json
{
  "status": true,
  "stock_details": [
    {
      "product_name": "Product 1",
      "product_price": 10,
      "remaining_items_in_shelves": 100
    },
    {
      "product_name": "Product 2",
      "product_price": 20,
      "remaining_items_in_shelves": 50
    }
  ]
}
```

---

#### 4. Store Accounts Endpoint

**Endpoint URL:** `https://easesystemtech.com/kontapro-api/store-accounts.php`

**Description:** Manage user authentication and registration within the POS system.

##### Login

- **Method:** POST
- **Operation:** Authenticate the user and retrieve user details.
- **Request Body:**
  ```json
  {
    "user_id": "example_user",
    "password": "example_password"
  }
  ```

**Response Example:**
```json
{
  "status": true,
  "id": "store_123",
  "username": "example_user",
  "storename": "Example Store",
  "message": "Login successful"
}
```

##### Signup

- **Method:** POST
- **Operation:** Register a new user.
- **Request Body:**
  ```json
  {
    "username": "example_user",
    "password": "example_password",
    "storename": "Example Store"
  }
  ```

**Response Example:**
```json
{
  "status": true,
  "message": "Signup successful"
}
```

> **Note:** The `process-signup` endpoint is a temporary fix and may be replaced or updated in the future. The signup process will be fully supported by the `store-accounts` endpoint.

---

This document provides a detailed reference for the API endpoints available in the kontapro POS system. Use this reference to integrate and interact with the API effectively.
