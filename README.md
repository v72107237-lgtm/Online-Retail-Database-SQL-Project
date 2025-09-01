# Online-Retail-Database-SQL-Project
This SQL Server project implements a database for a fictional online retail company, showcasing essential SQL skills for entry-level SQL Developer or DBA roles. It includes database creation, schema design, data insertion, advanced queries, triggers, indexes, views, and role-based access control (RBAC) for securit

## Overview
This project implements a database for a fictional online retail company using SQL Server. It demonstrates key SQL skills for an entry-level SQL Developer or SQL DBA role, including:

- Database creation and schema design with primary keys, foreign keys, and constraints.
- Data insertion with sample records.
- Advanced queries using joins, aggregations, subqueries, CTEs, and window functions (e.g., ROW_NUMBER).
- Triggers for auditing INSERT, UPDATE, and DELETE operations on key tables (Products and Customers).
- Indexes (clustered and non-clustered) for query performance optimization.
- Views for simplified data access and reporting.
- Security implementation with logins, users, roles, permissions, and RBAC scenarios.

The database tracks customers, products, categories, orders, and order items. It includes logging for changes, performance tuning via indexes, and role-based access control for security.

This project is ideal for showcasing foundational SQL knowledge in database management, querying, optimization, and security—perfect for roles requiring 0 years of experience.

## Prerequisites
- SQL Server (e.g., Microsoft SQL Server Management Studio - SSMS) or Azure SQL Database.
- Basic familiarity with SQL scripting.
- Run the script in a new query window to create and populate the database.

## Installation/Setup
1. Open SSMS and connect to your SQL Server instance.
2. Create a new query and paste the entire SQL script from the project file (e.g., OnlineRetailDB.sql).
3. Execute the script step-by-step or in full. It will:
   - Create the OnlineRetailDB database.
   - Create tables with constraints.
   - Insert sample data.
   - Define triggers, indexes, views, and security roles.
4. The database is now ready. Note: Some operations (e.g., security logins) require sysadmin privileges. Adjust as needed for your environment.

If running in an existing database, remove the CREATE DATABASE statement. For security sections, ensure you have permissions to create logins and roles.

## Database Schema
The database includes 6 main tables plus a logging table. Relationships are enforced with foreign keys.


### Table Descriptions
- *Customers*: Customer details (e.g., name, contact, address).
- *Products*: Product info (name, price, stock) linked to categories.
- *Categories*: Product categories (e.g., Electronics, Clothing).
- *Orders*: Order headers (date, total amount) linked to customers.
- *OrderItems*: Line items in orders (quantity, price) linked to orders and products.
- *ChangeLog*: Audit log for changes (INSERT/UPDATE/DELETE) on Products and Customers via triggers.

## Key Features

### Triggers
Triggers log changes to ChangeLog for auditing:
- Products: trg_Insert_Product, trg_Update_Product, trg_Delete_Product.
- Customers: trg_Insert_Customers, trg_Update_Customers, trg_Delete_Customers.

Example: Inserting a product logs an 'INSERT' entry with user and timestamp.

### Indexes
- Clustered: On primary keys (e.g., IDX_Products_ProductID).
- Non-clustered: On foreign keys and frequent query columns (e.g., IDX_Products_CategoryID, IDX_Orders_OrderDate).

These optimize queries like filtering by category or date.

### Views
- vw_ProductDetails: Products with category names.
- vw_CustomerOrders: Customer order summaries (total orders, amount).
- vw_RecentOrders: Recent orders with customer details and amounts.

Views simplify complex joins for reporting.

### Queries
The script includes 44+ queries demonstrating:
- Retrieval (e.g., customer orders, out-of-stock products).
- Aggregations (e.g., total sales per product/category, average order value).
- Advanced: Subqueries (e.g., highest-priced product per category), CTEs/Window functions (e.g., top customers by spending), date-based filters (e.g., last 30 days).
- Joins: Multi-table reports (e.g., orders with product details).

### Security (RBAC)
- Logins/Users: e.g., SalesUser.
- Roles: e.g., SalesRole, ProductManagerRole (20 scenarios covered).
- Permissions: GRANT/REVOKE/DENY for SELECT/INSERT/UPDATE/DELETE on tables/views.
- Examples: Read-only roles, column-level access, application roles.

This shows understanding of security best practices.

## Sample Data and Insights
- 3 categories, 8+ products, 5+ customers, 3+ orders.
- Sample queries output: e.g., Total sales per product, most popular category (by quantity sold).
- Logging: Tracks changes with user info for compliance/auditing.

Run SELECT * FROM ChangeLog; after modifications to see audit trails.

This project is open-source; fork and modify for learning!
