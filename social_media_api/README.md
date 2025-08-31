📌 Social Media Backend API (Django + DRF)

A fully functional backend for a social networking platform built with Django and Django REST Framework (DRF).
This API powers user authentication, following/unfollowing, posting, feeds, and activity notifications — designed to be scalable and ready for integration with any frontend (React, Vue, mobile apps, etc.).

🚀 Core Features
🔑 Authentication

User registration with automatic token generation

JWT-based login & logout

Secure protected routes

👥 Social Features

Follow & unfollow other users

Personalized feed from followed accounts

📝 Posts & Comments

Create, read, update, and delete posts

Comment on posts

Like and unlike functionality

🔔 Notifications

Real-time activity tracking (follow, like, comment, post)

Each user gets a notification feed

📂 Project Layout
social_api/
│── accounts/          # User management: register, login, follow/unfollow
│   ├── models.py
│   ├── serializers.py
│   ├── views.py
│
│── posts/             # Posts & comments logic
│   ├── models.py
│   ├── serializers.py
│   ├── views.py
│
│── notifications/     # System for tracking user activity
│   ├── models.py
│   ├── serializers.py
│   ├── views.py
│
│── social_api/        # Project configuration
│   ├── settings.py
│   ├── urls.py

⚙️ Setup Guide

Clone the repository

git clone https://github.com/your-username/social_api.git
cd social_api


Create a virtual environment & activate it

python -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows


Install dependencies

pip install -r requirements.txt


Apply migrations

python manage.py migrate


Create superuser

python manage.py createsuperuser


Run the development server

python manage.py runserver

🔑 Authentication Flow

Register or login to receive a JWT access + refresh token.

Pass token in headers for authenticated requests:

Authorization: Bearer <access_token>

📡 API Endpoints
👤 Accounts

POST /api/accounts/register/ → Register a new user

POST /api/accounts/login/ → Login & get JWT tokens

POST /api/accounts/follow/<user_id>/ → Follow another user

POST /api/accounts/unfollow/<user_id>/ → Unfollow a user

📝 Posts

GET /api/posts/ → List all posts (with pagination, filtering, search)

POST /api/posts/ → Create a new post

GET /api/posts/<id>/ → Retrieve a single post

PUT /api/posts/<id>/ → Update a post

DELETE /api/posts/<id>/ → Delete a post

POST /api/posts/<id>/like/ → Like a post

POST /api/posts/<id>/unlike/ → Unlike a post

💬 Comments

GET /api/comments/ → List all comments

POST /api/comments/ → Add a comment

GET /api/comments/<id>/ → Get single comment

PUT /api/comments/<id>/ → Update a comment

DELETE /api/comments/<id>/ → Delete a comment

🔔 Notifications

GET /api/notifications/ → Fetch all notifications for the logged-in user

Sample Notification Response

[
  {
    "id": 1,
    "actor": "jane_doe",
    "verb": "liked your post",
    "target": "My first post",
    "timestamp": "2025-08-24T21:12:00Z",
    "read": false
  }
]

🛠️ Tech Stack

Python 3.x

Django 5.x

Django REST Framework

JWT Authentication (SimpleJWT)

PostgreSQL / SQLite (local dev)

✅ Example Usage Flow

User A registers & logs in → gets JWT token.

User A follows User B → User B gets a notification.

User A writes a post → shows up in feeds of User A’s followers.

User B likes the post → User A gets a notification.

📜 License

Open-source project — free to use and extend.

✨ This backend is designed to be lightweight, modular, and easily extendable. Perfect for building your own social media app, integrating with a mobile frontend, or experimenting with real-time user interactions.
