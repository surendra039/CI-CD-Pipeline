# CI-CD-Pipeline
# Assignment 1

---

## **Pipeline Overview**

The pipeline automates the following tasks:

1. **Checkout:** Clone the repository from GitHub  
2. **Backend Build:** Create Python virtual environment, install dependencies  
3. **Backend Test:** Run unit tests using pytest  
4. **Backend Deploy:** Start the Flask backend application  
5. **Frontend Build & Deploy:** Install Node dependencies, build frontend, deploy build folder  
6. **Triggers:** Automatically run on every push to the `main` branch  
7. **Notifications:** Send email alerts on success or failure  

---

## **Jenkins Setup**

1. Install Jenkins on a VM or use a cloud Jenkins instance  
2. Install required plugins: Pipeline, Git, Email Extension  
3. Configure SMTP server in **Manage Jenkins → Configure System → Extended E-mail Notification**  
4. Create a new **Pipeline job** in Jenkins:
   - Pipeline script from SCM  
   - Repository URL: `https://github.com/surendra039/TravelMemory.git`  
   - Branch: `main`  
   - Script Path: `Jenkinsfile`  

---

## **Pipeline Stages**

### **1. Checkout**
- Clones the repository from GitHub  
- Checks out the `main` branch  

### **2. Backend Build**
- Creates a virtual environment at `backend/venv`  
- Installs dependencies from `backend/requirements.txt`  

### **3. Backend Test**
- Runs pytest on `backend/tests`  
- Skipped if no tests folder is present  

### **4. Backend Deploy**
- Starts `backend/app.py` in the background  
- Uses virtual environment for execution  

### **5. Frontend Build & Deploy**
- Moves into `frontend/` folder  
- Runs `npm install` and `npm run build`  
- Deploys build folder (customize deployment path if needed)  

---

## **Triggers**

- Triggered automatically on **push to main branch** via **GitHub webhook**  
- Alternatively, can use **Poll SCM** in Jenkins (every 5 minutes)  

---

## **Notifications**

- Sends email notifications using **Email Extension Plugin**  
- Notifies on:
  - **Success:** Build completed successfully  
  - **Failure:** Build failed, check console output  

---

## **How to Run**

1. Commit changes to the `main` branch  
2. Jenkins will automatically trigger the pipeline (via webhook or poll)  
3. Monitor pipeline progress in Jenkins console  
4. On success, backend and frontend are deployed  

---

## **Notes**

- Ensure the Jenkins workspace path has **no spaces** to avoid shell script errors  
- Update paths in `Jenkinsfile` if the repository structure changes  
- For frontend deployment, update the build copy path according to your server setup (e.g., `/var/www/html/frontend`)  
- For Gmail notifications, use an **App Password** for SMTP authentication  

---

###Assginment 2#####



Assign
