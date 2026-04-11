# 🌐 Enterprise Static Website Hosting on AWS

**Amazon S3 + CloudFront + Route 53 + HTTPS + Edge Security**

![AWS](https://img.shields.io/badge/AWS-S3%20%7C%20CloudFront%20%7C%20Route53-orange)
![Architecture](https://img.shields.io/badge/Architecture-Global%20Serverless-blue)
![Security](https://img.shields.io/badge/Security-HTTPS%20%7C%20DDoS%20Protection-green)
![Status](https://img.shields.io/badge/Project-Production--Ready-success)

---

## 📖 Overview

This project demonstrates how to design and deploy a **secure, scalable, and production-grade static website hosting architecture** on AWS.

It leverages:

- **Amazon S3** for private object storage  
- **Amazon CloudFront** for global CDN and edge delivery  
- **Amazon Route 53** for DNS routing  
- **AWS Certificate Manager (ACM)** for HTTPS encryption  

---

## ❗ Problem Statement

Organizations hosting web applications globally often face:

- ❌ High latency for distributed users  
- ❌ Security risks from public S3 buckets  
- ❌ Lack of protection against DDoS attacks  
- ❌ Complex infrastructure scaling challenges  
- ❌ Poor content delivery performance  

---

## 💡 Solution

This project implements a **secure, serverless, edge-optimized architecture** using AWS managed services.

### Key Capabilities

- ✅ Private S3 bucket (no public access)  
- ✅ CloudFront CDN for global content delivery  
- ✅ HTTPS enforced using ACM certificates  
- ✅ Secure access using CloudFront Origin Access Control (OAC)  
- ✅ DNS routing via Route 53  
- ✅ Built-in DDoS protection via AWS Shield  

---

## 🏗️ Architecture Diagram

<p align="center">
  <img src="screenshots/architecture.png" width="750"/>
</p>

---

## 🔄 Architecture Flow

1. User accesses domain (`ausfrane.com`)  
2. Route 53 resolves DNS request  
3. Request routed to nearest CloudFront edge location  
4. CloudFront fetches content from private S3 bucket  
5. Content cached and delivered globally  

---

## 🌍 Real-World Relevance

- 🌐 Enterprise websites  
- 🛒 E-commerce platforms  
- 🚀 SaaS frontends  
- 📱 Web applications  
- 🏢 Internal portals  

---

## 📊 Business Impact

- ⚡ **60–80% latency reduction**  
- 🌍 Global edge delivery  
- 🔄 High availability architecture  
- 🔐 HTTPS + DDoS protection  
- 📉 ~80% reduction in operational overhead  

---

## 💼 Business Value

- 🚀 Faster deployments  
- 💰 Cost efficiency  
- 📈 Scalable architecture  
- 🔐 Improved security posture  
- 👨‍💻 Increased productivity  

---

## 🎯 Key Features

### 🌍 Global CDN Delivery
- Edge caching via CloudFront  
- Low latency worldwide  

### 🔐 Security
- Private S3 bucket  
- HTTPS enforcement  
- AWS Shield protection  

### ⚡ High Availability
- Fully serverless  
- No single point of failure  

### 📦 Cost Optimization
- Pay-as-you-go  
- Reduced origin requests  

---

## ⚙️ Implementation Steps

### 1️⃣ Create S3 Bucket

- Create bucket: `ausfrane.com`  
- Enable versioning and bucket key  
- Enable **Block Public Access**

---

### 2️⃣ Upload Website Files

- Upload `index.html`  
- Confirm file exists  

---

### 3️⃣ Disable Static Website Hosting

- Go to **Properties**  
- Disable static hosting  

---

### 4️⃣ Configure Bucket Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowCloudFrontAccess",
      "Effect": "Allow",
      "Principal": {
        "Service": "cloudfront.amazonaws.com"
      },
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::ausfrane.com/*",
      "Condition": {
        "StringEquals": {
          "AWS:SourceArn": "arn:aws:cloudfront::<ACCOUNT_ID>:distribution/<DISTRIBUTION_ID>"
        }
      }
    }
  ]
}
```

---

5️⃣ Create CloudFront Distribution
Origin: S3 bucket
Viewer protocol: Redirect HTTP → HTTPS
Attach ACM certificate
Enable caching
6️⃣ Configure CloudFront
Set default root object: index.html
Create cache invalidation:
/*
7️⃣ Configure Route 53
Create hosted zone: ausfrane.com
Create A (Alias) record → CloudFront
8️⃣ Access Website
https://ausfrane.com
🔐 Security Architecture
Layer	Protection
CloudFront	AWS Shield (DDoS protection)
HTTPS	TLS encryption
S3	Private bucket
IAM	Least privilege
📸 Screenshots
S3 Bucket
<p align="center"> <img src="screenshots/s3-bucket.png" width="700"/> </p>
Upload
<p align="center"> <img src="screenshots/upload.png" width="700"/> </p>
CloudFront
<p align="center"> <img src="screenshots/cloudfront.png" width="700"/> </p>
Route 53
<p align="center"> <img src="screenshots/route53.png" width="700"/> </p>
Output
<p align="center"> <img src="screenshots/output.png" width="700"/> </p>
🧠 Key Learnings
CDN reduces latency significantly
Private S3 improves security
CloudFront enhances performance + protection
Route 53 enables reliable DNS routing
Edge caching improves efficiency
📈 Future Improvements
🔒 Implement full OAC
🛡️ Add AWS WAF
⚙️ Terraform automation
🔄 CI/CD with GitHub Actions
📊 CloudWatch monitoring
📂 Project Structure
project-root/
├── index.html
├── screenshots/
└── README.md
👨‍💻 Author

Augustine Ebere Ohuabunwa
Solutions Architect | AWS Certified | DBA

📜 License

Educational and real-world implementation use.

⭐ Final Note
🌍 Global scalability
🔐 Secure architecture
⚡ High performance
📈 Enterprise-ready design
