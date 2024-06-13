# kontapro-api-documentation

1. store-accounts end point:  

[post] https://easesystemtech.com/kontapro-api/store-accounts
       

[Get] https://easesystemtech.com/kontapro-api/store-accountsstore-accounts/{storeId}
      

2. Store stocks endpoint: 

[Get] https://easesystemtech.com/kontapro-api/store-accounts.php/{storeId}

[Get] https://easesystemtech.com/kontapro-api/store-accounts.php/{storeId}{$searchKeyWord}

3. Store products endpoint: 

[Post] https://easesystemtech.com/kontapro-api/products.php

[Get] https://easesystemtech.com/kontapro-api/products.php{storeId}

[Get] www.kontapro.com/kontapro-api/products/{storeId}{$searchKeyWord}

[Put] www.kontapro.com/kontapro-api/products/{storeId}


5. Store sales endpoint: 

[Post] https://easesystemtech.com/kontapro-api/stocks.php

[Get] https://easesystemtech.com/kontapro-api/stocks.php/{storeId}{$productId}{$productId}

#Documentation draft:

Sure! Here are the JSON response bodies for the endpoints in your REST API:

**1. Store Accounts Endpoints**

- [POST] /store-accounts

Creates a new store account.

Request body:

```json
{
  "name": "string",
  "address": "string",
  "phone": "string",
  "email": "string"
}
```

Response body:

```json
{
  "storeId": "string",
  "name": "string",
  "address": "string",
  "phone": "string",
  "email": "string"
}
```

- [GET] /store-accounts/{storeId}

Retrieves information about a specific store account identified by `storeId`.

Response body:

```json
{
  "storeId": "string",
  "name": "string",
  "address": "string",
  "phone": "string",
  "email": "string"
}
```


**3. Store Stocks Endpoints**

- [GET] /stocks/{storeId}

Retrieves the stock levels of all products for the store identified by `storeId`.

Response body:

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

- [GET] /stocks/{storeId}{$searchKeyWord}

Retrieves the stock levels of products that match the `searchKeyWord` for the store identified by `storeId`.

Response body:

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

**4. Store Products Endpoints**

- [POST] /products

Creates a new product for a store.

Request body:

```json
{
  "storeId": "string",
  "name": "string",
  "description": "string",
  "price": "number",
  "stockLevel": "number"
}
```

Response body:

```json
{
  "productId": "string",
  "storeId": "string",
  "name": "string"
}

```

**5. Store Sales Endpoints**

- [POST] /sales

Creates a new sales record for a store.

Request body:

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

Response body:

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

- [GET] /sales/{storeId}{$productId}{$productId}

Retrieves sales records for a store identified by `storeId` for the products identified by `productId`.

Response body:

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
