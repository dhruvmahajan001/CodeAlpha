# ConnectHub — Modern Mini Social Media Platform

ConnectHub is a modern, responsive, internship-level social media platform built for **CodeAlpha Task 2**. It features user account creation, secure login, a live home feed with trending hashtag tracking, user search, post creation (supporting both direct image URLs and local base64 photo uploads), like/unlike toggles, thread-based comments, and an interactive follow/unfollow system.

The application incorporates a sleek, glassmorphic layout and comes with full **Dark Mode** theme configuration out of the box.

---

## Technical Stack

*   **Frontend**: HTML5, CSS3 (Vanilla design tokens, CSS variables, glassmorphic card patterns), Vanilla ES6 JavaScript
*   **Backend**: Node.js, Express.js
*   **Database**: MongoDB Atlas, Mongoose ODM
*   **Authentication**: JSON Web Tokens (JWT) & `bcryptjs` password hashing

---

## Directory Structure

```
task2
├── frontend
│   ├── index.html            # Main dashboard / feed view
│   ├── login.html            # Security login panel
│   ├── register.html         # User account registration panel
│   ├── profile.html          # Dynamic profile views & editing
│   ├── post.html             # Thread details, comment inputs
│   ├── css
│   │   └── style.css         # Responsive styling & dark theme
│   └── js
│       ├── config.js         # API URL environmental switches
│       ├── api.js            # Centralized API fetch engine
│       ├── auth.js           # Route guards, dark mode, user snippets
│       ├── feed.js           # Feed rendering, hashtags, likes, creators
│       ├── profile.js        # Profile detail manager, uploads
│       └── post.js           # Thread load controllers, comment submission
├── backend
│   ├── config
│   │   └── db.js             # Mongoose connection bootstrapper
│   ├── controllers
│   │   ├── authController.js # Handles registration & log ins
│   │   ├── userController.js # Profiles editing, follows & suggestions
│   │   └── postController.js # Post CRUD, likes, comments, hashtag trend logs
│   ├── middleware
│   │   ├── authMiddleware.js # JWT token validation routing guard
│   │   └── errorMiddleware.js# Custom Express JSON error responder
│   ├── models
│   │   ├── User.js           # MongoDB User Schema definition
│   │   ├── Post.js           # MongoDB Post Schema definition
│   │   └── Comment.js        # MongoDB Comment Schema definition
│   ├── routes
│   │   ├── authRoutes.js     # Express auth routes mapping
│   │   ├── userRoutes.js     # Express profile/follow routes mapping
│   │   └── postRoutes.js     # Express post/like/comment routes mapping
│   ├── package.json          # Node dependencies configuration
│   ├── server.js             # Application bootstrapper file
│   ├── .env.example          # Environment variables template
│   └── .gitignore            # Version control ignore lists
└── README.md                 # Complete project documentation
```

---

## Local Development Startup Guide

### Prerequisites
*   Node.js installed (v18.0.0 or higher recommended)
*   A MongoDB Atlas connection URI or local MongoDB instance

### 1. Backend Server Setup
1. Open a terminal and navigate to the backend directory:
   ```bash
   cd backend
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create a `.env` file based on the template:
   ```bash
   copy .env.example .env
   ```
4. Edit the `.env` file and replace the placeholders:
   *   `MONGODB_URI`: Insert your MongoDB Atlas connection string.
   *   `JWT_SECRET`: Insert a private key string (e.g. `my_super_secret_connecthub_key_123`).
   *   `PORT`: Keep it at `5000` (or match whatever port you want).
5. Start the backend developer server:
   ```bash
   npm run dev
   ```
   *(The terminal should output `MongoDB Connected: ...` and `Server running on port 5000`)*

### 2. Frontend Client Setup
1. The frontend uses static Vanilla JS and HTML. You can launch it using any web host or local static server.
2. In VS Code, you can click **Go Live** using the *Live Server* extension on the `frontend/index.html` file.
3. Keep the default local server url at `http://127.0.0.1:5500` or `http://localhost:5500`. Ensure that the backend CORS rules allow cross-origin requests.

---


## Premium Features Added
*   **Theme Toggle**: Fully responsive Dark Mode using CSS styling variables.
*   **Dynamic suggested users**: Fetches recommended profiles excluding accounts you already follow.
*   **Dynamic trending hashtags**: Renders active tags compiled directly from current posts. Clicking a tag immediately filters the Home Feed.
*   **No-Cloud base64 file uploads**: Upload profile avatar changes and post images locally without external AWS/Cloudinary configuration requirements.
*   **Activity relative timestamps**: Renders modern dates (e.g. `5m ago`, `2h ago`).
