# Laravel E-commerce Example

![Laravel E-commerce Example](https://user-images.githubusercontent.com/4316355/36414878-d41987b2-15f1-11e8-9f2c-6c3a68e4a14b.gif)

A full-featured e-commerce application built with Laravel, featuring Stripe integration, shopping cart functionality, and an admin dashboard.

## Demo

- **Live Demo**: [https://laravelecommerceexample.ca](https://laravelecommerceexample.ca)
- **Video Tutorial Series**: [Watch on YouTube](https://www.youtube.com/watch?v=o5PWIuDTgxg&list=PLEhEHUEU3x5oPTli631ZX9cxl6cU_sDaR)

*Note: The demo site has limited permissions. For full access, please install locally.*

## Prerequisites

- PHP >= 7.4
- Composer
- Node.js & NPM
- MySQL/PostgreSQL
- Stripe Account
- Algolia Account (for search functionality)
- Braintree Account (optional, for PayPal integration)

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/laravel-ecommerce-example.git
    cd laravel-ecommerce-example
    ```

2. Install dependencies:
    ```bash
    composer install
    npm install
    ```

3. Configure environment:
    ```bash
    cp .env.example .env
    php artisan key:generate
    ```

4. Configure the following in your `.env` file:
    - Database credentials
    - `STRIPE_KEY` and `STRIPE_SECRET`
    - `ALGOLIA_APP_ID` and `ALGOLIA_SECRET`
    - `BT_MERCHANT_ID`, `BT_PUBLIC_KEY`, `BT_PRIVATE_KEY` (for PayPal)
    - `APP_URL`
    - `ADMIN_PASSWORD` (defaults to 'password' if not set)

5. Set up the application:
    ```bash
    php artisan ecommerce:install
    npm run dev
    ```

6. Start the development server:
    ```bash
    php artisan serve
    ```

7. Visit `http://localhost:8000` in your browser

## Admin Access

Access the Voyager admin backend at `/admin` with these credentials:
- Admin: `admin@admin.com` / `password`
- Web Admin: `adminweb@adminweb.com` / `password`

## Technical Details

### Shopping Cart Implementation

We utilize [hardevine/LaravelShoppingcart](https://github.com/hardevine/LaravelShoppingcart), a maintained fork of the original Crinsane package, chosen for its consistent updates and Laravel version compatibility.

### Windows Compatibility

For Windows users, replace the `money_format()` function (which is not supported on Windows) with the following modifications:

1. In `app/helpers.php`:
    ```php
    return '$'.number_format($price / 100, 2);
    ```

2. In `app/Product.php`:
    ```php
    return '$'.number_format($this->price / 100, 2);
    ```

3. In `config/cart.php`:
    - Set `thousand_seperator` to an empty string to prevent numeric value errors

## Development

### Starting from a Specific Commit

To begin from a particular point in the development:

1. Clone the repository
2. Checkout the desired commit:
    ```bash
    git checkout <commit-hash>
    ```
3. Follow the standard installation steps, but replace `php artisan ecommerce:install` with:
    ```bash
    php artisan migrate --seed
    ```

## Contributing

Please read our contributing guidelines before submitting pull requests.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
