# GameVoucher

GameVoucher is a platform designed for easy and reliable purchase of game vouchers, in-game credits, and managing transactions. The platform supports a variety of games and ensures secure payment integration for a smooth experience.

## Features

- **User Authentication**: Register, login, and manage profiles securely.
- **Product Management**: Admins can create, edit, and delete products, while users can browse and view product details.
- **Cart & Wishlist Management**: Users can add items to their cart or wishlist for future purchases.
- **Order Management**: Handle the lifecycle of user orders, from placement to tracking and completion.
- **Payment Processing**: Secure and reliable payment options, with real-time tracking and invoice generation.
- **Tag & Genre Management**: Organize products with tags and allow users to filter based on these tags.
- **Order Item Management**: Manage details of each item within an order, ensuring accurate tracking.
- **Device Compatibility Management**: Ensure products are correctly categorized by compatible devices.

## Tech Stack

### Backend
- **Laravel** - Backend built with Laravel to handle logic and manage databases efficiently.
- **Laragon** - Relational database for storing user data, product information, and orders.

### Frontend
- **React** - A powerful JavaScript library for creating dynamic user interfaces.
- **Tailwind CSS** - Utility-first CSS framework for styling the frontend.
- **Inertia.js** - Bridges the backend and frontend by rendering views server-side using React.

### Other Tools
- **ESLint** - Code quality and linting tool to maintain consistency.
- **Prettier** - Code formatting tool to ensure clean code style.
- **Nginx** - Serves the frontend and backend in production as a reverse proxy.

## Prerequisites

Make sure you have the following installed:
- [PHP](https://www.php.net/)
- [Composer](https://getcomposer.org/)
- [Node.js](https://nodejs.org/)
- [Yarn](https://yarnpkg.com/)

## Installation

1. Clone the repository:
    ```bash
    git clone "https://github.com/orgs/YourRepo/gamevoucher"
    ```

2. Navigate to the project directory:
    ```bash
    cd gamevoucher
    ```

3. Install the backend dependencies:
    ```bash
    composer install
    ```

4. Install the frontend dependencies:
    ```bash
    yarn install
    ```

5. Set up the environment:
    - Copy `.env.example` to `.env`:
        ```bash
        cp .env.example .env
        ```
    - Update `.env` with your database credentials and other required environment variables.

6. Run database migrations:
    ```bash
    php artisan migrate
    ```

7. Start the local development server:
    ```bash
    php artisan serve
    yarn dev
    ```
   Open [http://localhost:8000](http://localhost:8000) for the backend and [http://localhost:3000](http://localhost:3000) for the frontend in your browser.

## Directory Structure

```plaintext
GAMEVOUCHER/
│
├── dosumentation/              # Detail documentation (API,architecture,backlog,etc)
├── backend/                    # Backend Laravel project
├── frontend/                   # Frontend React project
│   ├── assets/                 # Static assets like images, fonts, etc.
│   ├── components/             # Reusable React components
│   ├── pages/                  # Page components for routing
│   ├── services/               # API service functions
│   └── App.js                  # Main React application entry point                
└── README.md                   # This documentation
