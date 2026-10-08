# AutoParts Pro - Vehicle Spare Parts and Services Management System

A full-stack MERN web application developed for the **IT2150 IT Project** at SLIIT. The system brings spare-parts browsing, product administration, orders, supplier management, inventory, services, bookings, reviews, and warranty workflows into one platform.

**Project ID:** ITP-IT-25  
**Project type:** University group project  
**Repository:** [ITP-Web_Application-Y2S2](https://github.com/Kithsara-01/ITP-Web_Application-Y2S2)

## Overview

Manual spare-parts and service operations make it difficult to maintain product information, check availability, track stock, and manage customer requests. AutoParts Pro provides a React web interface connected to an Express REST API and MongoDB database.

## My Contribution

**Deshan S.M.K - Spare Parts / Product Management**

Handled the complete Spare Parts / Product Management module across both the React frontend and the Node.js, Express, and MongoDB backend. Developed the module's user interfaces and REST APIs, connected the frontend to the backend using Axios, and implemented product-image upload and catalogue management functionality.

My contribution covers my assigned module. Overall system structure and final project integration were handled by other team members.

### Product Management Highlights

- Product creation, viewing, editing, and removal.
- Product image upload and display.
- Search, filtering, and sorting of the product catalogue.
- Product categorization and vehicle-related information.
- Product price and discount information.
- Top-rated product listings.
- Administrative routes for availability changes, removed-product retrieval, and restoration.

## System Modules

| Module | Purpose |
| --- | --- |
| Accounts | Registration, login, profile management, and JWT authentication |
| Products | Customer catalogue and administrative product management |
| Orders and Delivery | Cart/checkout interfaces, order history, and order-management workflows |
| Suppliers | Supplier records and related management operations |
| Inventory | Stock records and inventory workflows |
| Services and Bookings | Service browsing and appointment management |
| Reviews and Warranty | Customer feedback and warranty requests |
| Additional Features | Wishlist, notification routes, payment integration, and invoice-generation utilities |

## Technology Stack

| Layer | Technologies |
| --- | --- |
| Frontend | React 18, Vite 5, React Router 6, Tailwind CSS 3 |
| Client utilities | Axios, React Icons, React Hot Toast |
| Backend | Node.js, Express 4 |
| Database | MongoDB, Mongoose 8 |
| Authentication | JSON Web Tokens, bcryptjs |
| Backend utilities | Multer, express-validator, Nodemailer, PDFKit |
| Development | npm, nodemon |

## Architecture and Source Layout

The React frontend communicates with the Express backend through Axios and REST APIs. The backend uses Mongoose models to access MongoDB and serves uploaded files through `/uploads`.

| Path | Contents |
| --- | --- |
| `frontend/src/pages/` | Customer and administrative pages |
| `frontend/src/components/` | Shared UI and route components |
| `frontend/src/context/` | Shared application state |
| `frontend/src/services/api.js` | Axios client and JWT request handling |
| `frontend/vite.config.js` | Development server and API/upload proxies |
| `backend/server.js` | Express application and route registration |
| `backend/controllers/` | Module request-handling logic |
| `backend/models/` | MongoDB/Mongoose data models |
| `backend/routes/` | REST API definitions |
| `backend/middleware/` | Authentication, authorization, and uploads |
| `backend/config/db.js` | Database connection logic |
| `backend/utils/invoiceGenerator.js` | Invoice generation |

## Local Setup

### Prerequisites

- Node.js 18 or newer, with npm.
- MongoDB locally or through MongoDB Atlas.
- A browser.
- Your own payment-provider configuration when demonstrating payments.

### 1. Backend configuration

Create `backend/.env` locally:

```dotenv
PORT=5001
MONGODB_URI=mongodb://127.0.0.1:27017/autoparts_demo
JWT_SECRET=replace_with_a_long_random_secret
```

For Atlas, replace `MONGODB_URI` with your own database connection string. Do not commit credentials.

**Port alignment matters:** the existing Vite configuration proxies `/api` and `/uploads` to `http://localhost:5001`. Use `PORT=5001` as above. The backend otherwise defaults to port `5000`.

Run in a terminal at the repository root:

```bash
cd backend
npm ci
npm run dev
```

For normal startup, use `npm start`.

### 2. Frontend startup

Open a second terminal at the repository root:

```bash
cd frontend
npm ci
npm run dev
```

Open `http://localhost:3000`. The frontend uses relative `/api` requests, which Vite forwards to the backend during development.

### 3. Optional payment configuration

The payment controller references these additional environment variables:

```dotenv
PAYHERE_MERCHANT_ID=your_merchant_id
PAYHERE_MERCHANT_SECRET=your_merchant_secret
FRONTEND_URL=http://localhost:3000
PAYHERE_NOTIFY_URL=your_reachable_notification_endpoint
```

Use a sandbox account for demonstrations and configure callback URLs for your own environment. Payment-provider availability and end-to-end payment behavior have not been newly tested for this publication.

### Frontend build

```bash
cd frontend
npm run build
```

This generates `frontend/dist`. A production deployment also needs routing for `/api` and `/uploads`; the Vite development proxy does not provide production hosting configuration.

## API Areas

| Base Path | Module |
| --- | --- |
| `/api/auth` | Authentication and profiles |
| `/api/products` | Product catalogue and administration |
| `/api/orders` | Orders |
| `/api/suppliers` | Suppliers |
| `/api/inventory` | Inventory |
| `/api/services` | Services |
| `/api/bookings` | Bookings |
| `/api/reviews` | Reviews |
| `/api/warranty` | Warranty |
| `/api/notifications` | Notifications |
| `/api/payments` | Payments |
| `/api/wishlist` | Wishlist |

Protected requests use `Authorization: Bearer <token>`. Product create, update, remove, restore, and availability-change routes use the backend's authentication and admin middleware.

Refer to the relevant route, controller, and model files for complete request fields and access requirements.

## Product Module Demo

1. Start the frontend and backend with a separate demonstration database.
2. Browse the product catalogue and inspect product details.
3. Demonstrate search, filter, and sort controls.
4. Sign in with an appropriately configured administrative account.
5. Create or edit a product and upload an image.
6. Demonstrate availability and product-removal/restoration workflows.
7. Confirm the corresponding changes in the customer catalogue.

No shared login credentials or database dump are included. The admin-seeding script containing a fixed password has been excluded from this portfolio copy; provision a demo administrator in your own environment.

## Team Credits

The topic approval document assigns the following modules:

| Member | Student ID | Module |
| --- | --- | --- |
| Dilka K.B.T | IT24101143 | Order and Delivery Management |
| Ramanayaka R A S S | IT24103406 | Feedback and Warranty Management |
| Maryshalini A | IT24100683 | Supplier Management |
| Deshan S.M.K | IT24104190 | Spare Parts / Product Management |
| Disanayaka K.G.G.S | IT24102031 | Service and Booking Management |
| Jayakody J.A.K.S.S | IT24100778 | Stocks and Inventory Management |

## Publication Notes

- This repository is a portfolio copy of a university group project, with each member's module credited above.
- Environment files, uploaded images, generated frontend output, OS metadata, and the fixed-password admin-seeding script are excluded.
- Existing image references require the corresponding files; previously uploaded images are not bundled.
- The database connection code removes named legacy product indexes when present. Use a separate demonstration database for local exploration.
- Neither package defines an automated test script. No automated-test results or new runtime-verification claims are made here.
- Production deployment and further security validation remain separate work from publishing the source code.
