# HOSTELNOW

A comprehensive MERN stack property rental platform designed for hostel and accommodation bookings. HostelNow provides a seamless experience for property owners to list their properties and for users to search, book, and review accommodations.

![MERN Stack](https://img.shields.io/badge/Stack-MERN-green)

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [API Endpoints](#api-endpoints)
- [Environment Variables](#environment-variables)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Project Overview

HostelNow is a full-stack property rental application that enables users to browse, search, and book accommodations. Property owners can create and manage listings, while users can search for properties based on various criteria, view detailed information with interactive maps, leave reviews, and complete secure payments.

## 🛠️ Tech Stack

### Frontend

- **React 18.2** - UI library
- **Vite 4.4** - Build tool and development server
- **Redux Toolkit** - State management
- **Redux Persist** - Persist Redux state
- **React Router DOM** - Client-side routing
- **Tailwind CSS** - Utility-first CSS framework
- **Flowbite React** - UI components
- **Firebase** - Authentication and image storage
- **Leaflet & React Leaflet** - Interactive maps
- **Swiper** - Image carousel/gallery
- **Axios** - HTTP client
- **React Icons** - Icon library

### Backend

- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM
- **JWT** - Authentication tokens
- **bcryptjs** - Password hashing
- **Cookie Parser** - Parse cookies
- **CORS** - Cross-origin resource sharing
- **Stripe** - Payment processing
- **AWS Comprehend** - Sentiment analysis for comments

## ✨ Features

### User Features

- 🔐 **User Authentication** - Sign up/Sign in with email or Google OAuth
- 🏘️ **Property Listings** - Browse and search properties with advanced filters
- 🔍 **Advanced Search** - Filter by type (rent/sale), price, amenities (parking, furnished), and more
- 🗺️ **Interactive Maps** - View property locations on Leaflet maps
- 📸 **Image Galleries** - Swiper-powered image carousels for property photos
- 💳 **Secure Payments** - Stripe integration for booking payments
- ⭐ **Reviews & Ratings** - Leave comments and ratings with sentiment analysis
- 👤 **User Profile** - Manage account settings and view your listings
- 📱 **Responsive Design** - Mobile-friendly interface

### Admin Features

- 📊 **Dashboard** - Admin panel for managing users, listings, and comments
- 📝 **Listing Management** - Create, update, and delete property listings
- 👥 **User Management** - View and manage registered users
- 💬 **Comment Moderation** - Monitor and manage user reviews

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v14.0 or higher)
- **npm** (v6.0 or higher) or **yarn**
- **MongoDB** (v4.0 or higher) - Local installation or MongoDB Atlas account
- **Git** - Version control

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/mern-estate.git
cd mern-estate
```

### 2. Install Dependencies

#### Install server dependencies:

```bash
npm install
```

#### Install client dependencies:

```bash
cd client
npm install
cd ..
```

### 3. Environment Variables Setup

Create a `.env` file in the root directory and add the following variables:

```env
# MongoDB Connection
MONGO=your_mongodb_connection_string

# JWT Secret Key
JWT_SECRET=your_jwt_secret_key

# Stripe Payment
STRIPE_SECRET_KEY=your_stripe_secret_key

# AWS Comprehend (for sentiment analysis)
AWS_ACCESS_KEY=your_aws_access_key
AWS_SECRET_KEY=your_aws_secret_key
```

### 4. Firebase Configuration

Update the Firebase configuration in `client/src/firebase.js` with your Firebase project credentials:

```javascript
const firebaseConfig = {
  apiKey: "your_firebase_api_key",
  authDomain: "your_project.firebaseapp.com",
  projectId: "your_project_id",
  storageBucket: "your_project.appspot.com",
  messagingSenderId: "your_messaging_sender_id",
  appId: "your_app_id",
};
```

### 5. Database Configuration

- **Local MongoDB**: Ensure MongoDB is running on your machine
- **MongoDB Atlas**: Create a cluster and get your connection string

Update the `MONGO` variable in your `.env` file with your connection string.

## 🏃 Running the Application

### Development Mode

#### Run both client and server concurrently:

**Terminal 1 - Start the backend server:**

```bash
npm run dev
```

The server will run on `http://localhost:3000`

**Terminal 2 - Start the frontend development server:**

```bash
cd client
npm run dev
```

The client will run on `http://localhost:5173`

### Production Mode

Build and run the application:

```bash
npm run build
npm start
```

This will:

1. Install all dependencies
2. Build the client for production
3. Serve the static files from the Express server

## 📁 Project Structure

```
MERN_ESTATE/
├── api/                          # Backend server
│   ├── controllers/              # Route controllers
│   │   ├── auth.controller.js    # Authentication logic
│   │   ├── user.controller.js    # User management
│   │   ├── listing.controller.js # Property listings
│   │   └── comment.controller.js # Comments & reviews
│   ├── models/                   # Mongoose models
│   │   ├── user.model.js         # User schema
│   │   ├── listing.model.js      # Listing schema
│   │   └── comment.model.js      # Comment schema
│   ├── routes/                   # API routes
│   │   ├── auth.route.js         # Auth endpoints
│   │   ├── user.route.js         # User endpoints
│   │   ├── listing.route.js      # Listing endpoints
│   │   └── comment.route.js      # Comment endpoints
│   ├── utils/                    # Utility functions
│   │   ├── verifyUser.js         # JWT verification
│   │   ├── error.js              # Error handler
│   │   └── sentiment-analysis.js # AWS Comprehend integration
│   └── index.js                  # Server entry point
├── client/                       # Frontend application
│   ├── public/                   # Static assets
│   ├── src/
│   │   ├── components/           # Reusable components
│   │   │   ├── Header.jsx
│   │   │   ├── PrivateRoute.jsx
│   │   │   ├── OAuth.jsx
│   │   │   ├── ListingItem.jsx
│   │   │   ├── Map.jsx
│   │   │   └── comments/         # Comment components
│   │   ├── pages/                # Page components
│   │   │   ├── Home.jsx
│   │   │   ├── SignIn.jsx
│   │   │   ├── SignUp.jsx
│   │   │   ├── Profile.jsx
│   │   │   ├── Search.jsx
│   │   │   ├── Listing.jsx
│   │   │   ├── CreateListing.jsx
│   │   │   ├── UpdateListing.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   └── About.jsx
│   │   ├── redux/                # Redux store & slices
│   │   │   ├── store.js
│   │   │   └── user/
│   │   ├── firebase.js           # Firebase configuration
│   │   ├── App.jsx               # Main app component
│   │   └── main.jsx              # Entry point
│   ├── index.html
│   ├── vite.config.js            # Vite configuration
│   ├── tailwind.config.js        # Tailwind CSS config
│   └── package.json
├── .env                          # Environment variables
├── .gitignore
├── package.json                  # Server dependencies
└── README.md

## 🔌 API Endpoints

### Authentication Routes (`/api/auth`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/signup` | Register a new user | No |
| POST | `/signin` | Login user | No |
| POST | `/google` | Google OAuth login | No |
| GET | `/signout` | Logout user | No |

### User Routes (`/api/user`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/test` | Test route | No |
| POST | `/update/:id` | Update user profile | Yes |
| DELETE | `/delete/:id` | Delete user account | Yes |
| GET | `/listings/:id` | Get user's listings | Yes |
| GET | `/:id` | Get user by ID | Yes |

### Listing Routes (`/api/listing`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/create` | Create new listing | Yes |
| DELETE | `/delete/:id` | Delete listing | Yes |
| POST | `/update/:id` | Update listing | Yes |
| GET | `/get/:id` | Get single listing | No |
| GET | `/get` | Get all listings (with filters) | No |
| POST | `/reduceBooking` | Process booking & payment | No |
| GET | `/listingScore/:listingId` | Get average rating | No |

### Comment Routes (`/api/comment`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/addComment` | Add new comment | No |
| GET | `/allComments/:listingId` | Get all comments for listing | No |
| GET | `/getComment/:id` | Get comment by ID | No |
| DELETE | `/deleteComment/:id` | Delete comment | No |
| PATCH | `/updateComment/:id` | Update comment | No |

### Query Parameters for Listings

The `/api/listing/get` endpoint supports the following query parameters:

- `searchTerm` - Search by property name
- `type` - Filter by type: `rent`, `sale`, or `all`
- `parking` - Filter by parking availability: `true` or `false`
- `furnished` - Filter by furnished status: `true` or `false`
- `offer` - Filter by special offers: `true` or `false`
- `sort` - Sort field (default: `createdAt`)
- `order` - Sort order: `asc` or `desc` (default: `desc`)
- `limit` - Number of results (default: 9)
- `startIndex` - Pagination start index (default: 0)

**Example:**
```

GET /api/listing/get?type=rent&parking=true&sort=regularPrice&order=asc&limit=10

````

## 🔐 Environment Variables

### Required Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `MONGO` | MongoDB connection string | `mongodb+srv://user:pass@cluster.mongodb.net/dbname` |
| `JWT_SECRET` | Secret key for JWT tokens | `your_random_secret_key_here` |
| `STRIPE_SECRET_KEY` | Stripe secret key for payments | `sk_test_...` |
| `AWS_ACCESS_KEY` | AWS access key for Comprehend | `AKIA...` |
| `AWS_SECRET_KEY` | AWS secret key for Comprehend | `your_aws_secret` |

### Firebase Configuration (client-side)

Update `client/src/firebase.js` with your Firebase project credentials from the Firebase Console.

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/AmazingFeature
````

3. **Commit your changes**
   ```bash
   git commit -m 'Add some AmazingFeature'
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/AmazingFeature
   ```
5. **Open a Pull Request**

### Coding Standards

- Follow ESLint rules configured in the project
- Use meaningful variable and function names
- Write clean, readable code with proper comments
- Test your changes before submitting

## 🙏 Acknowledgments

- MongoDB for the database
- Firebase for authentication and storage
- Stripe for payment processing
- AWS Comprehend for sentiment analysis
- All contributors and open-source libraries used in this project

## 📞 Support

If you need help or have questions, please open an issue in this repository.

---

**Made with ❤️ using the MERN Stack**
