AmazifyAI

AI-Assisted Product Authenticity Verification Platform

AmazifyAI is a web-based product verification platform designed to help sellers submit product information and images for authenticity assessment before listing. The system combines a seller-facing workflow with product verification, status tracking, and a MySQL-backed application.

Project status: The current repository contains the web application and database workflow. The authenticity/ML component is documented only to the extent supported by the current implementation; model architecture, training data, and evaluation metrics will be added as the ML pipeline is integrated and verified.

Overview

Counterfeit products can reduce customer trust and create significant risks for online marketplaces. AmazifyAI explores an automated verification workflow in which sellers provide product details and images, after which the system can assign a verification outcome such as:

Verified

Rejected

Pending

The goal is to make product screening more structured and provide sellers with a clear view of their submissions.

Key Features

🔐 Seller Authentication

Seller sign-up workflow

Seller login workflow

PHP/MySQL-based authentication

📦 Product Submission

Product listing form

Product details submission

Product image upload workflow

🔎 Product Verification

Designed for image-based authenticity assessment

Supports an authenticity/verification score workflow

Verification result can be represented as verified, rejected, or pending

📊 Seller Status Tracking

Seller-specific product status

Visibility into submitted products

Clear verification outcomes

🗄️ Database Integration

MySQL/MariaDB database

SQL schema included in the repository

PHP backend connected through mysqli

Application Flow

Seller
  │
  ├── Sign Up / Login
  │
  ▼
Product Submission
  │
  ├── Product details
  └── Product images
  │
  ▼
Authenticity / Verification Layer
  │
  ▼
Verification Result
  │
  ├── Verified
  ├── Rejected
  └── Pending
  │
  ▼
Seller Dashboard / Status View

Tech Stack

Layer

Technology

Frontend

HTML, CSS, JavaScript

Backend

PHP

Database

MySQL / MariaDB

Local Server

XAMPP / Apache

Database Management

phpMyAdmin

ML / AI

Image-processing based authenticity verification (integration in progress)

Project Structure

AmazifyAI/
│
├── add-product-page/
│   └── Product submission interface
│
├── images/
│   └── Application assets
│
├── sign-up/
│   └── Seller registration interface
│
├── .vscode/
│   └── VS Code project configuration
│
├── Amazify.sql
│   └── Database schema and initial database setup
│
├── config.php
│   └── MySQL database connection
│
├── index.html
│   └── Application entry page
│
├── login.php
│   └── Seller login handling
│
├── login-main.js
│   └── Login-side JavaScript
│
├── login-styles.css
│   └── Login page styling
│
└── README.md
    └── Project documentation

Prerequisites

Before running AmazifyAI locally, install:

XAMPP

A web browser

VS Code (recommended)

Git (if cloning the repository)

The project currently uses PHP and MySQL/MariaDB, so it should be served through Apache rather than opened directly from the filesystem.

Installation & Local Setup

1. Clone the repository

git clone https://github.com/tanisharattan/AmazifyAI.git
cd AmazifyAI

2. Move the project into XAMPP

On Windows, copy the project into:

C:\xampp\htdocs\AmazifyAI

The final structure should look like:

C:\xampp\htdocs\AmazifyAI\

3. Start Apache

Open the XAMPP Control Panel and start:

Apache

4. Configure MySQL/MariaDB

AmazifyAI uses MySQL/MariaDB for storing application data.

If another MySQL installation is already using port 3306, XAMPP MariaDB can be configured to use another available port (for example 3307).

Make sure the database connection settings in config.php match the XAMPP database configuration.

5. Create the database

Open:

http://localhost/phpmyadmin/

Import the SQL file:

Amazify.sql

This creates the database structure required by the application.

If the database name or table names are changed while evolving the project into AmazifyAI, update both the SQL file and config.php consistently.

6. Configure config.php

The application uses PHP's mysqli connection.

Example structure:

<?php

$conn = mysqli_connect("localhost", "root", "", "Amazify");

if (!$conn) {
    die("Database connection failed: " . mysqli_connect_error());
}
?>

If your XAMPP MariaDB is running on port 3307, the connection should include the port:

$conn = mysqli_connect("localhost", "root", "", "Amazify", 3307);

Use the actual database name and credentials configured on your machine.

7. Run the application

Open:

http://localhost/AmazifyAI/

Database

The repository contains:

Amazify.sql

This file is the starting point for the application's database setup.

The database layer is currently implemented using PHP mysqli and a MySQL/MariaDB server.

ML / AI Component

AmazifyAI is intended to use image-based product analysis as part of the authenticity verification workflow.

The planned pipeline is:

Product Images
      │
      ▼
Image Preprocessing
      │
      ▼
Feature Extraction / ML Model
      │
      ▼
Authenticity Score
      │
      ▼
Verification Decision

Important

The current repository documentation should not claim a specific:

model architecture

dataset size

accuracy

F1-score

precision/recall

confidence threshold

until those values are verified from the actual ML implementation and experiments.

These details can be added once the ML pipeline is integrated and evaluated.

Current Development Roadmap

Phase 1 — Web Application

Seller registration interface

Seller login workflow

Product submission interface

Image submission workflow

MySQL/MariaDB integration

Local XAMPP setup

Phase 2 — Verification Pipeline

Connect the image-processing/ML model

Define authenticity score generation

Define verification threshold

Connect model output to product status

Add model inference endpoint/workflow

Phase 3 — Evaluation

Prepare/validate dataset

Train or integrate the selected model

Evaluate accuracy

Evaluate precision, recall and F1-score

Analyze false positives and false negatives

Phase 4 — Product Improvements

Improve seller dashboard

Add verification history

Add admin controls

Improve image upload validation

Add better error handling

Improve UI/UX

Add deployment configuration

Security Considerations

Before production deployment, the application should be hardened with:

Password hashing instead of storing plain-text passwords

Prepared SQL statements

Server-side input validation

File type and file size validation for uploaded images

Secure session handling

CSRF protection where appropriate

Environment-based database credentials

Removal of development credentials from source control

Never commit database passwords, API keys, model credentials, or other secrets to GitHub.

Future Scope

AmazifyAI can be extended into a more complete marketplace trust layer by adding:

Multi-image product analysis

Computer vision-based counterfeit detection

Seller risk scoring

Product verification history

Explainable verification results

Automated admin review queues

Model monitoring and retraining

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