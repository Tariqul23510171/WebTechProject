# WebTechProject — Sanitized Project Summary

## Project Objective

WebTechProject is a group-developed e-commerce application created for the Web Technologies course at American International University-Bangladesh (AIUB). The project applies server-side web-development concepts through a custom PHP MVC architecture and an integrated MySQL-backed workflow.

The application combines customer account management, catalogue administration, shopping and checkout, order handling, and product reviews in one course project. This summary preserves the academic and technical record without publishing the personal identifiers contained in the original report.

## Academic Context

- **Course:** Web Technologies
- **Institution:** American International University-Bangladesh (AIUB)
- **Project:** Project 04 — E-Commerce Store
- **Development model:** Four assigned modules integrated into a shared application

The original assignment is available as [`P4.pdf`](../P4.pdf).

## Application Architecture

The project uses native PHP and a custom MVC-style structure:

- `Public/index.php` receives requests and dispatches application routes.
- `Controller/` performs form and API request processing, validation, session checks, and Model/View coordination.
- `Model/` contains database connectivity, persistence operations, and application entities.
- `View/` contains customer and administrator templates, forms, CSS, and browser-side JavaScript.
- `config/helpers.php` centralizes URLs, escaping, flash messages, session and role guards, JSON responses, and CSRF helpers.

The code uses both PDO and MySQLi prepared statements. Browser-side interactions use the Fetch API and `XMLHttpRequest` with JSON responses.

## Task Distribution

| Task | Module | Primary assigned contributor |
| --- | --- | --- |
| 1 | Authentication & Profile | Shuvrata Banik Shuvo |
| 2 | Product & Category Management | Tariqul Islam Sesir |
| 3 | Shopping Cart & Checkout | Mahbub Hasnain |
| 4 | Orders & Product Reviews | Toyeb Ali |

The module assignments identify primary responsibility, while integration, debugging, testing, and verification were collaborative activities.

## My Contribution

**Project Leader · Primary Developer for Product & Category Management · Report Writing Lead · Integration & Verification Contributor**

Tariqul Islam Sesir's principal implementation responsibility was Task 2. This work included category hierarchy and CRUD workflows, product catalogue administration, image handling, stock and availability management, validation, MySQL integration, administrator interfaces, and AJAX availability updates.

As project leader, he also coordinated and wrote the project report, supported implementation and error resolution, helped integrate the four modules, and participated in debugging, testing, verification, and final application review. His involvement in Tasks 1, 3, and 4 was implementation support, debugging, integration, and verification rather than primary module ownership.

## Major Functionality

### Authentication and profile

- Registration, login, logout, and role-aware redirects
- Password hashing and verification
- PHP session handling and session regeneration
- Remember-me token support
- Profile, password, and saved shipping-address management

### Product and category administration

- Main and one-level subcategory CRUD
- Parent-child relationship and hierarchy validation
- Duplicate-name and invalid-parent checks
- Protected category deletion when dependent records exist
- Product CRUD, category assignment, price, stock, and availability management
- JPEG/PNG MIME validation and a 3 MB upload limit
- Stored product images and optional replacement during editing
- Low-stock highlighting at five units or fewer
- Protected deletion when order items reference a product
- AJAX availability changes with JSON responses

### Shopping cart and checkout

- Product browsing, keyword search, filters, and details
- Session-based cart operations and stock-aware quantities
- Cart totals and checkout validation
- Saved or new shipping addresses
- Order and order-item creation inside a database transaction
- Stock reduction, cart clearing, and customer-scoped confirmation

### Orders and reviews

- Customer order history and scoped order details
- Administrator status/date filtering
- Controlled order-status transitions through a JSON endpoint
- Delivered-purchase review eligibility
- Rating validation, application-level duplicate prevention, review submission, retrieval, and average ratings

## Database Overview

The application expects a local MySQL database named `ecommerce_store` with the following source-verified tables:

- `users`
- `categories`
- `products`
- `orders`
- `order_items`
- `reviews`

The shopping cart is maintained in the PHP session. The original repository did not include a schema, migration, or seed file, so this documentation does not infer unverified foreign keys or database constraints.

## AJAX Functionality

Dynamic operations include product search and filtering, review retrieval, product availability changes, cart add/update/remove actions, administrator order-status updates, and review submission. The application uses Fetch, `XMLHttpRequest`, and JSON response handling.

## Security and Validation

The submitted source includes prepared queries, password hashing and verification, session authentication, administrator guards, output escaping, request-method checks, image MIME/size validation, transactional checkout, and CSRF checks in several authentication, profile, and checkout workflows.

Coverage is not uniform across every workflow. In particular, Task 2 state changes do not consistently verify CSRF tokens, and some deletion actions use GET requests. These findings are documented rather than silently changing the submitted academic implementation.

## Testing, Integration, and Report Preparation

The completed project required cross-module routing, database-flow checks, interface verification, debugging, and final integration across the four assigned tasks. Tariqul Islam Sesir contributed to those activities and led preparation of the group report, while the repository history and task table preserve the teammates' module ownership.

## Limitations

- Database credentials are hardcoded for a local `root` user with a blank password.
- Environment-specific configuration is not implemented.
- No SQL schema, migration, or seed file was supplied.
- CSRF protection is not consistently applied to Task 2 state changes.
- Some destructive routes use GET requests.
- The remember-me cookie does not explicitly set `Secure`.
- A demonstration credential is visible on the login interface.
- Fresh runtime reproduction was not performed for this documentation update because PHP and MySQL were unavailable and the database schema was not supplied.

## Conclusion

WebTechProject demonstrates the integration of core web-application concerns—authentication, CRUD administration, shopping state, transactional checkout, orders, reviews, AJAX, and relational persistence—within a native PHP course project. It also records the collaborative structure of the work and identifies Product & Category Management as Tariqul Islam Sesir's primary technical contribution.
