# Serverless File Sharing Platform

A **secure, scalable, and serverless file sharing platform** built using AWS services.  
It enables users to upload and download files via a simple HTTP API, with authentication and access control managed through **AWS Cognito**.  

---

## 📌 Features
- 🔐 **Authentication** – User registration, login, and JWT-based authentication using AWS Cognito.  
- 📤 **File Uploads** – Upload files securely to **Amazon S3** via authenticated API requests.  
- 📥 **File Downloads** – Retrieve files from S3 with secure access tokens.  
- 🔗 **File Sharing** – Generate secure links for file distribution.  
- 👨‍👩‍👧‍👦 **Collaboration** – Share resources among authenticated team members.  
- ☁️ **Serverless Infrastructure** – Fully managed on AWS Lambda, API Gateway, S3, and Cognito.  

---

## 🏗️ System Architecture

1. **Client (Postman / Any HTTP Client)**  
   - Authenticate with AWS Cognito to get a JWT token.  
   - Use token in Authorization header (`Bearer <token>`) for API requests.  

2. **AWS Cognito**  
   - Handles user sign-up, sign-in, and authentication.  
   - Issues secure JWT tokens.  

3. **API Gateway**  
   - Entry point for requests.  
   - Validates JWTs using Cognito Authorizer.  
   - Routes to appropriate Lambda function.  

4. **AWS Lambda Functions**  
   - **UploadFunction** → Stores files in S3.  
   - **DownloadFunction** → Fetches requested files from S3.  

5. **Amazon S3**  
   - Stores uploaded files securely.  
   - Scales automatically.  

---

## ⚙️ Technology Stack
- **AWS Services:** API Gateway, Lambda, S3, Cognito  
- **Programming Language:** Python 3.9  
- **Security & Access Control:**  
  - Cognito User Pools (user management)  
  - Cognito Authorizer (JWT validation)  
  - IAM Roles & Policies (secure access to S3)  
- **Tools:** Postman, AWS Console & CLI  

---

## 🚀 How to Use

1. **Authenticate** with AWS Cognito to obtain a JWT token.  
2. **Upload a file**  
   ```http
   POST /files
3. **Download a file**  
   ```http
   GET /files?fileName=example.txt
   Authorization: Bearer <JWT_TOKEN>
4. **Files are stored securely in S3**  
   - Only accessible by authenticated users.
   - Unauthorized requests will be denied.
   Authorization: Bearer <JWT_TOKEN>
   Body: { "fileName": "example.txt", "content": "<file_content>" }
