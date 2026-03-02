# 📚 Student OS - Complete Documentation

## 🎉 Welcome to Student OS!

A **modern, full-stack productivity dashboard** built specifically for students. Combine task management, focus tracking, study planning, and wellness features in one beautiful application.

---

## 📦 What You Get

### Frontend ✨
- **React 19** - Latest React with hooks
- **Vite** - Lightning-fast dev server
- **Tailwind CSS** - Beautiful utility-first styling
- **Lucide Icons** - 344+ professional icons
- **Context API** - Global state management
- **Dark Mode** - System detection + manual toggle
- **Fully Responsive** - Mobile, tablet, desktop

### Backend 🔧
- **Express.js** - Lightweight web framework
- **MongoDB** - NoSQL database
- **Mongoose** - Database modeling
- **JWT** - Secure authentication
- **bcryptjs** - Password hashing
- **CORS** - Cross-origin requests
- **Helmet** - Security headers

### Features 🌟
1. **Authentication** - Secure signup/login
2. **Task Management** - Create, edit, delete with categories
3. **Pomodoro Timer** - 25min focus + 5min breaks
4. **Water Tracker** - Daily hydration reminder
5. **Study Planner** - Monthly calendar scheduling
6. **World Clock** - Multi-timezone tracking
7. **Analytics** - Weekly performance stats
8. **Dark Mode** - Eye-friendly night mode

---

## 🚀 Getting Started (5 minutes)

