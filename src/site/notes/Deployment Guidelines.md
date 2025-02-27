---
{"dg-publish":true,"permalink":"/deployment-guidelines/"}
---

# Deployment Guidelines for Angular + Strapi

## **Overview**

This document outlines the deployment process for applications using **Angular** as the frontend and **Strapi** as the backend. It covers environment setup, build steps, hosting, and deployment best practices.

---

## **Pre-requisites**

Ensure you have the following installed and configured:

- **Node.js (LTS version)** – Required for both Angular and Strapi
- **npm or yarn** – Package managers
- **Docker** (Optional) – For containerized deployment
- **Database** – PostgreSQL, MySQL, or SQLite (for local testing)
- **Cloud Hosting Account** – AWS, DigitalOcean, Vercel, or similar

---

## **1. Backend (Strapi) Deployment**

### **Step 1: Install Dependencies**

Navigate to the Strapi project directory and install dependencies:

```sh
cd backend
npm install  # or yarn install
```

### **Step 2: Configure Environment Variables**

Create a `.env` file in the root of your Strapi project:

```env
DATABASE_CLIENT=postgres
DATABASE_HOST=your-db-host
DATABASE_PORT=5432
DATABASE_NAME=your-db-name
DATABASE_USERNAME=your-db-user
DATABASE_PASSWORD=your-db-password
JWT_SECRET=your-secret-key
```

### **Step 3: Build and Start Strapi**

For production:

```sh
npm run build
npm start
```

For development:

```sh
npm run develop
```

### **Step 4: Deploy Strapi**

#### **Option 1: Deploy on a Server (Linux-based)**

```sh
pm run build
pm install pm2 -g
pm start & # or use PM2 for process management
```

#### **Option 2: Deploy Using Docker**

```sh
docker-compose up -d
```

---

## **2. Frontend (Angular) Deployment**

### **Step 1: Install Dependencies**

Navigate to the Angular project directory and install dependencies:

```sh
cd frontend
npm install  # or yarn install
```

### **Step 2: Configure Environment Variables**

Modify `src/environments/environment.prod.ts`:

```typescript
export const environment = {
  production: true,
  apiUrl: 'https://api.example.com'
};
```

### **Step 3: Build Angular App**

```sh
ng build --configuration=production
```

This generates a `dist/` folder with production-ready files.

### **Step 4: Deploy Angular App**

#### **Option 1: Deploy to Vercel**

```sh
npm install -g vercel
vercel --prod
```

#### **Option 2: Deploy to Nginx (Linux Server)**

```sh
sudo cp -r dist/your-angular-app /var/www/html
sudo systemctl restart nginx
```

#### **Option 3: Deploy to Firebase**

```sh
npm install -g firebase-tools
firebase login
firebase deploy
```

---

## **3. Continuous Deployment (Optional)**

Use **GitHub Actions** or **GitLab CI/CD** to automate deployments:

Example GitHub Actions Workflow (`.github/workflows/deploy.yml`):

```yaml
name: Deploy Angular & Strapi

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Install Dependencies & Build Angular
        run: |
          cd frontend
          npm install
          ng build --configuration=production
      - name: Deploy to Server
        run: |
          ssh user@your-server "cd /var/www/frontend && git pull && ng build --configuration=production"
```

---

## **4. Monitoring & Maintenance**

- **Use PM2** to keep the backend running: `pm2 start npm --name "strapi" -- start`
- **Enable Logging** for error tracking
- **Set Up Backups** for the database

---

## **Conclusion**

Following these deployment steps ensures a smooth and efficient deployment process for your **Angular + Strapi** stack. 🚀