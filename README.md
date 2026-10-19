# 📰 MVC Tech Blog

A full-stack CMS-style tech blog where developers can publish articles, comment on each other's posts, and manage their own content from a personal dashboard. Built with the Model-View-Controller pattern using Handlebars.js, Sequelize, PostgreSQL, and Express.js — deployed on Render.


---

## 📖 Overview

This project follows the MVC architectural pattern end to end. Handlebars templates handle the View layer; Sequelize models with PostgreSQL back the Model layer; Express routes and controllers form the Controller layer. Authentication is managed with `express-session` and `bcrypt`, and sessions automatically expire after a period of inactivity to protect logged-in users.

---

## ✨ Features

- 🏠 **Homepage** — displays all published blog posts with author and creation date
- 🔐 **Sign up / Log in / Log out** — secure authentication with bcrypt-hashed passwords
- 📝 **Post detail page** — view a full post and all comments; add a comment when logged in
- 🗂️ **Dashboard** — personal view of your own posts; create, update, or delete them
- ⏱️ **Idle session timeout** — re-prompts for login after a configurable period of inactivity
- 🧩 **Handlebars partials** — reusable templates for the nav, post cards, and comment form
- 🚀 **Deployed to Render** with PostgreSQL as the production database

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Runtime | Node.js |
| Server | Express.js |
| View Engine | Handlebars.js (`express-handlebars`) |
| ORM | Sequelize |
| Database | PostgreSQL |
| Auth | `express-session`, `connect-session-sequelize`, `bcrypt` |
| Environment | `dotenv` |
| Deployment | Render |

---

## 🚀 Getting Started

### Prerequisites

- Node.js (v18+)
- PostgreSQL running locally

### Installation

```bash
git clone https://github.com/Voobane/Model-View-Controller-MVC-Tech-Blog.git
cd Model-View-Controller-MVC-Tech-Blog
npm install
```

### Environment Setup

Create a `.env` file in the root:

```env
DB_NAME=tech_blog_db
DB_USER=your_postgres_username
DB_PASSWORD=your_postgres_password
SESSION_SECRET=your_secret_key
```

### Database Setup

```bash
psql -U postgres
\i db/schema.sql
\q
```

### Running the App

```bash
npm start
```

Visit `http://localhost:3001`.

---

## 📁 Project Structure

```
Model-View-Controller-MVC-Tech-Blog/
├── config/
│   └── connection.js       # Sequelize + pg connection
├── controllers/
│   ├── api/
│   │   ├── userRoutes.js   # POST /api/users (signup, login, logout)
│   │   └── postRoutes.js   # CRUD for posts and comments
│   └── homeRoutes.js       # GET routes for Handlebars pages
├── db/
│   └── schema.sql          # CREATE DATABASE statement
├── models/
│   ├── User.js             # username, email, password (hashed via hook)
│   ├── Post.js             # title, content, user_id FK
│   ├── Comment.js          # comment_text, user_id FK, post_id FK
│   └── index.js            # Associations
├── public/
│   └── js/                 # Client-side JS for form submissions
├── seeds/                  # Optional seed data
├── utils/
│   ├── auth.js             # withAuth middleware (session check)
│   └── helpers.js          # Handlebars format_date helper
├── views/
│   ├── layouts/
│   │   └── main.handlebars
│   ├── partials/           # nav, post-card, comment-form
│   ├── homepage.handlebars
│   ├── post.handlebars
│   ├── dashboard.handlebars
│   ├── login.handlebars
│   └── signup.handlebars
├── server.js
└── README.md
```

---

## 💡 What I Learned

- Implementing the **MVC pattern** in a Node.js app — separating data, logic, and presentation cleanly
- Rendering server-side views with **Handlebars.js** — layouts, partials, and custom helpers
- Modeling **relational data** with Sequelize — `belongsTo`, `hasMany` associations between Users, Posts, and Comments
- Securing routes with a custom **`withAuth` middleware** that checks session state before allowing access
- Hashing passwords with **bcrypt** in a Sequelize `beforeCreate` hook and verifying them on login
- Managing **session persistence** with `connect-session-sequelize` so sessions survive server restarts
- Deploying a Sequelize + PostgreSQL app to **Render** with environment variables

---

## 📸 Screenshots

> _Add screenshots of the homepage, dashboard, and individual post page._

---

## 👤 Author

**Matt (Voobane)**
- GitHub: [@Voobane](https://github.com/Voobane)
