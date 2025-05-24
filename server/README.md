
# 📚 LMS Backend API

This is the backend API for a Learning Management System (LMS) built with Express.js. It supports user authentication, course management, payments, reviews, and contact form handling.

---

## ✨ Features

- 👤 User registration, login, profile management, password change
- 🎓 Course CRUD with lecture management
- 💳 Payment subscription and verification using Razorpay
- ⭐ User reviews and ratings
- 📩 Contact form (authenticated)
- 🛡️ Middleware for error handling, authentication, and role authorization
- 🖼️ File uploads (avatars, course thumbnails, lecture thumbnails)
- 🔗 CORS configured for frontend integration
- 📜 Request logging with Morgan

---

## 🧰 Tech Stack

- 🟢 Node.js & Express
- 🗃️ MongoDB (assumed)
- 📁 Multer for file uploads
- 📊 Morgan for logging
- 🔄 Cors and cookie-parser
- 🔐 JWT-based authentication (assumed)

---

## 🛠️ Setup and Installation

1. 📦 Clone the repository:

   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. 📥 Install dependencies:

   ```bash
   npm install
   ```

3. 🧾 Create a `.env` file in the root directory and add environment variables:

   ```env
   PORT=5000
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret
   FRONTEND_URL=http://localhost:3000
   RAZORPAY_KEY=your_razorpay_key
   ```

4. 🚀 Run the server:

   ```bash
   npm run dev
   ```

---

## 🌐 API Endpoints

### 👥 User Routes (`/api/v1/user`)

| Method | Endpoint       | Description                                  | Auth Required | Notes                          |
|--------|----------------|----------------------------------------------|---------------|--------------------------------|
| POST   | /register      | Register a new user (supports avatar upload) | No            | Uploads avatar image           |
| POST   | /login         | Login user                                   | No            |                                |
| GET    | /logout        | Logout user                                  | No            |                                |
| GET    | /me            | Get logged-in user profile                    | Yes           | Requires authentication         |
| POST   | /change-password | Change user password                         | Yes           |                                |
| PUT    | /update        | Update user details (supports avatar upload) | Yes           | Uploads avatar image           |

---

### 📘 Course Routes (`/api/v1/courses`)

| Method | Endpoint    | Description                                 | Auth Required       | Notes                           |
|--------|-------------|---------------------------------------------|---------------------|---------------------------------|
| GET    | /           | Get all courses                             | No                  | Public endpoint                 |
| POST   | /           | Create a new course                         | Yes, ADMIN role     | Supports thumbnail upload       |
| DELETE | /           | Delete lecture from a course                | Yes, ADMIN role     |                                 |
| GET    | /:id        | Get lectures by course ID                   | Yes, SUBSCRIBER role |                                 |
| PUT    | /:id        | Update course details                       | Yes, ADMIN role     | Supports thumbnail upload       |
| DELETE | /:id        | Delete course                              | Yes, ADMIN role     |                                 |
| POST   | /:id        | Add lecture to course                       | Yes, ADMIN role     | Supports lecture thumbnail upload |

---

### 💰 Payment Routes (`/api/v1/payments`)

| Method | Endpoint        | Description                              | Auth Required   | Notes                |
|--------|-----------------|------------------------------------------|-----------------|----------------------|
| GET    | /razorpay-key   | Get Razorpay API key                     | Yes             |                      |
| POST   | /subscribe      | Subscribe to a plan                      | Yes             |                      |
| POST   | /verify         | Verify subscription payment              | Yes             |                      |
| POST   | /unsubscribe    | Cancel subscription                      | Yes             |                      |
| POST   | /               | Get all payments                         | Yes, ADMIN role |                      |

---

### ⭐ Review Routes

| Method | Endpoint          | Description             | Auth Required | Notes           |
|--------|-------------------|-------------------------|---------------|-----------------|
| POST   | /api/v1/addreview | Add a user review       | Yes           |                 |
| GET    | /api/v1/allreview | Get all reviews         | No            | Public endpoint |

---

### 📬 Contact Route

| Method | Endpoint       | Description           | Auth Required | Notes |
|--------|----------------|-----------------------|---------------|-------|
| POST   | /api/v1/contact| Submit contact form    | Yes           |       |

---

### 🛠️ Other Routes

| Method | Endpoint | Description                         |
|--------|----------|-----------------------------------|
| GET    | /ping    | Health check endpoint (`/pong`)   |
| *      | *        | Catch-all 404 Page Not Found      |

---

## 🧱 Middleware

- 🌐 **CORS:** Allows requests from the frontend URL with credentials enabled.
- 📜 **Morgan:** HTTP request logging middleware (dev format).
- 🍪 **Cookie Parser:** Parses cookies to handle sessions/auth.
- 🔐 **Authentication:** Middleware to check if user is logged in.
- 🛡️ **Authorization:** Middleware to restrict routes by user roles (`ADMIN`, `SUBSCRIBER`).
- 🛠️ **Error Handler:** Centralized error handling middleware for the API.

---

## 🖼️ File Uploads

Uses `multer` for multipart/form-data uploads:

- 👤 User avatars during registration and profile update
- 🖼️ Course thumbnails when creating/updating courses
- 🎞️ Lecture thumbnails when adding lectures

---

## 📝 Notes

- 🛠️ Replace placeholders in `.env` with your real values (MongoDB URI, JWT secret, Razorpay key, frontend URL).
- 🔧 Password reset routes (`forgotPassword`, `resetPassword`) are stubbed and commented out; implement as needed.
- 🌐 Make sure your frontend URL matches the `FRONTEND_URL` in `.env` for CORS to work properly.
- 🗃️ This backend expects MongoDB and Razorpay integration.

---

## 📄 License

MIT License
