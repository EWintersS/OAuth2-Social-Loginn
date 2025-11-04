\# 🔐 OAuth2 Social Login System



A full-stack MERN application implementing secure OAuth 2.0 authentication with Google and Facebook providers.



\## 📸 Features



✅ \*\*Password-less Authentication\*\* - Sign in with Google/Facebook  

✅ \*\*Account Linking\*\* - Connect multiple OAuth providers  

✅ \*\*JWT Sessions\*\* - Secure httpOnly cookie-based authentication  

✅ \*\*Protected Routes\*\* - Role-based access control  

✅ \*\*Profile Management\*\* - Update user information  

✅ \*\*Provider Management\*\* - Link/unlink OAuth accounts  

✅ \*\*Responsive UI\*\* - Mobile-friendly React interface  

✅ \*\*Secure by Default\*\* - CORS, CSRF protection, input validation  



---



\## 🏗️ Tech Stack



\### Frontend

\- \*\*React 18\*\* - UI library

\- \*\*React Router v6\*\* - Client-side routing

\- \*\*Context API\*\* - State management

\- \*\*Axios\*\* - HTTP client

\- \*\*Tailwind CSS\*\* - Styling



\### Backend

\- \*\*Node.js\*\* - Runtime

\- \*\*Express\*\* - Web framework

\- \*\*Passport.js\*\* - OAuth strategies

\- \*\*MongoDB\*\* - Database

\- \*\*Mongoose\*\* - ODM

\- \*\*JWT\*\* - Token-based auth



---



\## 🚀 Quick Start



\### Prerequisites

```bash

node >= 18.0.0

npm >= 9.0.0

mongodb >= 5.0

```



\### 1. Clone Repository

```bash

git clone <your-repo-url>

cd oauth-login-project

```



\### 2. Backend Setup

```bash

cd server

npm install

cp .env.example .env

\# Edit .env with your credentials

npm run dev

```



\### 3. Frontend Setup

```bash

cd client

npm install

echo "VITE\_API\_URL=http://localhost:5000/api" > .env

npm run dev

```



\### 4. Access Application

\- Frontend: http://localhost:5173

\- Backend: http://localhost:5000



---



\## 🔑 OAuth Credentials Setup



\### Google OAuth

