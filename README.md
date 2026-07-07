# ?? MyFinance - Personal AI Financial Management Platform

An advanced full-stack financial management application built with the MERN stack (MongoDB, Express, React, Node.js) and powered by Google Gemini AI for intelligent financial insights.

---

## ?? License & Attribution

This project is based on the [Advanced MERN AI Financial SaaS Platform](https://github.com/TechWithEmmaYT/Advanced-MERN-AI-Financial-SaaS-Platform) by [TechWithEmmaYT](https://github.com/TechWithEmmaYT).

**Original License:** This code is licensed for commercial use only with a license, and is free for personal use. See [TECHWITHEMMA-LICENSE.md](./TECHWITHEMMA-LICENSE.md) for full details.

---

## ? Key Features

* **?? Secure Authentication** - Email + Password with JWT tokens
* **?? Transaction Management** - Create, edit, and organize financial transactions
* **?? Receipt Scanning** - AI-powered receipt upload and parsing via Google Gemini
* **?? Advanced Analytics** - Beautiful charts and insights using MongoDB aggregation pipelines
* **?? Recurring Transactions** - Automated recurring transaction handling with cron jobs
* **?? Intelligent Reports** - Auto-generated monthly financial reports with AI-powered insights
* **?? Bulk Import** - CSV transaction import for easy data migration
* **?? Search & Filter** - Advanced filtering, search, and pagination
* **?? Bulk Operations** - Delete, duplicate, and manage multiple transactions
* **??? Profile Management** - Upload and store profile photos via Cloudinary
* **?? Responsive Design** - Full-stack TypeScript with modern React 18 & Tailwind CSS

---

## ??? Tech Stack

### Backend
- **Runtime:** Node.js with Express 5.x
- **Database:** MongoDB with Mongoose
- **Authentication:** JWT with Passport.js
- **Language:** TypeScript
- **AI:** Google Gemini API

### Frontend
- **Framework:** React 18 with Vite
- **Styling:** Tailwind CSS v4
- **State Management:** Redux Toolkit
- **Charts:** Recharts for data visualization

---

## ?? Prerequisites

- Node.js v24+
- npm v11+
- MongoDB (local or Atlas)
- Google Gemini API Key
- Cloudinary Account
- Resend API Key

---

## ?? Quick Start

### 1. Install Dependencies

```bash
cd backend && npm install
cd ../client && npm install
```

### 2. Configure Environment Variables

Create `.env` files in both `backend/` and `client/` directories with your API keys and database connection details.

### 3. Start MongoDB & Development Servers

```bash
# Terminal 1: Backend
cd backend && npm run dev

# Terminal 2: Frontend
cd client && npm run dev
```

---

## ?? Build for Production

```bash
cd backend && npm run build && npm start
cd ../client && npm run build && npm run preview
```

---

## ?? License

Original work licensed under [TECHWITHEMMA-LICENSE.md](./TECHWITHEMMA-LICENSE.md). This is a customized portfolio version.

---

## ?? Acknowledgments

Built upon the foundation provided by [TechWithEmmaYT](https://github.com/TechWithEmmaYT).

---

**Happy coding!** ??
