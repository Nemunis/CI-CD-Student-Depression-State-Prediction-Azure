# CI/CD - Machine Learning Model Deployment using Azure App Service & GitHub Actions

This repository contains a Machine Learning model deployment pipeline using **Azure App Service** with **CI/CD** powered by **GitHub Actions**.

Every time you push changes to your GitHub repository, your app will automatically rebuild and redeploy on Azure App Service — no manual steps required.

---

## Project Overview

This setup allows you to:
- Deploy a streamlit app that serves your ML model.
- Automate deployment via GitHub Actions.
- Continuously integrate changes from GitHub to Azure.
- Easily maintain and update the model or API logic.
---

---

## Step-by-Step Setup and Deployment

### 1️⃣ Create Azure Account
- Go to [https://portal.azure.com](https://portal.azure.com)
- Sign in or create a new Microsoft Azure account.

---

### 2️⃣ Log in to Azure Portal
- Navigate to the [Azure Portal Dashboard](https://portal.azure.com/#home)
- You’ll manage your app from **App Services**.

---

### 3️⃣ Create an App Service (Web App)

1. In the left sidebar, click **App Services** → **Create** → **Web App**
2. Fill out the details:
   - **Subscription:** Your Azure subscription  
   - **Resource Group:** Create a new or select an existing one  
   - **Name:** Unique name for your app (e.g., `ml-model-api`)  
   - **Publish:** Select **Code**  
   - **Runtime stack:** Choose **Python 3.10+**  
   - **Region:** Choose nearest region (e.g., East US)  

3. Click **Review + Create**, then **Create**.

Once deployment completes, click **Go to Resource**.

---

### 4️⃣ Set Up Continuous Deployment from GitHub

1. In your App Service resource page, go to:
   **Deployment → Deployment Center**

2. Under **Source**, select:
   - **GitHub**

3. Under **Build Provider**, select:
   - **GitHub Actions**

4. Sign in with your GitHub account (if prompted).

5. Choose your:
   - **Organization**
   - **Repository**
   - **Branch** (usually `main`)

6. Click **Save** or **Finish**.

Azure will automatically create a GitHub Actions workflow (`azure-webapps.yml`) that deploys your app whenever changes are pushed to GitHub.

---

### 5️⃣ Configure the Startup Command

In your App Service:

1. Go to **Settings → Configuration → General Settings**  
2. Scroll down to **Startup Command**
3. Enter this command:

   ```bash
   streamlit run main.py --server.port 8000 --server.address 0.0.0.0
