# PostgreSQL Setup for Development

## Install PostgreSQL on Windows

### 1. Download PostgreSQL

1. Go to [PostgreSQL Downloads](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)
2. Download the latest Windows x86-64 version (PostgreSQL 16 or later)

### 2. Install PostgreSQL

1. **Run the installer** as Administrator
2. **Installation Directory**: Use default (`C:\Program Files\PostgreSQL\16\`)
3. **Select Components**:
   - ✅ PostgreSQL Server
   - ✅ pgAdmin 4 (GUI management tool)
   - ✅ Command Line Tools
   - ❌ Stack Builder (not needed for development)
4. **Data Directory**: Use default
5. **Password**: Set a password for the `postgres` superuser (remember this!)
6. **Port**: Use default `5432`
7. **Locale**: Use default
8. **Complete Installation**

### 3. Add PostgreSQL to PATH

1. Press `Win + R`, type `sysdm.cpl`, press Enter
2. Go to **Advanced** tab → **Environment Variables**
3. Under **System Variables**, select `Path` → **Edit**
4. Click **New** and add: `C:\Program Files\PostgreSQL\16\bin`
5. Click **OK** on all windows

### 4. Verify Installation

Open Command Prompt or PowerShell and run:
```bash
psql --version
```

You should see something like: `psql (PostgreSQL) 16.x`

### 5. Create Development Database

1. **Connect to PostgreSQL**:
   ```bash
   psql -U postgres
   ```
   (Enter the password you set during installation)

2. **Create database and user**:
   ```sql
   CREATE DATABASE privacy_comms_dev;
   CREATE USER dev_user WITH PASSWORD 'dev_password';
   GRANT ALL PRIVILEGES ON DATABASE privacy_comms_dev TO dev_user;
   \q
   ```

### 6. Test Connection

```bash
psql -U dev_user -d privacy_comms_dev -h localhost
```

### Development Environment Variables

Add these to your backend `.env` file:
```env
# Database Configuration
DB_HOST=localhost
DB_PORT=5432
DB_NAME=privacy_comms_dev
DB_USER=dev_user
DB_PASSWORD=dev_password
DB_SSL=false
```

### pgAdmin 4 (Optional GUI)

- Launch **pgAdmin 4** from Start Menu
- Add server with connection details above
- Use for visual database management

### Troubleshooting

**Connection Issues:**
- Ensure PostgreSQL service is running: `services.msc` → Look for `postgresql-x64-16`
- Check Windows Firewall if connecting from other machines

**Authentication Failed:**
- Double-check username/password
- Ensure user has proper database permissions 