1\. Go to \[Google Cloud Console](https://console.cloud.google.com/)

2\. Create project → Enable Google+ API

3\. Create OAuth 2.0 Client ID

4\. Add redirect URI: `http://localhost:5000/api/auth/google/callback`

5\. Copy Client ID and Secret to `.env`



\### Facebook OAuth

1\. Go to \[Facebook Developers](https://developers.facebook.com/)

2\. Create app → Add Facebook Login

3\. Add redirect URI: `http://localhost:5000/api/auth/facebook/callback`

4\. Copy App ID and Secret to `.env`



---



\## 📁 Project Structure



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

│   ├── package.json

│   └── .env

│

├── client/                      # Frontend

│   ├── src/

│   │   ├── components/

│   │   │   ├── Navbar.jsx

│   │   │   └── ProtectedRoute.jsx

│   │   ├── pages/

│   │   │   ├── Home.jsx

│   │   │   ├── Login.jsx

│   │   │   ├── Dashboard.jsx

│   │   │   └── Profile.jsx

│   │   ├── context/

│   │   │   └── AuthContext.jsx

│   │   ├── utils/

│   │   │   └── api.js

│   │   ├── App.jsx

│   │   └── main.jsx

│   ├── package.json

│   └── .env

│

└── README.md

```



---



\## 🔌 API Endpoints



\### Authentication

| Method | Endpoint | Description |

|--------|----------|-------------|

| GET | `/api/auth/google` | Initiate Google OAuth |

| GET | `/api/auth/google/callback` | Google callback |

| GET | `/api/auth/facebook` | Initiate Facebook OAuth |

| GET | `/api/auth/facebook/callback` | Facebook callback |

| POST | `/api/auth/logout` | Logout user |

| GET | `/api/auth/status` | Check auth status |



\### User (Protected)

| Method | Endpoint | Description |

|--------|----------|-------------|

| GET | `/api/user/profile` | Get user profile |

| PUT | `/api/user/profile` | Update profile |

| DELETE | `/api/user/provider/:provider` | Unlink provider |



---



\## 🗄️ Database Schema



```javascript

User {

&nbsp; \_id: ObjectId

&nbsp; email: String (unique, required)

&nbsp; name: String (required)

&nbsp; avatar: String

&nbsp; providers: \[{

&nbsp;   provider: 'google' | 'facebook'

&nbsp;   providerId: String

&nbsp;   email: String

&nbsp;   connectedAt: Date

&nbsp; }]

&nbsp; role: 'user' | 'admin'

&nbsp; lastLogin: Date

&nbsp; createdAt: Date

&nbsp; updatedAt: Date

}

```



---



\## 🔒 Security Features



\- ✅ \*\*HttpOnly Cookies\*\* - XSS protection

\- ✅ \*\*CORS Configuration\*\* - Origin whitelisting

\- ✅ \*\*CSRF Protection\*\* - SameSite cookies

\- ✅ \*\*Input Validation\*\* - Sanitization

\- ✅ \*\*JWT Expiration\*\* - Token lifecycle

\- ✅ \*\*Secure Sessions\*\* - MongoDB store

\- ✅ \*\*HTTPS Required\*\* - Production mode

\- ✅ \*\*Rate Limiting\*\* - Brute force prevention



---



\## 🧪 Testing



\### Test User Flow

1\. Visit http://localhost:5173

2\. Click "Login"

3\. Choose Google or Facebook

4\. Authorize application

5\. View Dashboard

6\. Edit Profile

7\. Link/Unlink accounts

8\. Logout



\### Test Scenarios

\- ✅ First-time Google login

\- ✅ Returning user login

\- ✅ Account linking (Google + Facebook)

\- ✅ Profile update

\- ✅ Provider unlinking

\- ✅ Protected route access

\- ✅ Session persistence



---



\## 🐛 Troubleshooting



\### "Redirect URI mismatch"

\*\*Solution:\*\* Ensure exact URIs in OAuth console:

```

http://localhost:5000/api/auth/google/callback

http://localhost:5000/api/auth/facebook/callback

```



\### CORS Errors

\*\*Solution:\*\* Check `CLIENT\_URL` in backend `.env`:

```env

CLIENT\_URL=http://localhost:5173

```



\### Session Not Persisting

\*\*Solution:\*\* Ensure `withCredentials: true` in axios and cookies enabled



\### MongoDB Connection Failed

\*\*Solution:\*\* Start MongoDB service:

```bash

mongod

\# or

docker run -d -p 27017:27017 mongo

```



---



\## 📦 Environment Variables



\### Backend (.env)

```env

NODE\_ENV=development

PORT=5000

CLIENT\_URL=http://localhost:5173

MONGO\_URI=mongodb://localhost:27017/oauth\_db

JWT\_SECRET=your\_jwt\_secret\_here

SESSION\_SECRET=your\_session\_secret\_here

GOOGLE\_CLIENT\_ID=your\_google\_client\_id

GOOGLE\_CLIENT\_SECRET=your\_google\_secret

FACEBOOK\_APP\_ID=your\_facebook\_app\_id

FACEBOOK\_APP\_SECRET=your\_facebook\_secret

```



\### Frontend (.env)

```env

VITE\_API\_URL=http://localhost:5000/api

```



---



\## 🚢 Deployment



\### Backend (Render/Railway/Heroku)

1\. Set all environment variables

2\. Update OAuth redirect URIs to production domain

3\. Set `NODE\_ENV=production`

4\. Use MongoDB Atlas for database



\### Frontend (Vercel/Netlify)

1\. Update `VITE\_API\_URL` to production backend

2\. Build: `npm run build`

3\. Deploy `dist` folder



---



\## 📝 NPM Scripts



\### Backend

```json

{

&nbsp; "start": "node server.js",

&nbsp; "dev": "nodemon server.js"

}

```



\### Frontend

```json

{

&nbsp; "dev": "vite",

&nbsp; "build": "vite build",

&nbsp; "preview": "vite preview"

}

```



---



\## 🎓 Learning Resources



\- \[Passport.js Docs](http://www.passportjs.org/)

\- \[OAuth 2.0 RFC](https://tools.ietf.org/html/rfc6749)

\- \[Google OAuth Guide](https://developers.google.com/identity/protocols/oauth2)

\- \[Facebook Login Docs](https://developers.facebook.com/docs/facebook-login)

\- \[JWT Best Practices](https://tools.ietf.org/html/rfc8725)



---



\## 🎯 Future Enhancements



\- \[ ] Add GitHub OAuth provider

\- \[ ] Implement email/password fallback

\- \[ ] Add two-factor authentication

\- \[ ] Create admin dashboard

\- \[ ] Add role-based permissions

\- \[ ] Implement refresh tokens

\- \[ ] Add activity logs

\- \[ ] Email verification



---



\## 📄 License



MIT License - Feel free to use this project for learning!



---



\## 👨‍💻 Author



\*\*Your Name\*\*  

\- GitHub: \[@Harsh13912](https://github.com/Harsh13912)

\- Email: 23bcs13912@gmail.com



---



\## 🙏 Acknowledgments



\- Passport.js team for OAuth strategies

\- MongoDB for database

\- React team for amazing UI library

\- Tailwind CSS for utility classes



---



\*\*⭐ Star this repo if you found it helpful!\*\*

