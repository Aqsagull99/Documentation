# Marketplace Technical Foundation - General E-commerce

## Table of Contents
1. [Introduction](#introduction)
2. [System Architecture](#system-architecture)
3. [API Endpoints](#api-endpoints)
4. [Frontend Pages](#frontend-pages)
5. [Backend Features](#backend-features)
6. [Sanity Schemas](#sanity-schemas)
7. [File Structure and Images](#file-structure-and-images)
8. [Collaboration Notes](#collaboration-notes)
9. [Review and Quality Check](#review-and-quality-check)

---

## Introduction

Welcome to **Hatkhton Day 2**!  
This is a general-purpose **e-commerce marketplace** designed to connect buyers and sellers. It allows users to browse products, place orders, and manage their profiles seamlessly.

**Key Features:**
- Product listing and management
- Order placement and tracking
- Secure and efficient backend integration
- User-friendly frontend interface

---

## System Architecture

Below is the **system architecture** diagram showcasing the flow between different components of the marketplace:

![System Architecture](Documentation/SystemArchitecture_Day2.png)

### **Architecture Components:**
1. **Frontend:** React/Next.js-based UI for product listing, cart, and user interaction.
2. **Backend:** Node.js/Express API to manage data flow and business logic.
3. **Database:** MongoDB/Sanity for storing product and order data.
4. **APIs:** RESTful APIs for communication between frontend and backend.

---

## API Endpoints

### **Product APIs:**
- **GET** `/products`: Fetch all products.
- **POST** `/products`: Add a new product.
- **PUT** `/products/{id}`: Update a product.
- **DELETE** `/products/{id}`: Delete a product.

### **Order APIs:**
- **GET** `/orders`: Fetch all orders.
- **POST** `/orders`: Create a new order.
- **PUT** `/orders/{id}`: Update an order status.
- **DELETE** `/orders/{id}`: Cancel an order.

---

## Frontend Pages

1. **Home Page:** Displays featured products and categories.
2. **Product Page:** Shows product details with options to add to the cart.
3. **Cart Page:** Displays selected items and total cost before checkout.
4. **Checkout Page:** User enters shipping and payment details.
5. **Order History:** Displays the user's past orders.

---

## Backend Features

- **Authentication:** Secure user login and signup.
- **Data Validation:** Ensures all API requests are properly formatted.
- **Error Handling:** Handles invalid requests and server errors gracefully.

---

## Sanity Schemas

### **Product Schema:**
```typescript

export default {
  name: "product",
  title: "Product",
  type: "document",
  fields: [
    { name: "title", type: "string", title: "Title" },
    { name: "price", type: "number", title: "Price" },
    { name: "description", type: "text", title: "Description" },
    { name: "image", type: "image", title: "Image" },
    { name: "category", type: "string", title: "Category" },
  ],
};

Order Schema

export default {
  name: "order",
  title: "Order",
  type: "document",
  fields: [
    { name: "user", type: "string", title: "User" },
    { name: "products", type: "array", of: [{ type: "reference", to: [{ type: "product" }] }], title: "Products" },
    { name: "totalPrice", type: "number", title: "Total Price" },
    { name: "status", type: "string", title: "Status", options: { list: ["Pending", "Shipped", "Delivered"] } },
  ],
};
