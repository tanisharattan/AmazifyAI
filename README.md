# AmazifyAI

A web-based platform for helping sellers verify product authenticity before listing items online.

<p align="center">
  <img src="https://img.shields.io/badge/PHP-8.2-777BB4?style=for-the-badge&logo=php" alt="PHP 8.2" />
  <img src="https://img.shields.io/badge/MySQL-MariaDB-4479A1?style=for-the-badge&logo=mysql" alt="MySQL / MariaDB" />
  <img src="https://img.shields.io/badge/Stack-PHP%20%2B%20MySQL-000000?style=for-the-badge" alt="PHP + MySQL" />
</p>

AmazifyAI is built to streamline the product verification workflow for sellers. Sellers can sign up, log in, submit product details and images, and track verification outcomes such as Verified, Rejected, or Pending. The project combines a PHP + MySQL backend with a simple frontend interface to create a complete product authenticity review flow.

## Overview

Counterfeit and low-quality products can damage trust in digital marketplaces. AmazifyAI explores an automated verification workflow where sellers submit product information and product images, and the system evaluates whether the listing is authentic or requires review.

The current implementation focuses on the seller workflow, product submission, status tracking, and database-backed storage. The AI/ML verification layer is planned as part of future integration work.

## Features

- Seller authentication with sign-up and login flow
- Product submission form with title, price, description, and image upload handling
- Product status tracking for each submission
- Verification result states: Verified, Rejected, and Pending
- MySQL database integration using PHP mysqli
- Simple web-based user interface for local deployment

## Workflow

```text
Seller
  ↓
Sign Up / Login
  ↓
Submit Product Details
  ↓
Upload Product Images
  ↓
Authenticity Verification Layer
  ↓
Verification Result
  ├── Verified
  ├── Rejected
  └── Pending
  ↓
Seller Dashboard / Product Status View
```

## Tech Stack

| Layer | Technology |
| --- | --- |
| Frontend | HTML, CSS, JavaScript |
| Backend | PHP |
| Database | MySQL / MariaDB |
| Local Server | XAMPP / Apache |
| Database Management | phpMyAdmin |
| AI / ML | Image-based authenticity verification (integration in progress) |

## Project Structure

```text
AmazifyAI/
├── add-product-page/
│   └── Product submission interface
├── images/
│   └── Static application assets
├── sign-up/
│   └── Seller registration interface
├── .vscode/
│   └── VS Code configuration
├── Amazify.sql
│   └── Database schema and seed data
├── config.php
│   └── Database connection configuration
├── index.html
│   └── Main app entry page
├── login.php
│   └── Seller login logic
├── login-main.js
│   └── Frontend login behavior
├── login-styles.css
│   └── Login page styling
├── README.md
│   └── Project documentation
└── .git/
    └── Repository metadata
```

## Prerequisites

Before running the project locally, make sure you have:

- XAMPP installed
- A browser such as Chrome or Edge
- VS Code (recommended)
- Git (optional, if cloning the repo)

This project uses PHP and MySQL/MariaDB, so it should be run through a local Apache server instead of opening files directly in a browser.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/tanisharattan/AmazifyAI.git
cd AmazifyAI
```

### 2. Place the project in your local web server

For Windows with XAMPP, place the project in:

```text
C:\xampp\htdocs\AmazifyAI
```

### 3. Start Apache and MySQL

Open the XAMPP Control Panel and start:

- Apache
- MySQL

### 4. Import the database

Open:

```text
http://localhost/phpmyadmin/
```

Then import:

```text
Amazify.sql
```

This creates the required `users` and `products` tables for the app.

### 5. Configure the database connection

Update the connection settings in `config.php` to match your local MySQL configuration.

Example:

```php
<?php
$conn = mysqli_connect("localhost", "root", "", "Amazify");

if (!$conn) {
    die("Database connection failed: " . mysqli_connect_error());
}
?>
```

If your MySQL is configured on a custom port (for example `3307`), use:

```php
<?php
$conn = mysqli_connect("localhost", "root", "", "Amazify", 3307);
?>
```

### 6. Run the application

Open the browser and visit:

```text
http://localhost/AmazifyAI/
```

## Database

The project currently uses a MySQL/MariaDB database defined by `Amazify.sql`.

### Included tables

- `users` — stores seller account information
- `products` — stores product submissions and verification-related fields

The database connection is handled using PHP's `mysqli` extension.

## Current Status

This repository contains the working web application and database layer. The AI-assisted authenticity verification component is currently planned and not yet fully integrated into the codebase.

## License

This project is currently distributed without a formal license file. Please check with the repository owner before using or distributing the code in production environments.

## Contact

For questions or collaboration opportunities, reach out through the repository owner or project maintainer.

## Roadmap

### Phase 1: Web application foundation
- Complete seller registration and login flow
- Improve product submission and image upload handling
- Finalize database schema and validation rules

### Phase 2: Verification pipeline
- Integrate AI or image-analysis-based authenticity checks
- Define verification score and decision thresholds
- Connect model output to product status updates

### Phase 3: Product experience improvements
- Improve seller dashboard usability
- Add verification history and review logs
- Strengthen error handling and validation

### Phase 4: Production readiness
- Add secure session and authentication hardening
- Validate uploads and protect against common web vulnerabilities
- Prepare deployment configuration for a production environment

## Security Notes

Before production deployment, the application should be hardened with:

- Password hashing for user credentials
- Prepared SQL statements to prevent injection attacks
- Server-side validation for all form inputs
- Image upload restrictions for file type and size
- Proper session management and CSRF protection
- Environment-based configuration for database credentials

Never commit database passwords, API keys, or other secrets to GitHub.

Confidence-based manual review

API-based integration with marketplace listing workflows

Project Identity

Project: AmazifyAI
Focus: Product authenticity verification
Application Type: Web application + ML verification workflow
Backend: PHP
Database: MySQL/MariaDB
Local Environment: XAMPP

License & Attribution

This repository is being developed as AmazifyAI.

The current codebase originated from an existing Amazify project and is being adapted, documented, and extended under this new project. Any original licenses, notices, or attribution requirements present in the source repository should be retained unless their terms clearly permit removal.

As the project is modified and new components are developed, this README will be updated to document those contributions accurately.