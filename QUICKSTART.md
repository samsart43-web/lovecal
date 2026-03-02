# 🚀 Student OS - Quick Start Guide

## Project Overview

Student OS is a **full-stack productivity dashboard** designed for students. It combines modern web technologies with beautiful UI to help manage tasks, focus sessions, study planning, and personal wellness.

### ✨ What's Included

✅ **Complete React Frontend** - Built with Vite, Tailwind CSS, and Context API  
✅ **Express Backend** - RESTful API with MongoDB integration  
✅ **Authentication** - JWT-based login/signup with password hashing  
✅ **Dark/Light Mode** - System theme detection with toggle  
✅ **Fully Responsive** - Mobile, tablet, and desktop optimized  
✅ **Production-Ready** - Error handling, loading states, validation  

---

## 🔧 Installation

### Step 1: Install Dependencies

**Backend:**
```bash
cd server
npm install
```

**Frontend:**
```bash
cd client
npm install
```

### Step 2: Configure Environment

**Backend (.env):**
```bash
cd server
cat > .env << EOF
MONGODB_URI=mongodb://localhost:27017/student-os
JWT_SECRET=your-super-secret-key-change-in-production
PORT=5000
NODE_ENV=development
EOF
```

**Frontend (.env.local):**
```bash
cd ../client
cat > .env.local << EOF
VITE_API_URL=http://localhost:5000/api
EOF
```

### Step 3: Start MongoDB

**Option 1: Local MongoDB**
```bash
# Make sure MongoDB is running on your system
mongod
```

**Option 2: MongoDB Atlas (Cloud)**
- Replace MONGODB_URI in server/.env with your Atlas connection string

### Step 4: Run the Application

**Terminal 1 - Backend:**
```bash
cd server
npm run dev
```
Backend runs on: `http://localhost:5000`

**Terminal 2 - Frontend:**
```bash
cd client
npm run dev
```
Frontend runs on: `http://localhost:5173`

### Step 5: Open in Browser

Go to: **http://localhost:5173**

---

## 📚 Features Overview

### 🔐 Authentication
- **Sign Up** - Create new account with name, email, password
- **Login** - Secure JWT-based authentication
- **Persistent Sessions** - Tokens stored in localStorage
- **Auto Logout** - Session invalidation on logout

### 📝 Smart To-Do System
- ➕ Add tasks with title, category, priority, due date
- ✏️ Edit task details inline
- ✅ Mark complete with smooth animation
- 🗂️ Filter by: All, Active, Completed
- 📊 Progress percentage display
- **Categories**: Study, Homework, Exam, Personal
- **Priorities**: Low, Medium, High

### ⏰ Focus Timer (Pomodoro)
- ⏱️ 25-min focus + 5-min break cycle
- 🎨 Beautiful circular progress indicator
- 🔧 Custom time duration support
- 📢 Sound notification when complete
- 📈 Session counter for motivation
- 🎯 Quick preset options (25min, 45min)

### 💧 Water Tracker
- 💧 Visual glass tracker with progress ring
- 🎯 Customizable daily goal
- 📱 Click glass to log water intake
- 🔄 Auto-reset daily
- 💡 Hydration tips and health facts

### 📅 Study Planner Calendar
- 📆 Monthly calendar view
- ➕ Add study sessions to specific dates
- 🕐 Set start/end times per session
- 📝 Add subject and notes
- 👁️ View all sessions for selected date
- 🎨 Color-coded scheduled days (green)

### 🌍 World Clock
- 🌐 Real-time global time display
- ➕ Add up to 3 custom cities
- 🔄 1-second updates
- 🗑️ Remove cities as needed
- 📍 Support for major timezones worldwide
- 🤝 Perfect for coordinating with global teams

### 📊 Analytics Dashboard
- 📈 Weekly task completion stats
- ⏳ Total focus hours this week
- 🔥 Study streak counter
- 📊 Completion rate percentage
- 📉 Visual progress charts
- 🎯 Performance metrics

### 🌓 Dark/Light Mode
- 🌙 System preference detection
- 🔘 Manual toggle in navigation
- 💾 Preference saved to localStorage
- ✨ Smooth transitions between themes

---

## 📁 Project Structure

```
student-os/
├── 📁 server/
│   ├── src/
│   │   ├── models/           # Database schemas (User, Task, etc)
│   │   ├── routes/           # API endpoints
│   │   ├── middleware/       # Auth & validation
│   │   ├── controller/       # Business logic (future)
│   │   └── server.js         # Main app entry
│   ├── package.json
│   ├── .env                  # Config (MONGODB, JWT, PORT)
│   └── README.md
│
└── 📁 client/
    ├── src/
    │   ├── components/       # Reusable UI components
    │   │   ├── TodoSystem.jsx
    │   │   ├── FocusTimer.jsx
    │   │   ├── WaterReminder.jsx
    │   │   ├── StudyPlannerCalendar.jsx
    │   │   ├── WorldClock.jsx
    │   │   ├── AnalyticsDashboard.jsx
    │   │   ├── AuthForm.jsx
    │   │   ├── Navigation.jsx
    │   │   ├── Sidebar.jsx
    │   │   ├── MainApp.jsx
    │   │   └── ThemeToggle.jsx
    │   │
    │   ├── pages/            # Full page components
    │   │   ├── AuthPage.jsx
    │   │   ├── Dashboard.jsx
    │   │   ├── TasksPage.jsx
    │   │   ├── FocusPage.jsx
    │   │   ├── WaterPage.jsx
    │   │   ├── CalendarPage.jsx
    │   │   └── ClockPage.jsx
    │   │
    │   ├── context/          # Global state
    │   │   ├── AuthContext.jsx    # User auth state
    │   │   └── ThemeContext.jsx   # Dark/light mode
    │   │
    │   ├── api/              # API calls
    │   │   └── client.js     # All API endpoints
    │   │
    │   ├── App.jsx           # Main app wrapper
    │   ├── main.jsx          # React entry point
    │   └── index.css         # Global styles + Tailwind
    │
    ├── package.json
    ├── .env.local            # Frontend API URL
    ├── vite.config.js        # Vite bundler config
    ├── tailwind.config.js    # Tailwind CSS config
    ├── postcss.config.js     # PostCSS config
    └── index.html            # HTML template
```

