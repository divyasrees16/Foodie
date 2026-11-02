# 🍔 Foodie

A full-stack food ordering web application. Customers can browse the menu, search and filter dishes, manage a cart, pay online with PayPal, and track their orders. Admins get a dashboard to manage foods, users, and orders.

Built with **React** on the frontend and **Node.js / Express / MongoDB** on the backend.

---

## ✨ Features

**Customers**
- Browse, search, and filter foods by tag
- Food detail page with star ratings, cook time, and origins
- Shopping cart with quantity updates
- Register, log in, update profile, and change password
- Checkout with delivery address picked on an interactive map (Leaflet)
- Online payment through PayPal
- Order tracking and order history
- Email receipt after payment (Mailgun)

**Admin**
- Dashboard with quick links
- Add, edit, and delete foods (image upload via Cloudinary)
- View, search, edit, and block/unblock users

---

## 🛠 Tech Stack

| Layer     | Technologies |
|-----------|--------------|
| Frontend  | React 18, React Router v6, React Hook Form, Axios, React Toastify, React Leaflet, PayPal React SDK |
| Backend   | Node.js (ES modules), Express, Mongoose, JSON Web Tokens, bcryptjs, Multer |
| Database  | MongoDB |
| Services  | Cloudinary (image uploads), PayPal (payments) |

---

## 📁 Project Structure

```
Foodie/
├── backend/
│   ├── src/
│   │   ├── config/        # Database, Cloudinary, and Mailgun setup
│   │   ├── constants/     # HTTP status codes, order statuses
│   │   ├── helpers/       # Email receipt helper
│   │   ├── middleware/    # Auth and admin guards
│   │   ├── models/        # Mongoose models (User, Food, Order)
│   │   ├── routers/       # API routes (foods, users, orders, upload)
│   │   ├── data.js        # Sample data used to seed the database
│   │   └── server.js      # App entry point
│   └── package.json
└── frontend/
    ├── public/            # Static assets (food images, icons, SVGs)
    ├── src/
    │   ├── components/    # Reusable UI components
    │   ├── hooks/         # useAuth, useCart, useLoading
    │   ├── interceptors/  # Axios auth and loading interceptors
    │   ├── pages/         # Route pages (Home, Cart, Checkout, Admin, ...)
    │   ├── services/      # API service functions
    │   └── AppRoutes.js
    └── package.json
```

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v16 or later
- A MongoDB database (local or [MongoDB Atlas](https://www.mongodb.com/atlas))
- Optional, for full functionality: Cloudinary, Mailgun, and PayPal sandbox accounts

### 1. Clone the repository

```bash
git clone https://github.com/divyasrees16/Foodie.git
cd Foodie
```

### 2. Set up the backend

```bash
cd backend
npm install
```

Create a `.env` file inside `backend/`:

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/foodie
JWT_SECRET=replace_with_a_long_random_string

# Image uploads (admin add/edit food)
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Email receipts
MAILGUN_API_KEY=your_mailgun_api_key
```

Start the server:

```bash
npm run dev     # development, with nodemon
# or
npm start       # production
```

The API runs at `http://localhost:5000`. On first start, the database is automatically seeded with sample foods and users.

### 3. Set up the frontend

Open a second terminal:

```bash
cd frontend
npm install
npm start
```

The app opens at `http://localhost:3000`.

---

## 🔌 API Overview

| Route prefix       | Purpose |
|--------------------|---------|
| `/api/foods`       | List, search, filter by tag, and (admin) create / update / delete foods |
| `/api/users`       | Login, register, update profile, change password, and (admin) manage users |
| `/api/orders`      | Create, pay, track, and list orders |
| `/api/upload`      | Upload images to Cloudinary (admin) |

Protected routes expect a JWT in the request header, issued at login.

---

## 🌐 Frontend Routes

| Path | Page |
|------|------|
| `/` | Home (menu) |
| `/search/:searchTerm`, `/tag/:tag` | Filtered menu |
| `/food/:id` | Food details |
| `/cart` | Cart |
| `/login`, `/register` | Authentication |
| `/checkout`, `/payment` | Checkout and PayPal payment |
| `/track/:orderId` | Order tracking |
| `/profile`, `/orders/:filter?` | Account and order history |
| `/dashboard` | User / admin dashboard |
| `/admin/foods`, `/admin/addFood`, `/admin/editFood/:foodId` | Food management (admin) |
| `/admin/users`, `/admin/editUser/:userId` | User management (admin) |

---

## 📦 Order Statuses

`NEW` → `PAYED` → `SHIPPED`, plus `CANCELED` and `REFUNDED`.

---
