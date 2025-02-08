git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main
```

### 3. Vercel Deployment

#### A. Connect to GitHub
1. Go to [Vercel](https://vercel.com)
2. Click "New Project"
3. Import your GitHub repository
4. Select the repository you just created

#### B. Configure Project Settings
1. Framework Preset: Select "Vite"
2. Build Command: Leave as default (`npm run build`)
3. Output Directory: Leave as default (`dist`)
4. Install Command: Leave as default (`npm install`)

#### C. Set Up Vercel Postgres (Free Tier)
1. In your Vercel dashboard, go to Storage
2. Click "Create Database"
3. Choose Postgres and select the free plan
4. Select the region closest to your users
5. Click "Create"
6. Vercel will automatically add the database connection details to your project

#### D. Configure Environment Variables
Add the following environment variables in your Vercel project settings:
```
SHOPIFY_API_KEY=your_api_key
SHOPIFY_API_SECRET=your_api_secret
APP_URL=https://your-vercel-domain.vercel.app
DATABASE_URL=your_vercel_postgres_url
```

### 4. Shopify App Setup

1. Go to your [Shopify Partners Dashboard](https://partners.shopify.com)
2. Create a new app
3. Under App Setup:
   - Set App URL to your Vercel deployment URL
   - Add allowed redirection URLs:
     ```
     https://your-vercel-domain.vercel.app/install
     https://your-vercel-domain.vercel.app/auth/callback
     ```
4. Copy the API credentials and add them to your Vercel environment variables

### 5. First Deployment

1. Commit and push any changes to GitHub
2. Vercel will automatically deploy your application
3. After deployment, your database tables will be automatically created
4. Visit your deployment URL to start using the application

## Local Development

1. Clone the repository:
```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
Create a `.env` file with the following:
```
SHOPIFY_API_KEY=your_api_key
SHOPIFY_API_SECRET=your_api_secret
APP_URL=http://localhost:5000
DATABASE_URL=your_database_url
```

4. Set up PostgreSQL:
- Install PostgreSQL locally (free)
  - Windows: Download from https://www.postgresql.org/download/windows/
  - Mac: Use `brew install postgresql`
  - Linux: `sudo apt-get install postgresql`
- Create a new database
- Update DATABASE_URL in your .env file

5. Start the development server:
```bash
npm run dev