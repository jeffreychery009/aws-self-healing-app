
# Cloud Incident Simulation: Troubleshooting Real-World AWS Failures

## 📌 Project Objective
To simulate real AWS infrastructure issues and resolve them using industry-standard cloud support practices. This project demonstrates the ability to identify, investigate, and fix common cloud-related incidents using EC2, IAM, CloudWatch, and related tools.

---

## 🎯 Project Goals
- Simulate real-world AWS cloud issues
- Diagnose and resolve infrastructure problems
- Practice tools used by AWS Cloud Support Engineers
- Showcase troubleshooting and documentation skills

---

## 🔧 Technologies Used
- AWS EC2 (Ubuntu)
- Node.js
- Security Groups (VPC)
- CloudWatch (planned)
- CloudTrail (planned)
- IAM (planned)
- Bash scripting (planned)

---

## 🧪 Incident 001 – EC2 Server Becomes Unresponsive

### 📍 Incident Summary
Simulated a production-like EC2 outage by terminating the Node.js process running on an Ubuntu instance. The application stopped responding publicly despite the EC2 being “healthy” in the AWS Console.

### 📍 Symptoms
- Public IP of EC2 stopped returning content
- No error displayed — browser hung or timed out
- EC2 showed "running" status in AWS
- SSH still accessible

### 📍 Diagnosis Steps
1. SSH’d into EC2 instance using terminal  
2. Ran `top` and `ps aux` to check active processes  
3. Confirmed Node.js server was not running  
4. Checked if port 3000 was still open using `netstat -tuln`  
5. Reviewed logs (app and system logs) for crash indicators

### 📍 Root Cause
The Node.js process was terminated manually (simulated failure). No process manager (e.g., PM2) was configured to keep the app alive after crashes or reboots.

### 📍 Resolution
- Restarted the Node.js server manually  
- Installed and configured **PM2** to automatically restart the app on failure  
- Verified by rebooting the EC2 instance and confirming app auto-restarted

### 📍 Preventive Actions
- Configure **CloudWatch Agent** to monitor CPU and process health  
- Set **CloudWatch Alarms** to notify when app stops responding  
- Documented all steps in GitHub repo for reproducibility

---

## ✅ Key Skills Demonstrated
- EC2 provisioning & SSH access  
- Security group configuration  
- Process monitoring and recovery (Unix tools)  
- Root cause analysis  
- Planning for auto-recovery (PM2, CloudWatch)
