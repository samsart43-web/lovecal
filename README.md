# Student OS - Full-Stack Productivity Dashboard

A modern, responsive web application for students built with React, Node.js, MongoDB, and Tailwind CSS.

## Features

### 🔐 Authentication
- Email & password registration/login
- JWT token-based auth
- Persistent user sessions
- Private data isolation

### 📝 Smart To-Do System
- Create, edit, delete tasks
- Categories: Study, Homework, Exam, Personal
- Priority levels: Low, Medium, High
- Due dates & reminders
- Progress tracking
- Task completion animations

### 🎯 Focus Timer (Pomodoro)
- 25 min focus + 5 min break
- Custom time options
- Session counter
- Notification sound
- Session history saved to profile

### 📅 Study Planner Calendar
- Monthly calendar view
- Add study sessions to dates
- View all tasks for selected day
- Time slot management
- Color-coded scheduled days

### 💧 Water Reminder
- Daily water intake tracking
- Customizable daily goal
- Progress ring animation
- Visual glass tracker
- Health tips and reminders

### 🌍 World Clock
- Current time display
- Add up to 3 custom cities
- Real-time updates
- Timezone support
- Meeting coordination tool

### 📊 Analytics Dashboard
- Weekly task completion stats
- Total focus hours
- Study streak counter
- Completion rate charts
- Progress visualization

## Tech Stack

### Frontend
- **React 19** - UI library
- **Tailwind CSS** - Utility-first styling
- **Vite** - Build tool
- **Lucide React** - Icon library
- **Context API** - State management

### Backend
- **Node.js** - JavaScript runtime
- **Express** - Web framework
- **MongoDB** - NoSQL database
- **JWT** - Authentication
- **bcryptjs** - Password hashing
- **Mongoose** - ODM

## Setup Instructions

### Prerequisites
- Node.js (v16+)
- MongoDB (local or cloud)
- npm or yarn

### Installation

1. **Clone and install backend:**
```bash
cd server
npm install
```

2. **Configure backend:**
```bash
# Create .env file with MongoDB URI and JWT secret
echo "MONGODB_URI=mongodb://localhost:27017/student-os" > .env
echo "JWT_SECRET=your-secret-key" >> .env
echo "PORT=5000" >> .env
```

3. **Start MongoDB:**
```bash
# Make sure MongoDB is running (local or Atlas URI in .env)
```

4. **Start backend server:**
```bash
npm run dev
```

5. **In another terminal, setup frontend:**
```bash
cd client
npm install
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

6. **Start dev server:**
```bash
npm run dev
```

7. **Open browser:**
```
http://localhost:5173
```

## Project Structure

```
student-os/
├── server/
│   ├── src/
│   │   ├── models/         # Database schemas
│   │   ├── routes/         # API endpoints
│   │   ├── middleware/     # Auth & error handling
│   │   ├── controller/     # Business logic
│   │   └── server.js       # Entry point
│   ├── package.json
│   ├── .env              # Environment variables
│   └── README.md
│
└── client/
    ├── src/
    │   ├── components/     # Reusable components
    │   ├── pages/          # Page components
    │   ├── context/        # Auth & theme context
    │   ├── api/            # API client
    │   ├── App.jsx
    │   └── main.jsx
    ├── package.json
    ├── vite.config.js
    ├── tailwind.config.js
    ├── .env.local        # Frontend config
    └── index.html
```

## API Documentation

### Authentication
- `POST /api/auth/register` - Create account
- `POST /api/auth/login` - Login user

### Tasks
- `GET /api/tasks` - Get all tasks
- `POST /api/tasks` - Create task
- `PUT /api/tasks/:id` - Update task
- `DELETE /api/tasks/:id` - Delete task

### Focus Sessions
- `POST /api/focus` - Start session
- `PUT /api/focus/:id/complete` - End session
- `GET /api/focus` - Get all sessions
- `GET /api/focus/stats/today` - Today's stats

### Water Tracker
- `GET /api/water` - Get tracker
- `POST /api/water/drink` - Log intake
- `PUT /api/water/goal` - Set goal

### Study Planner
- `GET /api/planner/:date` - Get sessions
- `POST /api/planner` - Add session

### Analytics
- `GET /api/analytics` - Get stats

### User
- `GET /api/user/profile` - Get profile
- `PUT /api/user/profile` - Update profile

## Building for Production

### Frontend
```bash
cd client
npm run build
```

### Backend
Create production `.env` with:
```
MONGODB_URI=your-production-mongodb-url
JWT_SECRET=strong-random-secret
PORT=5000
NODE_ENV=production
```

Then deploy to your server/cloud platform.

## Features Roadmap

- [ ] Google/GitHub OAuth
- [ ] Dark mode (✓ Implemented)
- [ ] Mobile app (React Native)
- [ ] Collaborative study sessions
- [ ] AI-powered study recommendations
- [ ] Export analytics as PDF
- [ ] Email notifications
- [ ] Two-factor authentication
- [ ] Study group functionality
- [ ] Integration with calendar apps

## Performance Optimizations

- Code splitting for components
- Lazy loading of routes
- Optimized images and assets
- Caching strategies
- Efficient re-renders with React.memo
- Debounced search and input

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Security Features

- Password hashing with bcryptjs
- JWT token validation
- CORS protection
- Input validation
- HTTPS ready
- Secure session management

## UI/UX Highlights

- Soft pastel color palette
- Smooth animations & transitions
- Rounded corners on all elements
- Dark/light mode toggle
- Mobile-first responsive design
- Accessibility features (ARIA labels)
- Loading states & error handling

## Contributing

Feel free to submit issues and enhancement requests!

## License

MIT License - feel free to use this project for your studies!

## Support

For questions or issues, please create an issue in the repository.

---

Made with ❤️ for students by students