### 1. Prerequisites
- Node.js 16+ ([Download](https://nodejs.org))
- MongoDB ([Local](https://mongodb.com/try/download/community) or [Atlas](https://mongodb.com/cloud/atlas))
- Git ([Download](https://git-scm.com))

### 2. Clone & Install
```bash
# Navigate to gr folder
cd gr

# Backend setup
cd server
npm install

# Frontend setup
cd ../client
npm install
```

### 3. Configure
**server/.env**
```env
MONGODB_URI=mongodb://localhost:27017/student-os
JWT_SECRET=super-secret-key-change-in-production
PORT=5000
```

**client/.env.local**
```env
VITE_API_URL=http://localhost:5000/api
```

### 4. Start Services
**Terminal 1 - MongoDB** (if local)
```bash
mongod
```

**Terminal 2 - Backend**
```bash
cd server
npm run dev
# Runs on http://localhost:5000
```

**Terminal 3 - Frontend**
```bash
cd client
npm run dev
# Runs on http://localhost:5173
```

### 5. Open App
Visit: **http://localhost:5173**

---

## 🎯 Feature Guide

### 🔐 Authentication
<img src="docs/auth.png" width="300" />

**How to use:**
1. Click "Sign Up" to create account
2. Enter name, email, password
3. Password is encrypted with bcryptjs
4. Login to get JWT token
5. Token automatically saved (30 days)

**Tech:** JWT + bcryptjs + MongoDB

---

### 📝 Task Management
<img src="docs/tasks.png" width="300" />

**Features:**
- ➕ Add tasks with title + description
- 🏷️ Categorize: Study, Homework, Exam, Personal
- 📊 Set priority: Low, Medium, High
- 📅 Add due dates
- ✅ Mark complete (smooth animation)
- 🔄 Edit/delete inline
- 📈 Progress bar shows completion %

**Pro Tips:**
- Use High priority for urgent tasks
- Group by category for organization
- Filter by status: All, Active, Complete

**Tech:** React State + MongoDB + REST API

---

### ⏱️ Pomodoro Focus Timer
<img src="docs/timer.png" width="300" />

**How it works:**
1. **Focus Phase**: 25 minutes of deep work
2. **Break Phase**: 5 minutes to rest
3. **Repeat**: Continue cycles for productivity

**Features:**
- 🎨 Beautiful circular progress indicator
- 🔧 Custom duration support (15, 45 mins, etc)
- 📢 Sound notification when timer completes
- 📈 Session counter for daily motivation
- ⚡ Quick presets: 25min, 45min

**Science:** Based on Pomodoro Technique

**Pro Tips:**
- Turn off all notifications during focus
- Log each session to database  
- Take water breaks to stay hydrated
- After 4 sessions, take 15-30 min break

**Tech:** React Hooks + Web Audio API + MongoDB

---

### 💧 Water Tracker
<img src="docs/water.png" width="300" />

**Features:**
- 💧 Visual glass tracker (customizable goal)
- 🎨 Progress ring animation
- 📊 Percentage display
- 🎯 Set daily goal (8, 10, 12+ glasses)
- 📱 Click glass to log water intake
- 🔄 Auto-resets daily at midnight

**Benefits of hydration:**
- ✅ Improves focus by 30%
- ✅ Reduces fatigue
- ✅ Enhances mood
- ✅ Better cognitive function
- ✅ Boosts energy levels

**Pro Tips:**
- Log after each focus session
- Set reminders at specific times
- Track on mobile for on-the-go updates

**Tech:** React Context + LocalStorage + MongoDB

---

### 📅 Study Planner Calendar
<img src="docs/calendar.png" width="300" />

**Features:**
- 📆 Monthly calendar view
- ➕ Click date to add study session
- 🕐 Set start/end times
- 📝 Add subject name & notes
- 👁️ View all sessions for date
- 🎨 Green highlight shows scheduled days
- 🗑️ Delete sessions anytime

**How to plan:**
1. Click date on calendar
2. Click "Add Study Session"
3. Fill in title, subject, times
4. Sessions appear in list for that date
5. Review weekly schedule

**Pro Tips:**
- Plan week in advance on Sunday
- Space out intensive subjects
- Include buffer time between sessions
- Review before major exams

**Tech:** React Calendar + MongoDB

---

### 🌍 World Clock
<img src="docs/clock.png" width="300" />

**Features:**
- 🌐 Real-time global time display
- ➕ Add up to 3 custom cities
- 🔄 Updates every second
- 🗑️ Remove cities as needed
- 📍 Support for 12+ timezones

**Supported Cities:**
- USA: New York, Los Angeles
- Europe: London, Paris
- Asia: Tokyo, Hong Kong, Singapore, Dubai
- Oceania: Sydney, Bangkok

**Use Cases:**
- 🤝 Coordinate with teammates worldwide
- 📞 Schedule online classes
- 💼 Plan global study groups
- ⏰ Never miss meetings

**Pro Tips:**
- Add your friends' timezones
- Use for online study groups
- Plan meeting times instantly

**Tech:** Intl.DateTimeFormat API + React State

---

### 📊 Analytics Dashboard
<img src="docs/analytics.png" width="300" />

**Metrics tracked:**
- 📈 Tasks completed this week
- ⏳ Total focus hours this week  
- 🔥 Study streak counter
- 📊 Completion rate (%)
- 🎯 Performance trends

**How it helps:**
- See your productivity trends
- Identify best study times
- Track progress toward goals
- Stay motivated with streaks

**Pro Tips:**
- Review analytics weekly
- Set weekly task targets
- Challenge yourself to beat last week
- Share progress with study group

**Tech:** REST API + Chart.js + React

---

### 🌓 Dark Mode
<img src="docs/darkmode.png" width="300" />

**Feature:**
- 🌙 Automatic detection (system preference)
- 🔘 Manual toggle in navbar
- 💾 Preference saved to localStorage
- ✨ Smooth transitions
- 👁️ Eye-friendly colors

**Benefits:**
- Easier on eyes at night
- Reduces blue light
- Saves battery on OLED screens
- Professional dark theme

**Tech:** CSS Dark Mode + Context API

---

## 📚 API Documentation

### Port: 5000

### Authentication
```bash
# Register
POST /api/auth/register
Body: { name, email, password }
Response: { token, user }

# Login
POST /api/auth/login
Body: { email, password }
Response: { token, user }
```

### Tasks (require Authorization header)
```bash
# Get all
GET /api/tasks
Header: "Authorization: Bearer {token}"

# Create
POST /api/tasks
Body: { title, description, category, priority, dueDate }

# Update
PUT /api/tasks/:id
Body: { any fields to update }

# Delete
DELETE /api/tasks/:id

# By category
GET /api/tasks/category/Study
```

### Focus Sessions
```bash
# Create session
POST /api/focus
Body: { duration, sessionType: 'focus'|'break' }

# Complete session
PUT /api/focus/:id/complete

# Get all sessions
GET /api/focus

# Get today's stats
GET /api/focus/stats/today
Response: { totalMinutes, sessionCount }
```

### Water Tracker
```bash
# Get tracker
GET /api/water
Response: { waterGoal, glassesCompleted, percentage }

# Log drink
POST /api/water/drink

# Set goal
PUT /api/water/goal
Body: { waterGoal: 10 }
```

### Study Planner
```bash
# Get sessions for date
GET /api/planner/2024-02-28

# Add session
POST /api/planner
Body: { date, session: { title, subject, startTime, endTime } }

# Update session
PUT /api/planner/:id
Body: { sessionId, updatedSession }

# Delete session
DELETE /api/planner/:plannerId/:sessionId
```

### Analytics
```bash
# Get weekly stats
GET /api/analytics
Response: {
  tasksCompleted,
  totalTasks,
  focusHours,
  studyStreak,
  thisWeekCount
}
```

### User
```bash
# Get profile
GET /api/user/profile

# Update profile
PUT /api/user/profile
Body: { name, email }
```

---

## 🎨 Design System

### Colors
```
Light Mode:
- Primary: #4F46E5 (Indigo)
- Secondary: #9333EA (Purple)
- Background: #F9FAFB (Light Gray)
- Text: #1F2937 (Dark Gray)

Dark Mode:
- Primary: #4F46E5 (Indigo)
- Secondary: #9333EA (Purple)
- Background: #111827 (Dark Gray)
- Text: #F3F4F6 (Light Gray)
```

### Components
- **Border Radius**: 8-12px (rounded to xl)
- **Shadows**: Subtle (hover state)
- **Animations**: 300-500ms smooth transitions
- **Spacing**: 8px grid system
- **Typography**: System font stack, 16px base

### Icons
- Lucide React: 344+ professional icons
- Consistent sizing: 16-24px
- Always filled or stroke

---

## 🗂️ Project Structure

```
student-os/
│
├── 📁 server/
│   ├── src/
│   │   ├── models/          # MongoDB schemas
│   │   │   ├── User.js      # Users
│   │   │   ├── Task.js      # Tasks
│   │   │   ├── FocusSession.js
│   │   │   └── StudyPlanner.js
│   │   ├── routes/          # API endpoints
│   │   │   ├── auth.js
│   │   │   ├── tasks.js
│   │   │   ├── focus.js
│   │   │   ├── water.js
│   │   │   ├── planner.js
│   │   │   ├── analytics.js
│   │   │   └── user.js
│   │   ├── middleware/
│   │   │   └── auth.js      # JWT verification
│   │   └── server.js        # Express app
│   ├── package.json
│   ├── .env
│   └── README.md
│
├── 📁 client/
│   ├── src/
│   │   ├── components/      # Reusable components
│   │   │   ├── TodoSystem.jsx          # Task management
│   │   │   ├── FocusTimer.jsx          # Pomodoro
│   │   │   ├── WaterReminder.jsx       # Hydration
│   │   │   ├── StudyPlannerCalendar.jsx# Calendar
│   │   │   ├── WorldClock.jsx          # Timezones
│   │   │   ├── AnalyticsDashboard.jsx  # Stats
│   │   │   ├── TaskItem.jsx            # Single task
│   │   │   ├── AuthForm.jsx            # Login/signup
│   │   │   ├── Navigation.jsx          # Top navbar
│   │   │   ├── Sidebar.jsx             # Left menu
│   │   │   ├── MainApp.jsx             # App wrapper
│   │   │   └── ThemeToggle.jsx         # Dark/light
│   │   ├── pages/           # Full screens
│   │   │   ├── AuthPage.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   ├── TasksPage.jsx
│   │   │   ├── FocusPage.jsx
│   │   │   ├── WaterPage.jsx
│   │   │   ├── CalendarPage.jsx
│   │   │   └── ClockPage.jsx
│   │   ├── context/         # Global state
│   │   │   ├── AuthContext.jsx
│   │   │   └── ThemeContext.jsx
│   │   ├── api/
│   │   │   └── client.js    # API methods
│   │   ├── App.jsx          # Root component
│   │   ├── main.jsx         # Entry point
│   │   └── index.css        # Tailwind + styles
│   ├── public/              # Static assets
│   ├── package.json
│   ├── .env.local
│   ├── vite.config.js
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   ├── eslint.config.js
│   └── index.html
│
├── README.md
├── QUICKSTART.md
├── DEPLOYMENT.md
└── .gitignore
```

---

## 🔐 Security Features

✅ **Password Security**
- bcryptjs 10-round hashing
- No plaintext storage
- Secure comparison

✅ **Authentication**
- JWT tokens (30-day expiration)
- Token validation on all routes
- Logout clears tokens

✅ **Data Protection**
- User isolation (userId checks)
- CORS whitelist (frontend only)
- HTTPS ready
- Environment variables for secrets

✅ **API Security**
- Helmet security headers
- Input validation
- Rate limiting ready
- SQL injection protection (MongoDB)

---

## 🚀 Deployment

### Quick Deploy

**Frontend to Vercel:**
```bash
npm i -g vercel
cd client
vercel
```

**Backend to Railway:**
1. Connect GitHub repo
2. Add environment variables
3. Deploy

See [DEPLOYMENT.md](DEPLOYMENT.md) for detailed guides.

---

## 📊 Database Schema

### User
```javascript
{
  name: String,
  email: String (unique),
  password: String (hashed),
  waterGoal: Number,
  waterTracker: [{
    date: Date,
    glassesCompleted: Number
  }],
  studyStreak: Number,
  lastActiveDate: Date,
  createdAt: Date,
  updatedAt: Date
}
```

### Task
```javascript
{
  userId: ObjectId (ref User),
  title: String,
  description: String,
  category: Enum (Study|Homework|Exam|Personal),
  priority: Enum (Low|Medium|High),
  dueDate: Date,
  completed: Boolean,
  completedAt: Date,
  createdAt: Date,
  updatedAt: Date
}
```

### FocusSession
```javascript
{
  userId: ObjectId,
  duration: Number (minutes),
  started: Date,
  ended: Date,
  completed: Boolean,
  sessionType: Enum (focus|break)
}
```

### StudyPlanner
```javascript
{
  userId: ObjectId,
  date: Date,
  sessions: [{
    title: String,
    subject: String,
    startTime: Date,
    endTime: Date,
    notes: String
  }]
}
```

---

## 🐛 Troubleshooting

| Problem | Solution |
|---------|----------|
| Can't connect to MongoDB | Make sure mongod is running or check Atlas URI |
| CORS error | Verify VITE_API_URL in .env.local matches backend |
| Tasks not saving | Check backend console for API errors |
| Dark mode not working | Clear browser cache and localStorage |
| Timer sound not playing | Enable audio in browser permissions |
| Focus timer stuck | Refresh page, clear browser cache |
| Can't login | Verify email/password correct, check backend errors |

---

## 💡 Tips for Students

### Productivity
- 🍅 Use Pomodoro (25+5) technique
- 💧 Drink water during breaks
- 📝 Write tasks immediately
- 🎯 Set realistic daily goals
- 📊 Review analytics weekly

### Study
- 📚 Plan study sessions monthly
- ⏰ Schedule consistent times
- 🤝 Join study groups (with World Clock)
- 📅 Mark exam dates in advance
- 🔄 Track progress over time

### Health
- 💪 Drink 8+ glasses daily
- 🧘 Take breaks every hour
- 👁️ Use dark mode at night
- 🏃 Move during break time
- 😴 Respect sleep schedule

---

## 🔮 Future Features

- [ ] Google/GitHub OAuth
- [ ] Email notifications
- [ ] Export analytics as PDF
- [ ] Collaborative study groups
- [ ] AI study recommendations
- [ ] Mobile app (React Native)
- [ ] Voice commands
- [ ] Habit tracking
- [ ] Study resources library
- [ ] Integration with Google Calendar

---

## 📝 License

MIT License - Free to use for any purpose

---

## 🤝 Contributing

Found a bug or have a feature idea?
1. Create an issue on GitHub
2. Fork and make changes
3. Submit pull request

---

## 📞 Support

- 📧 Email: support@studentos.dev
- 💬 Discord: [Join community]
- 🐛 GitHub Issues: [Report bugs]
- 📖 Documentation: [Read docs]

---

## 🙏 Credits

Built with ❤️ for students by:
- React & Vite teams
- Tailwind CSS
- MongoDB
- Express.js community

---

## 📈 Roadmap

**Q1 2026**
- Launch v1.0 (Current)
- User beta testing
- Mobile UI refinement

**Q2 2026**
- OAuth integration
- Push notifications
- Advanced analytics

**Q3 2026**
- Mobile app release
- Collaborative features
- AI recommendations

**Q4 2026**
- 50K+ users goal
- Enterprise features
- API marketplace

---

**Happy studying! Make your productivity count.** 🚀

Last Updated: February 28, 2026  
Version: 1.0.0  
Status: ✅ Ready for Production
