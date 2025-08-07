# Pall Network - Netlify Deployment Guide

## 📋 Prerequisites

Before deploying to Netlify, ensure you have:

1. **Netlify Account**: Sign up at [netlify.com](https://netlify.com)
2. **Database**: Set up a PostgreSQL database (recommended: Neon, Supabase, or Railway)
3. **Environment Variables**: Collect all required API keys and secrets

## 🚀 Step-by-Step Deployment

### Step 1: Prepare Your Database

1. **Create a PostgreSQL Database**:
   - **Neon** (Recommended): Go to [neon.tech](https://neon.tech)
   - **Supabase**: Go to [supabase.com](https://supabase.com)
   - **Railway**: Go to [railway.app](https://railway.app)

2. **Get Your Database URL**:
   - Copy the connection string (format: `postgresql://username:password@host:port/database`)

3. **Run Database Migrations**:
   ```bash
   # In your local project
   npm run db:push
   ```

### Step 2: Deploy to Netlify

#### Option A: Git Deployment (Recommended)

1. **Push to GitHub**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit - Pall Network App"
   git branch -M main
   git remote add origin https://github.com/yourusername/pall-network.git
   git push -u origin main
   ```

2. **Connect to Netlify**:
   - Go to [netlify.com](https://netlify.com) and log in
   - Click "New site from Git"
   - Choose "GitHub" and authorize access
   - Select your `pall-network` repository

3. **Configure Build Settings**:
   - **Build command**: `npm run build`
   - **Publish directory**: `dist/public`
   - **Functions directory**: `netlify/functions`

#### Option B: Manual Deployment

1. **Upload Zip File**:
   - Go to Netlify dashboard
   - Click "Deploy manually"
   - Drag and drop your project zip file

### Step 3: Configure Environment Variables

In your Netlify site settings, go to **Site settings** > **Environment variables** and add:

```bash
# Database
DATABASE_URL=your_postgresql_connection_string

# Session Security
SESSION_SECRET=your_super_secret_session_key_here

# Replit Authentication (if using)
REPLIT_CLIENT_ID=your_replit_client_id
REPLIT_CLIENT_SECRET=your_replit_client_secret

# Node Environment
NODE_ENV=production
```

### Step 4: Configure Custom Domain (Optional)

1. **Add Custom Domain**:
   - Go to **Site settings** > **Domain management**
   - Click "Add custom domain"
   - Enter your domain name

2. **Configure DNS**:
   - Point your domain's CNAME to: `your-site-name.netlify.app`
   - Or use Netlify DNS for easier setup

### Step 5: Enable HTTPS

1. **SSL Certificate**:
   - Netlify automatically provides SSL certificates
   - Wait for provisioning to complete (~5-10 minutes)

### Step 6: Test Your Deployment

1. **Access Your App**:
   - Visit your Netlify URL: `https://your-site-name.netlify.app`

2. **Test Core Features**:
   - User authentication
   - Mining functionality
   - Package upgrades
   - Wallet transactions

## 🔧 Important Configuration Files

### netlify.toml
Your site includes a `netlify.toml` file with:
- Build settings
- Function configuration
- Redirect rules
- Development settings

### Environment Variables Required

| Variable | Description | Example |
|----------|-------------|---------|
| `DATABASE_URL` | PostgreSQL connection string | `postgresql://user:pass@host:5432/db` |
| `SESSION_SECRET` | Secret for session encryption | `super-secret-key-change-this` |
| `REPLIT_CLIENT_ID` | Replit OAuth client ID | `your-replit-client-id` |
| `REPLIT_CLIENT_SECRET` | Replit OAuth client secret | `your-replit-client-secret` |
| `NODE_ENV` | Environment mode | `production` |

## 🔍 Troubleshooting

### Common Issues

1. **Build Fails**:
   - Check that all dependencies are listed in package.json
   - Verify TypeScript compilation passes locally
   - Check build logs in Netlify dashboard

2. **Database Connection Issues**:
   - Verify DATABASE_URL is correctly formatted
   - Ensure database allows external connections
   - Check if database is running

3. **Authentication Problems**:
   - Verify Replit OAuth settings
   - Check redirect URLs in Replit app settings
   - Ensure SESSION_SECRET is set

4. **API Functions Not Working**:
   - Check function logs in Netlify dashboard
   - Verify functions are in `netlify/functions` directory
   - Ensure API routes are properly configured

### Build Commands Reference

```bash
# Local development
npm run dev

# Production build
npm run build

# Database migration
npm run db:push

# Type checking
npm run check
```

## 🎉 Success Checklist

- ✅ Database is connected and migrations are applied
- ✅ Environment variables are configured
- ✅ Site builds without errors
- ✅ User authentication works
- ✅ Mining functionality operates correctly
- ✅ Package upgrades function properly
- ✅ Mobile responsiveness is verified
- ✅ HTTPS is enabled

## 📞 Need Help?

If you encounter issues:
1. Check Netlify build logs
2. Review function logs
3. Verify environment variables
4. Test database connection
5. Check browser console for errors

Your Pall Network app is now ready for production! 🚀