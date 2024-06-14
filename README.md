### DOCUMENTAÇÃO DE REFERÊNCIA DOS ENDPOINTS DA API KONTAPRO POS

Este documento fornece detalhes abrangentes dos endpoints  disponíveis na API  do   Kontapro POS, Cada endpoint é descrito com seu métodos, URL, parâmetros, corpo da requisição (quando aplicável) e formato da resposta.

### Ferramenta para testar: Postman ou similares.
---

#### 1. Endpoint de Vendas

**URL do Endpoint:** `https://easesystemtech.com/kontapro-api/sales.php`

**Descrição:** Gerenciar dados de vendas dentro do sistema POS.

##### Buscar Detalhes Semanais de Vendas

- **Método:** GET
- **Operação:** Recuperar detalhes de vendas para uma semana específica.
- **Parâmetros:**
  - `store_id` (string): O ID da loja.
  - `first_day_of_week` (string): Data de início da semana (AAAA-MM-DD).
  - `last_day_of_week` (string): Data de fim da semana (AAAA-MM-DD).

**Exemplo de Requisição:**
```http
GET https://easesystemtech.com/kontapro-api/sales.php?store_id=121&first_day_of_week=2023-05-20&last_day_of_week=2023-05-26
```

**Exemplo de Resposta:**
```json
{
  "status": true,
  "weekly_sales": [
    {
      "product_name": "Produto 1",
      "total_unit_sold": 10,
      "total_gross_sales": 100,
      "sold_at": "2023-05-20"
    },
    {
      "product_name": "Produto 2",
      "total_unit_sold": 5,
      "total_gross_sales": 50,
      "sold_at": "2023-05-21"
    }
  ],
  "total_gross_sales_of_week": 150
}
```

##### Buscar Detalhes Diários de Vendas

- **Método:** GET
- **Operação:** Recuperar detalhes de vendas para um dia específico.
- **Parâmetros:**
  - `store_id` (string): O ID da loja.
  - `date_sale` (string): Data das vendas (AAAA-MM-DD).

**Exemplo de Requisição:**
```http
GET https://easesystemtech.com/kontapro-api/sales.php?store_id=121&date_sale=2023-06-14
```

**Exemplo de Resposta:**
```json
{
  "status": true,
  "daily_sales": [
    {
      "product_name": "Produto 1",
      "total_unit_sold": 5,
      "total_gross_sales": 50
    },
    {
      "product_name": "Produto 2",
      "total_unit_sold": 3,
      "total_gross_sales": 30
    }
  ],
  "gross_sales_for_the_day": 80
}
```

##### Submeter Dados de Vendas

- **Método:** POST
- **Operação:** Enviar dados de vendas.
- **Corpo da Requisição:**
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

**Exemplo de Resposta:**
```json
{
  "status": true,
  "message": "Dados de vendas enviados com sucesso"
}
```

---

#### 2. Endpoint de Produtos

**URL do Endpoint:** `https://easesystemtech.com/kontapro-api/products.php`

**Descrição:** Gerenciar o catálogo de produtos dentro do sistema POS.

##### Buscar Catálogo de Produtos

- **Método:** GET
- **Operação:** Recuperar a lista de produtos no catálogo da loja.
- **Parâmetros:**
  - `store_id` (string): O ID da loja.

**Exemplo de Requisição:**
```http
GET https://easesystemtech.com/kontapro-api/products.php?store_id=121
```

**Exemplo de Resposta:**
```json
{
  "status": true,
  "product_catalogue": [
    {
      "product_id": "1",
      "product_name": "Produto 1",
      "product_price": 10
    },
    {
      "product_id": "2",
      "product_name": "Produto 2",
      "product_price": 20
    }
  ]
}
```

##### Adicionar Produto ao Catálogo

- **Método:** POST
- **Operação:** Adicionar um novo produto ao catálogo da loja.
- **Corpo da Requisição:**
  ```json
  {
    "store_id": "121",
    "product_name": "Produto 1",
    "barcode": "123456789012",
    "price": "10,00",
    "opening_stock": "50"
  }
  ```

**Exemplo de Resposta:**
```json
{
  "status": true,
  "message": "Produto adicionado com sucesso"
}
```

---

#### 3. Endpoint de Estoques

**URL do Endpoint:** `https://easesystemtech.com/kontapro-api/stocks.php`

**Descrição:** Gerenciar detalhes de estoque dentro do sistema POS.

##### Buscar Detalhes de Estoque

- **Método:** GET
- **Operação:** Recuperar os detalhes de estoque para a loja.
- **Parâmetros:**
  - `store_id` (string): O ID da loja.

**Exemplo de Requisição:**
```http
GET https://easesystemtech.com/kontapro-api/stocks.php?store_id=121
```

**Exemplo de Resposta:**
```json
{
  "status": true,
  "stock_details": [
    {
      "product_name": "Produto 1",
      "product_price": 10,
      "remaining_items_in_shelves": 100
    },
    {
      "product_name": "Produto 2",
      "product_price": 20,
      "remaining_items_in_shelves": 50
    }
  ]
}
```

---

#### 4. Endpoint de Contas da Loja

**URL do Endpoint:** `https://easesystemtech.com/kontapro-api/store-accounts.php`

**Descrição:** Gerenciar autenticação e registro de usuários dentro do sistema POS.

##### Login

- **Método:** POST
- **Operação:** Autenticar o usuário e recuperar detalhes do usuário.
- **Corpo da Requisição:**
  ```json
  {
    "user_id": "exemplo_usuario",
    "password": "exemplo_senha"
  }
  ```

**Exemplo de Resposta:**
```json
{
  "status": true,
  "id": "store_123",
  "username": "exemplo_usuario",
  "storename": "Exemplo de Loja",
  "message": "Login realizado com sucesso"
}
```

##### Cadastro

- **Método:** POST
- **Operação:** Registrar um novo usuário.
- **Corpo da Requisição:**
  ```json
  {
    "username": "exemplo_usuario",
    "password": "exemplo_senha",
    "storename": "Exemplo de Loja"
  }
  ```

**Exemplo de Resposta:**
```json
{
  "status": true,
  "message": "Cadastro realizado com sucesso"
}
```

> **Observação:** O endpoint `process-signup` é uma solução temporária e pode ser substituído ou atualizado no futuro. O processo de cadastro será totalmente suportado pelo endpoint `store-accounts`.

---

Este documento fornece uma referência detalhada dos endpoints da API disponíveis no sistema POS da Kontapro. Utilize esta referência para integrar e interagir efetivamente com a API.

> **Observação:**  Os códigos de status de resposta da API não estão em conformidade com os padrões, utilizando **true** ou **false**. Os códigos de status de resposta da API serão atualizados para estar em conformidade com os códigos padrão HTTP. Por exemplo, o código **204** indica "Sem conteúdo".
