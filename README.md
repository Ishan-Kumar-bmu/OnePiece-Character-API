# Character API

Backend tutorial project: Node.js, Express and MongoDB, organised as Model-Route-Controller.

## Setup

1. Install packages:
   ```
   npm install
   ```
2. Copy `.env.example` to `.env` and fill in your values:
   ```
   PORT=3000
   MONGO_URI=<your MongoDB Atlas connection string>
   JWT_SECRET=<any long random string>
   ```
3. Start the server:
   ```
   npm start
   ```
   (or `npm run dev` to auto-restart on changes)

## Structure

```
config/db.js                 MongoDB connection
models/User.js, Post.js      Database models
controllers/                 Request logic
routes/                      URL -> controller mapping
middleware/authMiddleware.js Checks the login cookie
server.js                    Entry point
```

## API endpoints

| Method | URL                  | Auth | Body                          |
|--------|----------------------|------|-------------------------------|
| POST   | /api/auth/register   | no   | username, email, password     |
| POST   | /api/auth/login      | no   | email, password               |
| POST   | /api/auth/logout     | no   | -                             |
| GET    | /api/posts           | no   | -                             |
| GET    | /api/posts/:id       | no   | -                             |
| POST   | /api/posts           | yes  | name, description, anime, imageUrl |
| PUT    | /api/posts/:id       | yes  | any of the fields above       |
| DELETE | /api/posts/:id       | yes  | -                             |

"Auth" means you must log in first. Postman stores the login cookie automatically.

## Testing in Postman

1. POST `/api/auth/register`, then POST `/api/auth/login` (check the cookie is saved).
2. POST `/api/posts` with JSON, expect status `201`.
3. GET `/api/posts`, PUT and DELETE `/api/posts/:id`, and check the status codes.
