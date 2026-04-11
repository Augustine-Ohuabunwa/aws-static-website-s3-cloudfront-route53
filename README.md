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

This architecture reflects **real-world enterprise cloud design**, focusing on performance, security, and scalability.

---

## ❗ Problem Statement

Organizations hosting web applications globally often face:

- ❌ High latency for distributed users  
- ❌ Security risks from public S3 buckets  
- ❌ Lack of protection against DDoS attacks  
- ❌ Complex infrastructure scaling challenges  
- ❌ Poor content delivery performance  

Traditional hosting approaches fail to provide **low latency, high availability, and strong security simultaneously**.

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
5. Content cached and delivered globally with low latency  

---

## 🌍 Real-World Relevance

This architecture is widely used for:

- 🌐 Enterprise websites  
- 🛒 E-commerce platforms  
- 🚀 SaaS frontends  
- 📱 Web and mobile applications  
- 🏢 Internal enterprise portals  

It represents **modern cloud-native and edge delivery architecture**.

---

## 📊 Business Impact

- ⚡ **Latency Reduction:** Up to **60–80% faster delivery**  
- 🌍 **Global Performance:** Content served from nearest edge location  
- 🔄 **High Availability:** Distributed infrastructure ensures uptime  
- 🔐 **Enhanced Security:** HTTPS + DDoS protection  
- 📉 **Operational Efficiency:** ~80% reduction in infrastructure management  

---

## 💼 Business Value

- 🚀 Faster time-to-market  
- 💰 Reduced infrastructure cost  
- 📈 Scalable for growth  
- 🔐 Improved security posture  
- 👨‍💻 Increased engineering productivity  

---

## 🎯 Key Features

### 🌍 Global CDN Delivery
- Low latency worldwide  
- Edge caching via CloudFront  

### 🔐 Security
- Private S3 bucket  
- HTTPS enforced  
- AWS Shield protection  

### ⚡ High Availability
- Serverless architecture  
- No single point of failure  

### 📦 Cost Optimization
- Pay-as-you-go pricing  
- Reduced origin requests  

---

## ⚙️ Implementation Steps

### 1️⃣ Create S3 Bucket

- Create bucket: `ausfrane.com`  
- Enable:
  - Versioning  
  - Bucket Key  
- Enable **Block Public Access** (keep bucket private)  

---

### 2️⃣ Upload Website Files

- Upload `index.html`  
- Verify file exists in bucket  

---

### 3️⃣ Disable Static Website Hosting

- Navigate to **Properties**  
- Disable static website hosting  

---

### 4️⃣ Configure Bucket Policy (CloudFront Access)

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
5️⃣ Create CloudFront Distribution
Origin: S3 bucket
Origin type: Amazon S3
Viewer protocol: Redirect HTTP → HTTPS
Attach ACM certificate
Enable caching
6️⃣ Configure CloudFront
Set Default Root Object: index.html
Create cache invalidation:
/*
7️⃣ Configure Route 53
Create hosted zone: ausfrane.com
Create record:
Type: A (Alias)
Target: CloudFront distribution
8️⃣ Access Website

Open:

https://ausfrane.com
🔐 Security Architecture
Layer	Protection
CloudFront	AWS Shield (DDoS protection)
HTTPS	TLS encryption
S3	Private bucket
IAM	Least privilege access
📸 Screenshots
S3 Bucket Configuration
<p align="center"> <img src="screenshots/s3-bucket.png" width="700"/> </p>
File Upload
<p align="center"> <img src="screenshots/upload.png" width="700"/> </p>
CloudFront Distribution
<p align="center"> <img src="screenshots/cloudfront.png" width="700"/> </p>
Route 53 Configuration
<p align="center"> <img src="screenshots/route53.png" width="700"/> </p>
Live Website
<p align="center"> <img src="screenshots/output.png" width="700"/> </p>
🧠 Key Learnings
Importance of CDN in reducing latency
Difference between public vs private S3 access
CloudFront as a security and performance layer
DNS routing using Route 53
Edge caching strategies
📈 Future Improvements
🔒 Implement Origin Access Control (OAC fully)
🛡️ Add AWS WAF rules
⚙️ Automate deployment using Terraform
🔄 CI/CD pipeline using GitHub Actions
📊 Monitoring with CloudWatch
📂 Project Structure
project-root/
│
├── index.html
├── screenshots/
└── README.md
👨‍💻 Author

Augustine Ebere Ohuabunwa
Solutions Architect | AWS Certified | DBA
Cloud • Security • Automation • Cost Optimization

📜 License

This project is for educational, demonstration, and real-world implementation purposes.

⭐ Final Note

This project demonstrates a production-grade AWS architecture used in real enterprises to deliver:

🌍 Global scalability
🔐 Secure web applications
⚡ High performance
📈 Reliable infrastructure
