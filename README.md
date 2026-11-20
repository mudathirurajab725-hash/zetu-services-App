rm -f zetuservices.com
git init
git branch -M main
git add .
git commit -m "Initial commit - Zetu Services"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin mainservices:
  - type: web
    name: zetu-services
    runtime: node
    plan: free
    buildCommand: npm install && npm run build
    startCommand: npm run start
    healthCheckPath: /api/health
    envVars:
      - key: NODE_ENV
        value: production
      - key: NODE_VERSION
        value: 22.12.0
      - key: SESSION_SECRET
        generateValue: true
      - key: MASTER_ADMIN_PASSWORD
        sync: false
      - key: APP_URL
        sync: false
      - key: SUPABASE_URL
        sync: false
      - key: VITE_SUPABASE_URL
        sync: false
      - key: VITE_SUPABASE_ANON_KEY
        sync: false
      - key: SUPABASE_SERVICE_ROLE_KEY
        sync: false
      - key: PESAPAL_ENV
        value: live
      - key: PESAPAL_CONSUMER_KEY
        sync: false
      - key: PESAPAL_CONSUMER_SECRET
        sync: falsenpm install && npm run buildNODE_ENV=production
NODE_VERSION=22.12.0
PESAPAL_ENV=live
MASTER_ADMIN_PASSWORD=your-strong-admin-password
SESSION_SECRET=any-long-random-string
APP_URL=https://zetu-services.onrender.com
SUPABASE_URL=your-supabase-url
VITE_SUPABASE_URL=your-supabase-url
VITE_SUPABASE_ANON_KEY=your-supabase-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-supabase-secret-key
PESAPAL_CONSUMER_KEY=your-pesapal-key
PESAPAL_CONSUMER_SECRET=your-pesapal-secret/api/healthnpm run start