---

## 🎨 Design System

### Color Palette
- **Primary**: Indigo (#4F46E5)
- **Secondary**: Purple (#9333EA)
- **Accents**: Orange, Cyan, Green
- **Backgrounds**: Soft pastels in light mode, grays in dark mode
- **Text**: Dark gray on light, light gray on dark

### Components
- **Rounded corners**: 8-12px (xl/2xl)
- **Shadows**: Subtle elevation
- **Animations**: Smooth 300-500ms transitions
- **Typography**: System font stack with 16px base

---

## 🔌 API Endpoints

### Authentication
```
POST   /api/auth/register      # Create account
POST   /api/auth/login         # Login user
```

### Tasks (All require auth header)
```
GET    /api/tasks              # Get all tasks
POST   /api/tasks              # Create task
PUT    /api/tasks/:id          # Update task
DELETE /api/tasks/:id          # Delete task
GET    /api/tasks/category/:c  # Filter by category
```

### Focus Sessions
```
POST   /api/focus              # Start session
PUT    /api/focus/:id/complete # End session
GET    /api/focus              # Get all sessions
GET    /api/focus/stats/today  # Today's stats
```

### Water Tracker
```
GET    /api/water              # Get tracker
POST   /api/water/drink        # Log glass
PUT    /api/water/goal         # Set daily goal
```

### Study Planner
```
GET    /api/planner/:date      # Get sessions for date
POST   /api/planner            # Add session
PUT    /api/planner/:id        # Update session
DELETE /api/planner/:id/:sid   # Delete session
```

### Analytics
```
GET    /api/analytics          # Get weekly stats
```

### User
```
GET    /api/user/profile       # Get profile
PUT    /api/user/profile       # Update profile
```

---

## 🚀 Building for Production

### Frontend Build
```bash
cd client
npm run build
```
Creates optimized build in `client/dist/`

### Backend Deploy
1. Set production environment variables:
   ```
   MONGODB_URI=your-production-db
   JWT_SECRET=strong-random-secret
   NODE_ENV=production
   PORT=5000
   ```

2. Deploy to: Vercel, Netlify (frontend) + Heroku, Railway, Render (backend)

---

## 🔐 Security Checklist

✅ Passwords hashed with bcryptjs (10 rounds)  
✅ JWT tokens with 30-day expiration  
✅ CORS enabled for frontend origin  
✅ Input validation on all endpoints  
✅ User data isolation (userId checks)  
✅ Secure headers with helmet  
✅ Environment variables for secrets  
✅ No credentials in code/git  

---

## 🐛 Troubleshooting

### MongoDB Connection Error
```
// Check if MongoDB is running
// Windows: mongod from cmd
// macOS: brew services start mongodb-community
// Linux: sudo systemctl start mongod
```

### CORS Error
```
// Make sure backend is running on 5000
// Frontend .env.local has correct VITE_API_URL
```

### Port Already in Use
```bash
# Kill process on port 5000
# Windows: netstat -ano | findstr :5000
# macOS/Linux: lsof -i :5000 | kill -9 <PID>
```

### Clear Cache Issues
```bash
# Frontend
rm -rf client/node_modules client/package-lock.json
cd client && npm install

# Backend
rm -rf server/node_modules server/package-lock.json
cd server && npm install
```

---

## 📖 Next Steps

1. **Explore Features** - Try all features in the app
2. **Customize** - Modify colors, add new features
3. **Deploy** - Push to production
4. **Extend** - Add: OAuth login, notifications, export, mobile app
5. **Share** - Show friends and get feedback!

---

## 🎓 Learning Resources

- **React**: https://react.dev
- **Tailwind CSS**: https://tailwindcss.com
- **Express**: https://expressjs.com
- **MongoDB**: https://mongodb.com
- **Vite**: https://vitejs.dev

---

## 💡 Tips for Success

✨ **UI Tips**
- Use keyboard shortcuts (Enter to submit)
- Click dates on calendar to add sessions
- Dark mode for late night studying

🎯 **Productivity Tips**
- Use Pomodoro (25+5) for best focus
- Set realistic task deadlines
- Review analytics weekly
- Stay hydrated (drink water!)

📱 **Mobile Tips**
- All features work on mobile
- Use landscape for calendar
- Notifications will alert you (when added)

---

## 📞 Support & Feedback

Found a bug? Have a feature request?
- Create an issue on GitHub
- Email: support@studentos.dev
- Discord: Join our community

---

**Happy studying! 🚀 Make Student OS your productivity companion.**

Last Updated: February 2026
Version: 1.0.0
