# WebTechProject — PHP MVC E-Commerce Application

## Overview

WebTechProject is a group-built e-commerce application developed for the **Web Technologies** course at **American International University-Bangladesh (AIUB)**. It demonstrates a custom native PHP MVC architecture, MySQL persistence, server-rendered interfaces, session-based workflows, and JSON-backed AJAX interactions.

The application covers account management, catalogue administration, shopping and checkout, order management, and product reviews. It is presented as an academic implementation rather than a production-ready commerce platform.

## Academic Context

- **Course:** Web Technologies
- **Institution:** American International University-Bangladesh (AIUB)
- **Project type:** Group course project
- **Application domain:** E-commerce

## Course Project Specification

The original six-page assignment is preserved as the [Course Project Specification](P4.pdf). It defines the shared four-task application scope, database entities, validation requirements, and expected AJAX endpoints.

## Application Architecture

The project uses a custom MVC-style organization without Laravel or another PHP framework.

```text
WebTechProject/
├── config/
│   └── helpers.php
├── Controller/
├── Model/
├── Public/
│   ├── index.php
│   └── uploads/products/
├── View/
└── P4.pdf
```

- **`Public/index.php`** is the front controller and route dispatcher.
- **`Controller/`** handles requests, form processing, validation, authentication checks, API endpoints, and Model/View coordination.
- **`Model/`** contains database access, application entities, persistence logic, and supporting data operations.
- **`View/`** contains PHP templates, customer and administrator interfaces, forms, styling, and browser-side JavaScript.
- **`config/helpers.php`** provides URL helpers, output escaping, flash messages, session and administrator guards, JSON responses, and CSRF helpers.

## Core Features

### Task 1 — Authentication & Profile

**Primary assigned contributor:** Shuvrata Banik Shuvo

- Registration, login, and logout
- Password hashing and verification
- Session regeneration, authentication guards, and role-based redirects
- Remember-me token handling
- Profile, password, and shipping-address management
- Server-side validation and CSRF checks in the implemented authentication/profile workflows

My involvement in this team module focused on implementation support, debugging, integration, and verification.

### Task 2 — Product & Category Management

**Primary implementation:** Tariqul Islam Sesir

- Main-category and one-level subcategory management
- Product catalogue administration
- Category hierarchy and product validation
- Product images, stock, pricing, and availability
- Administrator dashboard, lists, and forms
- Low-stock visibility and AJAX availability updates

This module was my principal technical responsibility and is described in more detail below.

### Task 3 — Shopping Cart & Checkout

**Primary assigned contributor:** Mahbub Hasnain

- Product browsing, keyword search, category filtering, and product details
- Session-based cart with add, update, and remove operations
- Stock-aware quantity validation and calculated totals
- Saved or new shipping-address selection
- Payment-field validation
- Transactional order and order-item creation
- Stock reduction, cart clearing, and confirmation ownership checks

My involvement in this team module focused on implementation support, debugging, integration, and verification.

### Task 4 — Orders & Product Reviews

**Primary assigned contributor:** Toyeb Ali

- Customer order history and user-scoped order details
- Administrator order management with status and date filters
- JSON order-status updates and controlled status transitions
- Review eligibility for delivered purchases
- Rating validation from 1 to 5 and duplicate-review prevention
- Review submission and retrieval with average product ratings

My involvement in this team module focused on implementation support, debugging, integration, and final verification.

## My Role & Contribution

**Project Leader · Primary Developer for Product & Category Management · Report Writing Lead · Integration & Verification Contributor**

My primary implementation responsibility was **Task 2: Product & Category Management**, covering the administrative product catalogue, category hierarchy, product/category CRUD, image handling, stock and availability management, validation, database integration, and administrator workflows. As project leader, I also supported my teammates with implementation issues, debugging, cross-module integration, and verification across Tasks 1, 3, and 4, and I led preparation of the project report.

## Product & Category Management — Primary Contribution

### Category management

- Create, list, edit, and delete main categories and one-level subcategories
- Maintain parent-child relationships through the category forms
- Reject invalid parents, self-parenting, and unsupported hierarchy depth
- Check duplicate category names within the applicable hierarchy
- Prevent deletion when a category still has child categories or assigned products

### Product management

- Create, list, edit, and delete products
- Assign products to validated categories
- Manage descriptions, prices, stock quantities, and availability
- Prevent deletion when existing order items reference the product
- Display average ratings alongside catalogue-management information

### Administrator and inventory features

- Dedicated dashboard, category lists/forms, and product lists/forms
- Stock visibility with low-stock highlighting at **5 units or fewer**
- Availability updates through a JSON-returning AJAX endpoint
- Server-side validation for numeric price, non-negative integer stock, category selection, and availability values

### Image handling

