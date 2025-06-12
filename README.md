
## 🚀 Prerequisites

- ✅ **Node.js Version**: 18 or later (tested with v18 & v22)
- ✅ **npm** (comes with Node.js)
- ✅ **PM2** for process management

---

## 📦 Running the Application

### 1. Install Dependencies

```bash
npm install
```

### 2. Run Tests

```bash
npm run check
```

### 3. Start the Application

```bash
npm start
```

---

## 🚀 Deployment Process (PM2)

### 1. Stop Existing Process (if any)

```bash
pm2 delete node-app || true
```

### 2. Start the Application

```bash
pm2 start "./src/server.js" --name node-app
```

### 3. Save PM2 Process List

```bash
pm2 save
```

---

## 🌐 Application Overview

- **Routes:**
  - `/` → Returns a "Hello World" page
  - `/api` → Returns a JSON response

- **Default Port:** `3000`

---

## 🛠️ CI/CD Challenges & Solutions

### 1. ✅ Self-Hosted Runner Setup

**Challenge:** Ensuring the runner had all required tools (Node.js, npm, PM2).

**Solution:**  
Manual setup with the following:

```bash
# Install Node.js and npm (https://nodejs.org/en/download/)
# Then install pm2 globally
npm install -g pm2
```

---

### 2. 🧪 Capturing Test Output in PowerShell

**Challenge:** Redirecting both stdout and stderr from `npm run check`.

**Solution:**  
Used PowerShell-specific redirection:

```powershell
npm run check *>&1 | Out-File -FilePath test-results/test-output.txt -Encoding utf8
```

---

### 3. 🔄 Managing PM2 Processes Gracefully

**Challenge:** `pm2 stop` throws error if the app doesn't exist yet.

**Solution:**  
Used `try/catch` in PowerShell to prevent script failure on first deploy.
