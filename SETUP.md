# 🚀 Local Setup Guide - MyFinance Platform

This document walks you through completing the setup on your Windows machine.

---

## ✅ Completed Setup Steps

- ✅ Repository cloned from GitHub
- ✅ Dependencies installed (Backend & Frontend)
- ✅ Build issues fixed
- ✅ Environment files created
- ✅ Project customized for your portfolio

---

## 🔐 Step 1: Set Up MongoDB Atlas (Cloud Database)

Since local MongoDB installation is in progress, I recommend using **MongoDB Atlas** (free cloud tier) for fastest setup.

### 1.1 Create Atlas Account
1. Go to [mongodb.com/cloud/atlas](https://mongodb.com/cloud/atlas)
2. Click "Try Free"
3. Sign up with email or Google
4. Verify your email

### 1.2 Create Cluster
1. In Atlas Dashboard, click "Create" to build a new database
2. Choose **M0 FREE TIER** (always free)
3. Select a region close to you
4. Click "Create Cluster"
5. Wait 2-3 minutes for cluster to deploy

### 1.3 Get Connection String
1. Go to **Database** section in left sidebar
2. Click **CONNECT** on your cluster
3. Choose **Drivers**
4. Copy the connection string that looks like:
   ```
   mongodb+srv://username:password@cluster0.xxxxx.mongodb.net/finora?retryWrites=true&w=majority
   ```

### 1.4 Replace .env Connection String
In `backend/.env`, replace:
```env
MONGO_URI=mongodb+srv://YOUR_USERNAME:YOUR_PASSWORD@YOUR_CLUSTER.mongodb.net/finora?retryWrites=true&w=majority
```

---

## 🔑 Step 2: Configure API Keys

You need three free accounts for the AI and file storage features:

### 2.1 Google Gemini API Key

1. Visit [Google AI Studio](https://aistudio.google.com)
2. Click "Get API Key" → "Create API Key in new project"
3. Copy your API key
4. In `backend/.env`, update:
   ```env
   GEMINI_API_KEY=your_copied_api_key_here
   ```
5. **Free Tier:** 60 requests per minute

### 2.2 Cloudinary Account (Image Upload)

1. Go to [cloudinary.com](https://cloudinary.com)
2. Click "Sign Up" → Create free account
3. In Dashboard, copy:
   - **Cloud Name**
   - **API Key**
   - **API Secret** (click "View" to reveal)
4. In `backend/.env`, update:
   ```env
   CLOUDINARY_CLOUD_NAME=your_cloud_name
   CLOUDINARY_API_KEY=your_api_key
   CLOUDINARY_API_SECRET=your_api_secret
   ```
5. **Free Tier:** Up to 25 GB storage, 25 GB bandwidth

### 2.3 Resend API Key (Email Notifications)

1. Go to [resend.com](https://resend.com)
2. Sign up and verify email
3. Go to **API Keys** section
4. Create new API key
5. In `backend/.env`, update:
   ```env
   RESEND_API_KEY=your_resend_api_key
   RESEND_MAILER_SENDER=onboarding@resend.dev  # Use their default for testing
   ```
6. **Free Tier:** 100 emails per day during development

---

## 🎨 Step 3: Verify Frontend Configuration

Frontend `.env` should already be configured:

**client/.env:**
```env
VITE_API_URL=http://localhost:8000/api
VITE_REDUX_PERSIST_SECRET_KEY=redux-persist
```

No changes needed here for local development.

---

## ▶️ Step 4: Run the Application

### Terminal 1 - Start Backend Server

```powershell
cd c:\Users\ABHISHEK\.gemini\antigravity\scratch\fianance2\Advanced-MERN-AI-Financial-SaaS-Platform\backend
npm run dev
```

**Expected output:**
```
Server is running on port 8000 in development mode
Connected to MongoDB database
```

If you see `Error connecting to MongoDB`, verify your `MONGO_URI` connection string is correct.

### Terminal 2 - Start Frontend Dev Server

```powershell
cd c:\Users\ABHISHEK\.gemini\antigravity\scratch\fianance2\Advanced-MERN-AI-Financial-SaaS-Platform\client
npm run dev
```

**Expected output:**
```
Local:   http://localhost:5173/
```

### Terminal 3 (Optional) - MongoDB Shell (if using local)

```powershell
mongosh  # Connect to local MongoDB
```

---

## 🧪 Step 5: Test the Application

1. Open browser → http://localhost:5173
2. Click "Sign Up"
3. Create account with test email
4. Login with credentials
5. Try adding a transaction
6. Test receipt upload (uses Gemini AI)
7. Check analytics dashboard

---

## 📋 All .env Variables Reference

### Backend (backend/.env)

| Variable | Example | Notes |
|----------|---------|-------|
| `NODE_ENV` | `development` | Set to "production" for deployment |
| `PORT` | `8000` | Change if 8000 is already in use |
| `BASE_PATH` | `/api` | API route prefix |
| `MONGO_URI` | `mongodb+srv://...` | Your MongoDB Atlas connection string |
| `JWT_SECRET` | `your_random_secret` | Change to random string in production |
| `JWT_EXPIRES_IN` | `15m` | JWT token expiration time |
| `JWT_REFRESH_SECRET` | `your_refresh_secret` | Change to random string in production |
| `JWT_REFRESH_EXPIRES_IN` | `7d` | Refresh token expiration |
| `GEMINI_API_KEY` | `AIzaSy...` | From Google AI Studio |
| `CLOUDINARY_CLOUD_NAME` | `your_cloud_name` | From Cloudinary Dashboard |
| `CLOUDINARY_API_KEY` | `123456789` | From Cloudinary Dashboard |
| `CLOUDINARY_API_SECRET` | `abc123xyz` | From Cloudinary Dashboard |
| `RESEND_API_KEY` | `re_xxx...` | From Resend API Keys |
| `RESEND_MAILER_SENDER` | `onboarding@resend.dev` | Email sender address |
| `FRONTEND_ORIGIN` | `http://localhost:5173` | CORS origin for frontend |

### Frontend (client/.env)

| Variable | Example | Notes |
|----------|---------|-------|
| `VITE_API_URL` | `http://localhost:8000/api` | Backend API URL |
| `VITE_REDUX_PERSIST_SECRET_KEY` | `redux-persist` | Encryption key for state persistence |

---

## 🐛 Troubleshooting

### Port 8000 Already in Use
```powershell
# Find and kill process using port 8000
netstat -ano | findstr :8000
taskkill /PID <PID> /F

# Or change PORT in backend/.env to 3000
```

### MongoDB Connection Error
- Verify your Atlas connection string is copied correctly
- Check IP whitelist in Atlas (must include your IP)
- Ensure database name exists in the connection string

### Gemini API Not Working
- Verify API key is correct in `.env`
- Check rate limits: 60 requests/minute
- Ensure you have API enabled in Google Cloud Console

### Frontend Won't Connect to Backend
- Ensure backend is running on port 8000
- Check CORS error in browser console
- Verify `FRONTEND_ORIGIN` in backend `.env` matches frontend URL

### "Cannot find module" Errors
```powershell
# Reinstall dependencies
rm -r node_modules package-lock.json
npm install
```

---

## 📦 Production Deployment

When ready to deploy, follow these steps:

1. **Build Backend:**
   ```bash
   cd backend
   npm run build
   npm start  # Runs compiled dist/index.js
   ```

2. **Build Frontend:**
   ```bash
   cd client
   npm run build
   # Upload `dist/` folder to hosting (Vercel, Netlify, etc.)
   ```

3. **Environment Setup:**
   - Generate strong random JWT secrets
   - Use production MongoDB Atlas cluster
   - Update FRONTEND_ORIGIN to your domain
   - Set NODE_ENV=production

4. **Deploy Options:**
   - **Backend:** Railway, Render, Vercel (with serverless)
   - **Frontend:** Vercel, Netlify, GitHub Pages
   - **Database:** MongoDB Atlas (free tier)

---

## 📚 Project Links

- **GitHub Repository:** https://github.com/abhishekbarve9370621566/Advanced-MERN-AI-Financial-SaaS-Platform
- **API Documentation:** See `backend/src/routes/` for endpoints
- **Original Project:** https://github.com/TechWithEmmaYT/Advanced-MERN-AI-Financial-SaaS-Platform

---

## ✨ Next Steps

1. ✅ Set up MongoDB Atlas
2. ✅ Get API keys from Gemini, Cloudinary, Resend
3. ✅ Update backend/.env with all credentials
4. ✅ Run `npm run dev` in both backend & frontend
5. ✅ Test the application
6. ✅ Customize branding (optional)
7. ✅ Deploy to production

---

**You're all set!** 🎉 Your local development environment is ready to use. Happy coding!