- JPEG and PNG MIME validation using server-side file inspection
- Maximum upload size of 3 MB
- Generated filenames and server-side storage under `Public/uploads/products/`
- Optional image replacement during product editing

### Database integration

Task 2 uses MySQLi prepared statements for category and product persistence. Queries cover hierarchy inspection, duplicate checks, CRUD operations, product-reference checks, stock reporting, availability changes, and average-rating aggregation. Database constraints not represented in a supplied schema are not assumed here.

## Database

The submitted application uses the MySQL database name `ecommerce_store` and references these verified tables:

| Table | Purpose |
| --- | --- |
| `users` | Accounts, roles, credentials, contact fields, and saved addresses |
| `categories` | Main categories and one-level parent relationships |
| `products` | Catalogue content, prices, stock, images, and availability |
| `orders` | Customer, shipping, payment, total, status, and date information |
| `order_items` | Products, quantities, and unit prices associated with orders |
| `reviews` | Customer ratings and review text for products |

The cart is stored in the PHP session; there is no cart table. No SQL schema, migration, or seed file was included in the submitted repository, so this portfolio does not invent database definitions that cannot be verified from the source material.

## AJAX & Dynamic Interactions

The application uses the Fetch API, `XMLHttpRequest`, and JSON responses for:

- Product search and category filtering
- Product-review retrieval
- Product availability updates
- Cart add, update, and remove operations
- Administrator order-status updates
- Product-review submission

## Validation & Security

Source-verified controls include prepared PDO/MySQLi queries, `password_hash`, `password_verify`, PHP session authentication, administrator authorization, output escaping, request-method checks, upload MIME/size validation, transactional checkout, and CSRF protection in several authentication, profile, and checkout workflows.

These controls describe the submitted implementation; they are not a claim that the application has undergone a production security review.

## Technologies

- PHP 8-compatible syntax and native sessions
- MySQL, PDO, and MySQLi
- HTML and CSS
- JavaScript, Fetch API, and `XMLHttpRequest`
- JSON APIs
- Custom MVC architecture
- Prepared statements, password hashing, and image-upload handling

## Installation

The following local environment is expected:

- PHP 8.0 or later
- MySQL or MariaDB
- PHP extensions for PDO MySQL, MySQLi, and Fileinfo
- A local web server, or PHP's built-in development server

Clone the repository:

```bash
git clone https://github.com/Tariqul23510171/WebTechProject.git
cd WebTechProject
```

## Database Setup

Create a local MySQL database named `ecommerce_store` and provide the six tables described in the [Database](#database) section. The submitted source assumes a local `root` user with a blank password in the model classes.

Because the original submission does not contain SQL schema or seed files, exact database recreation cannot be guaranteed from this repository alone. The expected fields and relationships are documented in [P4.pdf](P4.pdf).

## Running Locally

From the repository root, a PHP development server can be started with:

```bash
php -S 127.0.0.1:8000 -t Public
```

Then open:

```text
http://127.0.0.1:8000/index.php
```

Runtime reproduction was not performed during the portfolio documentation update because PHP and MySQL were unavailable locally and the original SQL schema was not supplied.

## Limitations & Future Hardening

- Local database credentials are hardcoded and assume `root` with a blank password.
- No `.env` or environment-specific configuration layer is included.
- No SQL schema, migration, or seed data is included.
- Task 2 state-changing actions do not consistently verify CSRF tokens.
- Some destructive actions use GET requests.
- The remember-me cookie does not explicitly set the `Secure` attribute.
- A demonstration credential is displayed in the login view.
- Production deployment and security hardening were outside the course-project scope.

## Documentation

- [Sanitized Project Summary](docs/project_summary.md)
- [Course Project Specification](P4.pdf)

The original project report and code-printout PDF are intentionally excluded because they contain personal information and duplicate material already represented by the application source and sanitized summary.

## Team Contributions

| Task | Module | Primary assigned contributor | Tariqul Islam Sesir's involvement |
| --- | --- | --- | --- |
| 1 | Authentication & Profile | Shuvrata Banik Shuvo | Implementation support, debugging, integration, and verification |
| 2 | Product & Category Management | Tariqul Islam Sesir | Primary implementation responsibility |
| 3 | Shopping Cart & Checkout | Mahbub Hasnain | Implementation support, debugging, integration, and verification |
| 4 | Orders & Product Reviews | Toyeb Ali | Implementation support, debugging, integration, and final verification |

This was a group project. The role descriptions acknowledge primary module ownership while also reflecting the shared debugging, integration, testing, and verification required to produce the final application.

## Historical Team Repository

The [team repository maintained by Toyeb Ali](https://github.com/ToyebAli/WebTechProject) preserves the shared collaboration context. Both repositories contained the same final application tree when this portfolio documentation was prepared; this repository does not replace or erase teammate contributions.
