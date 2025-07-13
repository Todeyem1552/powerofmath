# 🔢 To the Power of Math – Serverless Calculator

A fully serverless web application built using **AWS Amplify**, **API Gateway**, **AWS Lambda**, and **DynamoDB**. The app calculates the power of a number (e.g., 2⁵ = 32), stores results in DynamoDB, and demonstrates real-time serverless computation with persistent storage and CI/CD using AWS Amplify.

---

## 🚀 Live Demo

👉 [Try the App Here](https://master.d2ty8p248jwx1e.amplifyapp.com/)  

---

## 📐 Architecture Overview

Frontend (HTML + JS)
↓
AWS Amplify (Static Hosting + CI/CD)
↓
API Gateway (POST Method)
↓
AWS Lambda (Python 3.12 Handler)
↓
DynamoDB (Power Result Storage)

---


---

## 🧠 Features

- 🧮 Calculates `base^exponent` via a POST API call
- ☁️ Hosted frontend on **AWS Amplify** with GitHub integration
- 🧠 Backend logic handled by **AWS Lambda** in **Python**
- 🗃️ Persistent storage with **DynamoDB**
- 🔧 Fully defined using **CloudFormation** (Infrastructure as Code)
- 🔐 Includes CORS headers and API key-based access control

---

## 🛠️ Technologies Used

| Component     | Service             |
|---------------|---------------------|
| Frontend      | HTML/CSS/JS hosted on AWS Amplify |
| Backend Logic | AWS Lambda (Python 3.12) |
| API Gateway   | REST API endpoint with POST |
| Database      | DynamoDB (PAY_PER_REQUEST mode) |
| IaC           | AWS CloudFormation |
| CI/CD         | GitHub → Amplify pipeline |
| Security      | IAM Roles, API Gateway API Key |

---

## 📄 How It Works

1. The user inputs a base and exponent via the Amplify-hosted frontend.
2. A `POST` request is sent to an API Gateway endpoint.
3. API Gateway invokes the Lambda function.
4. Lambda calculates the power, stores it in DynamoDB, and returns the result.
5. The frontend displays the computed result in a popup.

---

## 💻 Example Request/Response

### 🔁 POST Request Payload
```json
{
  "base": 2,
  "exponent": 5
}
{
  "message": "Your result is 32.0"
}

---
🔐 Suggested Security Improvements

1. Use API Keys with Usage Plans 

Generate an API Key in API Gateway
Attach it to a Usage Plan with throttling limits
Require the key in headers (x-api-key)

2. Store API Key Securely
Use AWS Secrets Manager to store the API key
Access it securely in CI/CD or from Lambda if needed

3. IAM Role Restrictions

Limit Lambda IAM permissions to specific DynamoDB table ARN
Restrict logs to only required CloudWatch resources

---

🌐 Fixing CORS (Cross-Origin Resource Sharing)
To avoid CORS issues, set these in your API Gateway configuration:

Method Response (POST /my-resource)
method.response.header.Access-Control-Allow-Headers: 'Content-Type,X-Amz-Date,Authorization,X-Api-Key,X-Amz-Security-Token'
method.response.header.Access-Control-Allow-Methods: 'OPTIONS,POST'
method.response.header.Access-Control-Allow-Origin: '*'

Integration Response (Lambda response headers)

{
"Access-Control-Allow-Headers": "Content-Type,X-Amz-Date,Authorization,X-Api-Key,X-Amz-Security-Token",
"Access-Control-Allow-Methods": "OPTIONS,POST",
"Access-Control-Allow-Origin": "*"
}







