# Project Architecture Documentation

## 1.Introduction

   1. **Purpose:**

   - Provide an overview of the system's architecture, including the components, their interactions, and how they are structured.

   2. **Technologies Used:**

   - Laravel v11.x
   - MySQL
   - Tailwind CSS
   - Blade Templates

### 2.System Overview

   1. **Core Components:**

      - **Frontend:**

      - Blade templates with Tailwind CSS for UI/UX.

      - **Backend:**

      - Laravel 11 framework handling business logic, routing.

      - **Database:**

      - MySQL for storing and managing data, including user information, orders, and transactions.

      - **Authentication:**

      - Laravel's built-in authentication system for user management (Breeze), including registration, login.

## 3.Database Architecture

   1. **ERD (Entity-Relationship Diagram):**

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

   2. **Database Migrations:**

      - Overview of migration files for creating and modifying database tables, including fields, indexes, and relationships.

## 4.Directory Structure

   1. **App Directory:**

      - **Models:**

      - Eloquent models representing database entities such as `User`, `Order`, `Product`, etc.

      - **Controllers:**

      - Handle HTTP requests, coordinate between models and views, and execute business logic.

      - **Services:**
      - Contain reusable business logic and helper functions.

   2. **Routes Directory:**

      - **web.php:**

      - Defines routes for the web application, mapping URLs to controllers.

   3. **Resources Directory:**

      - **Views:**

      - Blade templates for rendering HTML with Tailwind CSS styling.

      - **Assets:**
      - Contains CSS, JS, and image files used in the frontend.

   4. **Config Directory:**

      - **Configuration Files:**
      - Contains settings for services such as database connections, caching, and mail.

## 5.Application Flow

   1. **User Registration and Login:**

      - Describes the flow for user authentication, including registration, login, and account management.

   2. **Order Process:**

      - Explains how users browse products, add items to the cart, place orders, and complete payments.

   3. **Invoice Generation:**

      - Details the process of generating and delivering invoices to users after a successful order, including the format and access points.

## 6.Security Considerations

   1. **Data Protection:**

      - Uses Laravel’s built-in encryption and hashing mechanisms for protecting sensitive data.

   2. **Input Validation:**

      - Server-side validation to prevent common security issues such as XSS, SQL injection, and CSRF attacks.

   3. **Authentication & Authorization:**

      - Middleware and policies used to protect routes and manage user roles and permissions.

## 7.Testing

   1. **Unit Testing:**

      - Overview of unit tests for models, controllers, and services.

   2. **Feature Testing:**

      - End-to-end testing for key features like user registration, login, and order processing.

## 8.Deployment

   1. **Environment Configuration:**

      - Instructions on setting up the `.env` file for different environments (local, staging, production).

   2. **Server Requirements:**

      - Lists necessary server configurations such as PHP version, required PHP extensions, web server (Nginx/Apache), and MySQL setup.

   3. **Deployment Workflow:**

      - Step-by-step guide on deploying the application, running migrations, and seeding the database.


## 9.Documentation & Code Quality

   1. **Coding Standards:**

      - Following PSR-12 for PHP coding standards.

   2. **Code Review:**
      - Guidelines for peer reviews and code quality checks.

## 10.Future Enhancements

   1. **Scalability Considerations:**

      - Ideas for optimizing the application for higher traffic and larger datasets.

   2. **Feature Additions:**

      - Potential new features or improvements for future releases.
