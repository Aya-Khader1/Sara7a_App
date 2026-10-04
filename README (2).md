# Sara7a App

A backend REST API for an anonymous messaging platform. Users get a personal profile, share it, and receive anonymous messages from anyone. Includes secure authentication, Google sign-in, message management, and request logging.

Built with **Node.js, Express, and MongoDB**.

## Features

### Authentication & Security
- Registration and login with JWT-based authentication (access and refresh tokens)
- Email verification with expiring OTP codes (Nodemailer)
- Separate token secrets and lifetimes for users and admins
- Google sign-in (Google OAuth token verification)
- Secure password hashing
- Rate limiting on login to protect against brute-force attempts
- Helmet and CORS configuration
- OTP codes stored in Redis with an expiry time

### Users
- Profile management
- File uploads (Multer) with file-type validation

### Messages
- Send anonymous messages to any user
- Retrieve received messages with pagination
- Toggle a message's read / unread status

### Quality & Observability
- Request validation with Joi
- HTTP request logging (Morgan) and application logging

## Tech Stack

| Area | Technology |
|---|---|
| Runtime | Node.js (ES Modules) |
| Framework | Express 5 |
| Database | MongoDB with Mongoose |
| In-memory store | Redis (OTP storage) |
| Auth | JSON Web Tokens, Google Auth Library |
| Validation | Joi |
| Security | Helmet, CORS, express-rate-limit |
| Uploads | Multer, file-type |
| Email | Nodemailer |
| Logging | Morgan |

## Project Structure

```
.
├── config/            environment configuration
├── social-login/      Angular client used to test Google sign-in
├── index.js           application entry point
└── src/
    ├── app.controller.js   app bootstrap (middlewares, routes, DB)
    ├── DB/                 database connection and models
    ├── Middlewares/        authentication, validation, error handling
    ├── Modules/
    │   ├── Auth/           registration, login, Google sign-in
    │   ├── User/           profile management
    │   └── Messages/       send, list, and manage messages
    ├── Utils/              helpers
    └── loggers/            logging setup
```

## Getting Started

### Prerequisites
- Node.js 20+
- A MongoDB instance (local or Atlas)
- A Redis instance
- Google OAuth credentials
- A Gmail account with an App Password (for sending OTP emails)

### Installation

```bash
git clone https://github.com/Aya-Khader1/Sara7a_App.git
cd Sara7a_App
npm install
```

### Environment Variables

Create a `.env` file in the project root (never commit it):

```env
# App
PORT=3000
NODE_ENV=development
CLIENT_URL=http://localhost:4200

# Database
DB_URI=mongodb+srv://<username>:<password>@<cluster>.mongodb.net/<database>

# Redis
REDIS_URI=redis://127.0.0.1:6379

# Security
SALT_ROUND=12
ENC_KEY=your_32_character_encryption_key

# User tokens
ACCESS_TOKEN_USER_SECRET=your_secret
ACCESS_TOKEN_USER_EXPIRES_IN=3600
REFRESH_TOKEN_USER_SECRET=your_secret
REFRESH_TOKEN_USER_EXPIRES_IN=14400

# Admin tokens
ACCESS_TOKEN_ADMIN_SECRET=your_secret
ACCESS_TOKEN_ADMIN_EXPIRES_IN=86400
REFRESH_TOKEN_ADMIN_SECRET=your_secret
REFRESH_TOKEN_ADMIN_EXPIRES_IN=172800

# Google OAuth
CLIENT_ID=your_google_client_id

# Email
USER_EMAIL=your_email@gmail.com
USER_PASS=your_app_password

# OTP (seconds)
OTP_EXPIRES_IN=300

# CORS
WHITE_LIST=http://127.0.0.1:4200,http://127.0.0.1:5173
```

### Run in Development

```bash
npm run dev
```

## Author

**Ayah Khader**: Software Engineering student, backend developer
[GitHub](https://github.com/Aya-Khader1)
