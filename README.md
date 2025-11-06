# 🔐 OAuth2 Social Login System

A full-stack MERN application implementing secure OAuth 2.0 authentication with Google and Facebook providers.

## 🚀 Live Deployment

This project is successfully deployed and live\!

  * **Live Frontend (Netlify):** **[https://oauthloginproject.netlify.app](https://oauthloginproject.netlify.app)**
  * **Live Backend (Render):** **[https://my-oauth-server.onrender.com/api/health](https://my-oauth-server.onrender.com/api/health)**
  * **Database (MongoDB):** Hosted on **MongoDB Atlas**

-----

## 📸 Features

✅ **Password-less Authentication** - Sign in with Google/Facebook  
✅ **Account Linking** - Connect multiple OAuth providers  
✅ **JWT Sessions** - Secure httpOnly cookie-based authentication  
✅ **Protected Routes** - Role-based access control  
✅ **Profile Management** - Update user information  
✅ **Provider Management** - Link/unlink OAuth accounts  
✅ **Responsive UI** - Mobile-friendly React interface  
✅ **Secure by Default** - CORS, CSRF protection, input validation

-----

## 🏗️ Tech Stack

### Frontend

  - **React 18** - UI library
  - **React Router v6** - Client-side routing
  - **Context API** - State management
  - **Axios** - HTTP client
  - **Tailwind CSS** - Styling

### Backend

  - **Node.js** - Runtime
  - **Express** - Web framework
  - **Passport.js** - OAuth strategies
  - **MongoDB** - Database
  - **Mongoose** - ODM
  - **JWT** - Token-based auth

-----

## 🚀 Local Development Setup

### Prerequisites

```bash
node >= 18.0.0
npm >= 9.0.0
mongodb >= 5.0
```

### 1\. Clone Repository

```bash
git clone <your-repo-url>
cd oauth-login-project
```

### 2\. Backend Setup

```bash
cd server
npm install
cp .env.example .env
# Edit .env with your credentials (see .env section)
npm run dev
```

### 3\. Frontend Setup

```bash
cd client
npm install
echo "VITE_API_URL=http://localhost:5000/api" > .env
npm run dev
```

### 4\. Access Application

  - Frontend: http://localhost:5173
  - Backend: http://localhost:5000

-----

## 🔑 OAuth Credentials Setup

### Google OAuth

1.  Go to [Google Cloud Console](https://console.cloud.google.com/)
2.  Create project → Enable Google+ API
3.  Create OAuth 2.0 Client ID
4.  Add **Authorized JavaScript origins** (for frontend):
      - `http://localhost:5173` (for local dev)
      - `https://oauthloginproject.netlify.app` (for production)
5.  Add **Authorized redirect URIs** (for backend):
      - `http://localhost:5000/api/auth/google/callback` (for local dev)
      - `https://my-oauth-server.onrender.com/api/auth/google/callback` (for production)
6.  Copy Client ID and Secret to `.env`

### Facebook OAuth

1.  Go to [Facebook Developers](https://developers.facebook.com/)
2.  Create app → Add Facebook Login
3.  Add **Valid OAuth redirect URIs**:
      - `http://localhost:5000/api/auth/facebook/callback` (for local dev)
      - `https://my-oauth-server.onrender.com/api/auth/facebook/callback` (for production)
4.  Copy App ID and Secret to `.env`

-----

## 📁 Project Structure

```
oauth-login-project/
│
├── server/                      # Backend
│   ├── config/
│   │   └── passport.js         # OAuth strategies
│   ├── models/
│   │   └── User.js             # User model
│   ├── routes/
│   │   ├── auth.js             # Auth routes
│   │   └── user.js             # User routes
│   ├── middleware/
│   │   └── auth.js             # JWT middleware
│   ├── server.js               # Entry point
│   └── .env
│
├── client/                      # Frontend
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── context/
│   │   └── App.jsx
│   ├── netlify.toml            # Netlify SPA redirect config
│   └── .env
│
└── README.md
```

-----

## 🔌 API Endpoints

### Authentication

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/auth/google` | Initiate Google OAuth |
| GET | `/api/auth/google/callback` | Google callback |
| GET | `/api/auth/facebook` | Initiate Facebook OAuth |
| GET | `/api/auth/facebook/callback` | Facebook callback |
| POST | `/api/auth/logout` | Logout user |
| GET | `/api/auth/status` | Check auth status |

### User (Protected)

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/user/profile` | Get user profile |
| PUT | `/api/user/profile` | Update profile |
| DELETE | `/api/user/provider/:provider` | Unlink provider |

-----

## 🧪 Testing

### Test User Flow

1.  Visit **[https://oauthloginproject.netlify.app](https://www.google.com/url?sa=E&source=gmail&q=https://oauthloginproject.netlify.app)**
2.  Click "Login"
3.  Choose Google or Facebook
4.  Authorize application
5.  View Dashboard
6.  Edit Profile
7.  Link/Unlink accounts
8.  Logout

-----

## 🚢 Deployment

This project is deployed using a free-tier MERN stack.

### Backend (Render)

  - **Service:** `my-oauth-server` on **Render** (Web Service)
  - **Start Command:** `node server.js`
  - **Root Directory:** `server`
  - **NOTE:** Free tier services "spin down" and may take 30-50 seconds to wake up on the first request.

### Frontend (Netlify)

  - **Service:** `oauthloginproject` on **Netlify** (Static Site)
  - **Build Command:** `npm run build`
  - **Base Directory:** `client`
  - **Publish Directory:** `client/dist`
  - **Redirects:** A `client/netlify.toml` file is used to handle React Router's SPA routes.

### Database (MongoDB Atlas)

  - **Service:** **MongoDB Atlas**
  - **Tier:** M0 (Free) Shared Cluster

-----

## 📦 Environment Variables

### Backend (`.env` for Render)

```env
NODE_ENV=production
PORT=5000
CLIENT_URL=https://oauthloginproject.netlify.app
MONGO_URI=mongodb+srv://<user>:<password>@cluster.xyz.mongodb.net/
JWT_SECRET=your_jwt_secret_here
SESSION_SECRET=your_session_secret_here
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_secret
FACEBOOK_APP_ID=your_facebook_app_id
FACEBOOK_APP_SECRET=your_facebook_secret
```

### Frontend (`.env` for Netlify)

```env
VITE_API_URL=https://my-oauth-server.onrender.com/api
```

-----

## 🐛 Troubleshooting

### "Redirect URI mismatch"

**Solution:** Ensure the *exact* URIs are in your OAuth console, including `httpss://` for production.

  - **Google:** `https://my-oauth-server.onrender.com/api/auth/google/callback`
  - **Facebook:** `https://my-oauth-server.onrender.com/api/auth/facebook/callback`

### CORS Errors

**Solution:** Ensure the `CLIENT_URL` environment variable on Render is set to `https://oauthloginproject.netlify.app`.

### Session Not Persisting (Redirects to /login)

**Solution:** This is a cross-domain cookie issue. Ensure `sameSite: 'none'` and `secure: true` are set on your cookies in `server/routes/auth.js` when `NODE_ENV=production`.

-----

## 🎓 Learning Resources

  - [Passport.js Docs](http://www.passportjs.org/)
  - [OAuth 2.0 RFC](https://tools.ietf.org/html/rfc6749)
  - [Render Node.js Docs](https://render.com/docs/deploy-node-express-app)
  - [Netlify React Docs](https://www.google.com/search?q=https://docs.netlify.com/build-settings/frameworks/react/)

-----

## 👨‍💻 Author

**Your Name** - GitHub: [@Harsh13912](https://github.com/Harsh13912)

  - Email: 23bcs13912@gmail.com

-----

**⭐ Star this repo if you found it helpful\!**

