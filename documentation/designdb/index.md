# ERD Documentation Structure

## 1. Online Game Voucher Database Schema
This database is designed to support the core functions of an online game voucher platform, including product, user, order, shopping cart and wishlist management.
The goal is to provide an efficient and scalable data structure that can support the various features required by users and administrators.

## 2. Diagram ERD
```mermaid

erDiagram
    USERS {
        int id PK
        varchar username UNIQUE NOT NULL
        varchar email UNIQUE NOT NULL
        varchar password NOT NULL
        enum role "admin, buyer" NOT NULL
        datetime created_at
    }

    PRODUCTS {
        int id PK
        varchar name NOT NULL
        text description NOT NULL
        decimal price NOT NULL
        decimal discount NOT NULL
        int stock
        int device_id FK
        string images
        int seller_id FK
        string product_key
        datetime created_at
    }

    DEVICE {
        int id PK
        string name
        string version
    }

    CARTS {
        int id PK
        int user_id FK
        datetime created_at
    }

    PRODUCT_TAGS {
        int id PK
        int product_id FK
        int tag_id FK
        datetime created_at
    }

    TAGS {
        int id PK
        varchar name
        datetime created_at
    }

    CART_ITEMS {
        int id PK
        int cart_id FK
        int product_id FK
        int quantity
        datetime created_at
    }

    WISHLISTS {
        int id PK
        int user_id FK
        datetime created_at
    }

    WISHLIST_ITEMS {
        int id PK
        int wishlist_id FK
        int product_id FK
        datetime created_at
    }

    ORDERS {
        int id PK
        int user_id FK
        decimal total_price
        varchar status
        datetime created_at
    }

    ORDER_ITEMS {
        int id PK
        int order_id FK
        int product_id FK
        int quantity
        decimal price
        datetime created_at
    }

    PROFILES {
        int id PK
        int user_id FK
        text address
        varchar phone
        datetime created_at
    }

    PAYMENTS {
        int id PK
        string name
    }

    USERS ||--o{ PROFILES : "has"
    USERS ||--o{ CARTS : "has"
    USERS ||--o{ WISHLISTS : "has"
    USERS ||--o{ ORDERS : "places"
    PROFILES }o--|| USERS : "belongs to"
    CARTS }o--|| USERS : "belongs to"
    WISHLISTS }o--|| USERS : "belongs to"
    WISHLIST_ITEMS }o--|| WISHLISTS : "contains"
    WISHLIST_ITEMS }o--|| PRODUCTS : "contains"
    PRODUCTS }o--|| DEVICE : "supports"
    PRODUCTS }o--|| USERS : "sold by"
    PRODUCT_TAGS }o--|| PRODUCTS : "tags"
    PRODUCT_TAGS }o--|| TAGS : "categorized as"
    CART_ITEMS }o--|| CARTS : "contains"
    CART_ITEMS }o--|| PRODUCTS : "contains"
    ORDERS }o--|| USERS : "belongs to"
    ORDER_ITEMS }o--|| ORDERS : "contains"
    ORDER_ITEMS }o--|| PRODUCTS : "contains"
    PAYMENTS ||--o{ ORDERS : "pays for"
```

## 3. Entity Explanation
- **TABLE_NAME**: Description of the entity and its attributes.

## 4. Relation
- **Relationships between entities**: Description of the relation and cardinality.

## 5. Additional Notes
Additional relevant information.


