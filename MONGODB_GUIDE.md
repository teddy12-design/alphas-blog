# MongoDB Atlas Connection Guide

Since Vercel cannot access your local computer's database, you need to host your database in the cloud. **MongoDB Atlas** is the standard free way to do this.

## Step 1: Create a Cluster
1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register) and sign up for free.
2. Create a new project.
3. Click **"Build a Database"**.
4. Select **"M0 FREE"** (Shared) and click **"Create"**.
5. Choose a region (e.g., AWS / N. Virginia) and click **"Create Cluster"**.

## Step 2: Create a Database User
1. You will be asked to create a database user.
2. Enter a **Username** (e.g., `admin`) and a **Password**.
3. **IMPORTANT:** Write down this password! You will need it later.
4. Click **"Create User"**.

## Step 3: Allow Network Access
1. On the left sidebar, go to **"Network Access"**.
2. Click **"Add IP Address"**.
3. Select **"Allow Access from Anywhere"** (0.0.0.0/0).
   * *Note: This is required for Vercel to connect to your database.*
4. Click **"Confirm"**.

## Step 4: Get Connection String
1. Go back to **"Database"** on the left sidebar.
2. Click the **"Connect"** button on your cluster.
3. Select **"Drivers"** (Node.js).
4. Copy the connection string. It will look like this:
   `mongodb+srv://<username>:<password>@cluster0.abcde.mongodb.net/?retryWrites=true&w=majority`

## Step 5: Add to Vercel
1. Go to your Vercel Project Settings -> **Environment Variables**.
2. Add a new variable:
   * **Key:** `MONGODB_URI`
   * **Value:** Paste the string you copied.
3. **CRITICAL:** Replace `<password>` in the string with the actual password you created in Step 2.
   * Example: `mongodb+srv://admin:mypassword123@cluster0...`

## Step 6: Redeploy
1. Go to the **Deployments** tab in Vercel.
2. Click the three dots on your latest deployment -> **Redeploy**.
3. Your app should now work!
