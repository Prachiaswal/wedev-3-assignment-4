# Lab 4 - Secure Connect and Communication Platform

Backend project (Web Dev III, Unit 4) built with Node.js, Express, JWT, bcrypt, dotenv and Socket.IO.
Data is stored in memory (arrays), so it resets when the server restarts.

## Features
- Signup and login with bcrypt password hashing
- JWT authentication and protected routes
- Role-based access control (user / admin)
- Secure Notes API (CRUD, each user sees only their own notes)
- Real-time chat using Socket.IO (JWT-secured)
- Event-driven logging using EventEmitter

## Setup
```bash
npm install
cp .env.example .env     # then set your own JWT_SECRET
npm start                # http://localhost:3000
```

## API Endpoints
| Method | Route | Access |
|---|---|---|
| POST | /auth/signup | public (username, password, optional role "admin") |
| POST | /auth/login | public, returns JWT |
| GET | /profile | logged-in user |
| GET | /admin/users | admin only |
| POST, GET | /notes | own notes |
| GET, PUT, DELETE | /notes/:id | own notes |

Send the token as: `Authorization: Bearer <token>`

## Postman Output Screenshots

### 1. Signup
![Signup](screenshots/01-signup.png)

### 2. Login (JWT token returned)
![Login](screenshots/02-login.png)

### 3. Notes API blocked without token
![No token](screenshots/03-notes-no-token.png)

### 4. Protected route /profile with token
![Profile](screenshots/04-profile.png)

### 5. Admin route as normal user (403)
![Admin denied](screenshots/05-admin-denied.png)

### 6. Admin route as admin (200)
![Admin allowed](screenshots/06-admin-allowed.png)

### 7. Create note
![Create note](screenshots/07-create-note.png)

### 8. Get all notes
![Get notes](screenshots/08-get-notes.png)

### 9. Update note
![Update note](screenshots/09-update-note.png)

### 10. Delete note
![Delete note](screenshots/10-delete-note.png)

## Real-Time Chat (Socket.IO)

### 11. Chat in browser (two users)
![Chat browser](screenshots/11-chat-browser.png)

### 12. Server console showing [EVENT] and [SOCKET] logs
![Console logs](screenshots/12-console-logs.png)
