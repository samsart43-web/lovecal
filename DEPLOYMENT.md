# 🎯 Student OS - Deployment Guide

Complete guide to deploy Student OS to production.

## Deployment Options

### Frontend Deployment

#### Option 1: Vercel (Recommended)
```bash
# Install Vercel CLI
npm i -g vercel

# Login
vercel login

# Deploy from client folder
cd client
vercel
```

#### Option 2: Netlify
```bash
# Build first
cd client
npm run build

# Drag dist/ folder to Netlify
# Or use Netlify CLI:
npm install -g netlify-cli
netlify deploy --prod --dir=dist
```

#### Option 3: GitHub Pages
```bash
# Add to package.json
"homepage": "https://yourusername.github.io/student-os"

# Build and deploy
npm run build
cd build
git init
git add .
git commit -m "Deploy"
git push
```

### Backend Deployment

#### Option 1: Railway (Easiest)
1. Push code to GitHub
2. Go to https://railway.app
3. New Project → GitHub repo
4. Add environment variables
5. Deploy automatically

#### Option 2: Render
1. Create account at https://render.com
2. New Web Service → GitHub repo
3. Configure build & start commands
4. Add environment variables
5. Deploy

#### Option 3: Heroku
```bash
# Install Heroku CLI
npm i -g heroku

# Login
heroku login

# Create app
heroku create student-os-api

# Add MongoDB URI
heroku config:set MONGODB_URI=mongodb+srv://...

# Deploy
git push heroku main
```

#### Option 4: AWS EC2
```bash
# Launch Ubuntu 22.04 instance
# SSH into server
ssh -i key.pem ubuntu@instance-ip

# Install Node
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt-get install -y npm

# Install MongoDB
sudo apt-get install -y mongodb

# Clone repo
git clone https://github.com/yourusername/student-os.git
cd student-os/server

# Install deps
npm install

# Create .env
cat > .env << EOF
MONGODB_URI=mongodb://localhost:27017/student-os
JWT_SECRET=$(openssl rand -base64 32)
PORT=5000
NODE_ENV=production
EOF

# Start with PM2
npm install -g pm2
pm2 start src/server.js --name "student-os"
pm2 startup
pm2 save
```

## Database Deployment

### MongoDB Atlas (Cloud)
1. Go to https://www.mongodb.com/cloud/atlas
2. Create account
3. Create cluster (free tier available)
4. Get connection string
5. Add to .env: `MONGODB_URI=mongodb+srv://user:pass@cluster.mongodb.net/`

### Self-Hosted MongoDB
```bash
# Ubuntu
sudo apt-get install -y mongodb

# macOS
brew install mongodb-community

# Start service
sudo systemctl start mongod
```

## Environment Variables

### Frontend (.env.production)
```env
VITE_API_URL=https://api.yourdomain.com
VITE_ENV=production
```

### Backend (.env)
```env
MONGODB_URI=mongodb+srv://user:pass@cluster.mongodb.net/student-os
JWT_SECRET=your-long-random-secret-key-here
PORT=5000
NODE_ENV=production
CORS_ORIGIN=https://yourdomain.com
```

## GitHub Actions - Auto Deploy

### Frontend (.github/workflows/deploy-frontend.yml)
```yaml
name: Deploy Frontend

on:
  push:
    branches: [main]
    paths:
      - 'client/**'

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: cd client && npm ci && npm run build
      - uses: vercel/action@main
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
```

### Backend (.github/workflows/deploy-backend.yml)
```yaml
name: Deploy Backend

on:
  push:
    branches: [main]
    paths:
      - 'server/**'

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
      - run: cd server && npm ci
      - name: Deploy to Railway
        run: |
          npm install -g @railway/cli
          railway deploy
        env:
          RAILWAY_TOKEN: ${{ secrets.RAILWAY_TOKEN }}
```

## Production Checklist

### Security ✅
- [ ] Change JWT_SECRET to strong random string
- [ ] Set NODE_ENV=production
- [ ] Enable HTTPS/SSL
- [ ] Add CORS whitelist (frontend URL only)
- [ ] Rate limiting enabled
- [ ] Input validation on all endpoints
- [ ] No console.log in production code
- [ ] Environment variables not in code

### Performance ✅
- [ ] Frontend bundled & minified
- [ ] API responses gzipped
- [ ] Database indexes created
- [ ] CDN configured for static files
- [ ] Caching headers set
- [ ] Image optimization done

### Monitoring ✅
- [ ] Error tracking (Sentry, LogRocket)
- [ ] Performance monitoring
- [ ] Uptime monitoring
- [ ] Database backups automated
- [ ] Logs aggregation setup

### Testing ✅
- [ ] All features tested in staging
- [ ] Mobile responsiveness verified
- [ ] Authentication flow verified
- [ ] API endpoints tested
- [ ] Database migration tested

## Scaling Considerations

### Initial (< 1000 users)
- Single MongoDB instance
- Single Node.js server
- Basic CDN for static assets

### Growth (1K - 100K users)
- MongoDB replica set
- Multiple Node.js instances behind load balancer (nginx)
- Redis for caching
- Separate database for analytics

### Large Scale (100K+)
- MongoDB sharded cluster
- Kubernetes orchestration
- Microservices (auth, tasks, analytics)
- Message queue (RabbitMQ/Kafka)
- Advanced caching layer

## Rollback Procedures

### Frontend
```bash
# Revert to previous commit
git revert <commit-sha>
git push

# Vercel auto-deploys
```

### Backend
```bash
# With PM2
pm2 restart student-os  # Quick restart
pm2 revert              # Undo failed update

# With Docker
docker rollback <service> <version>
```

## Post-Deployment

1. ✅ Test all features on live site
2. ✅ Monitor error logs
3. ✅ Check performance metrics
4. ✅ Verify database backups
5. ✅ Set up monitoring alerts
6. ✅ Document deployment process
7. ✅ Plan maintenance window

## Useful Commands

```bash
# Check Node version
node -v

# Check MongoDB
mongo --version

# Test API health
curl https://api.yourdomain.com/api/health

# Monitor logs
pm2 logs

# Database backup
mongodump --out ./backup

# Restore database
mongorestore ./backup
```

## Support & Resources

- **Vercel Docs**: https://vercel.com/docs
- **Railway Docs**: https://docs.railway.app
- **MongoDB Atlas**: https://docs.atlas.mongodb.com
- **Node.js Deployment**: https://nodejs.org/en/docs/guides/nodejs-docker-webapp/

---

Ready to go live! 🚀
