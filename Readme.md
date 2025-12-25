# 🚀 Pingup – Full Stack Social Networking Platform

Pingup is a modern full-stack social platform inspired by Instagram + LinkedIn.  
Users can create posts, upload stories, send messages, and build real-world connections — all powered by a clean MERN-style architecture, Clerk authentication, ImageKit media storage, and optional Inngest background jobs.

---

## 🧩 Core Features

### 👤 Authentication & Users (Clerk)
- Secure signup, login, logout, session handling
- Protected backend routes using `@clerk/express`
- Public username/handle (example: `@abhishekmamta2002`)
- Editable bio, profile picture, and personal details

### 📝 Posts – Feed System
- Create and publish posts (text + images)
- Feed shows posts from you & your connections
- Like/unlike posts (MongoDB-persisted)
- Human-readable timestamps (e.g., “7 hours ago”)

### 📸 Stories – Ephemeral Media
- Create stories with image upload (via ImageKit + multer)
- Appears in story strip at top of feed
- Automatically expire after 24 hours (handled via DB cleanup / Inngest workflow)

### 🧑‍🤝‍🧑 Social Graph (Connections)
- Send / accept / reject connection requests
- Only connected users’ posts appear in feed
- Users are discoverable under “Discover” section

### 💬 Messaging (REST-based)
- 1-to-1 private chat
- Message history stored in MongoDB
- Fetch-on-demand (no WebSockets / Socket.io used)

### 📦 Integrations
| Tool | Purpose |
|------|---------|
| Clerk | Authentication + session JWT |
| ImageKit | Cloud media storage + CDN |
| multer | Multi-file upload handling |
| NodeMailer | Email transport (notifications/contact) |
| Inngest (optional) | Scheduled background jobs (ex: clean expired stories, send emails) |

---

## 🛠️ Tech Stack

### Frontend – `client/`
- Vite + React
- React Router
- Axios (API calls)
- CSS (custom utility styling)

### Backend – `server/`
- Node.js + Express
- MongoDB + Mongoose
- Clerk Auth
- ImageKit + multer
- NodeMailer
- Inngest (workflow jobs)


---

## ⚙️ Environment Variables

### 1️⃣ Backend – `server/.env`
```env
PORT=5000

MONGO_URI=your_mongo_connection_string

# Clerk Auth
CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key

# Media Storage
IMAGEKIT_PUBLIC_KEY=your_public_key
IMAGEKIT_PRIVATE_KEY=your_private_key
IMAGEKIT_URL_ENDPOINT=https://ik.imagekit.io/your_endpoint

# Email
SMTP_HOST=smtp.yourprovider.com
SMTP_PORT=587
SMTP_USER=email_username
SMTP_PASS=email_password

# Inngest
INNGEST_EVENT_KEY=your_inngest_key
INNGEST_SIGNING_KEY=your_signing_key

2️⃣ Frontend – client/.env

VITE_API_BASE_URL=http://localhost:5000/api
VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key

🚀 Running the Project Locally

git clone https://github.com/AbhishekSingh-Web-dev/pingup-full-stack.git
cd pingup-full-stack


Start Backend (API Server)

cd server
npm install
npm run dev   # or: npm start


Start Frontend (React App)


cd client
npm install
npm run dev









