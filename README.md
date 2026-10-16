# 🛒 SmartShop API

SmartShop is a production-ready RESTful Web API built with **.NET 9.0**, **Entity Framework Core 9.0**, and **SQL Server**. It powers the backend of a modern e-commerce platform featuring authentication, role-based authorization, catalog management, real-time stock control, and order processing.

---

## 🚀 Key Features

- **Authentication & Authorization (JWT & RBAC):**
  - User registration and login with password hashing (`SHA-256`).
  - Secure **JSON Web Token (JWT)** generation and validation.
  - **Role-Based Access Control (RBAC):** Granular endpoint authorization separating `User` and `Admin` permissions (`[Authorize(Roles = "Admin")]`).

- **Product Management:**
  - Public endpoints for browsing products and viewing product details.
  - Protected `POST`, `PUT`, and `DELETE` routes restricted exclusively to Administrators.

- **Order Processing & Inventory Control:**
  - Automated stock availability check and inventory reduction upon order creation.
  - Customer order history endpoint (`GET /api/orders/my-orders`).
  - System-wide order management dashboard endpoint for Admins (`GET /api/orders`).

- **Architecture & Performance Optimizations:**
  - **DTO (Data Transfer Object) Pattern:** Prevents circular dependency cycles (`System.Text.Json` object cycle errors) and decouples internal domain entities from public API models.
  - **EF Core Precision Mapping:** Explicit monetary precision configured in `AppDbContext` (`decimal(18,2)`).

---

## 🛠️ Tech Stack

- **Language & Framework:** C# / .NET 9.0 (ASP.NET Core Web API)
- **Database:** SQL Server
- **ORM:** Entity Framework Core 9.0
- **Security:** JWT (JSON Web Tokens), HMAC-SHA256
- **API Documentation:** Swagger / OpenAPI (Swashbuckle UI)

---

## 📂 Project Structure

```text
SmartShop.API/
│
├── Controllers/         # API Controllers (Auth, Products, Orders)
├── Data/                # AppDbContext & EF Core configurations
├── DTOs/                # Data Transfer Objects (Request/Response models)
├── Models/              # Domain Entities (User, Product, Order, OrderItem)
├── Program.cs           # Service registration, Middleware pipeline & JWT setup
└── appsettings.json     # Database Connection Strings & JWT settings
