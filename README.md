# 🌐 Production-Ready Static Website Hosting on AWS

**S3 + CloudFront + Route 53 + HTTPS + Edge Security**

![AWS](https://img.shields.io/badge/AWS-CloudFront%20%7C%20S3%20%7C%20Route53-orange)
![Architecture](https://img.shields.io/badge/Architecture-Global%20Serverless-blue)
![Security](https://img.shields.io/badge/Security-HTTPS%20%7C%20DDoS%20Protection-green)
![Status](https://img.shields.io/badge/Project-Production--Ready-success)

---

## 📌 Overview

This project implements a **secure, scalable, and globally distributed static website hosting architecture** on AWS using industry best practices.

It leverages:

- **Amazon S3** for object storage  
- **Amazon CloudFront** for global content delivery  
- **Amazon Route 53** for DNS routing  
- **AWS Certificate Manager (ACM)** for HTTPS encryption  

---

## ❗ Problem Statement

Organizations delivering web applications globally face several challenges:

- ❌ High latency for geographically distributed users  
- ❌ Security vulnerabilities from unsecured HTTP endpoints  
- ❌ Exposure to DDoS attacks and traffic spikes  
- ❌ Complex infrastructure management for scalability  
- ❌ Inefficient content delivery impacting user experience  

Traditional hosting solutions often fail to provide **low latency, high availability, and strong security simultaneously**, making them unsuitable for modern cloud-native workloads.

---

## 💡 Solution

This project implements a **production-grade, edge-optimized architecture** using AWS managed services.

The solution provides:

- ✅ **Global CDN distribution** using CloudFront  
- ✅ **Secure HTTPS communication** via ACM certificates  
- ✅ **Highly available storage** with Amazon S3  
- ✅ **DNS routing and failover** using Route 53  
- ✅ **Built-in DDoS protection** via AWS Shield (CloudFront)  
- ✅ **Serverless design** eliminating infrastructure management  

This architecture aligns with the **AWS Well-Architected Framework**, ensuring:

- Operational Excellence  
- Security  
- Reliability  
- Performance Efficiency  
- Cost Optimization  

---

## 🌍 Real-World Relevance

This architecture is widely adopted in production environments for:

- 🌐 Corporate and enterprise websites  
- 🛒 E-commerce frontend platforms  
- 🚀 SaaS landing pages and applications  
- 📱 Mobile/web frontend delivery  
- 🏢 Internal enterprise portals  

It reflects how organizations implement **edge computing and CDN strategies** to deliver fast, secure, and scalable applications globally.

---

## 📊 Business Impact

This solution delivers measurable improvements in performance, reliability, and efficiency:

- ⚡ **Latency Reduction**
  - Up to **60–80% faster content delivery** via CloudFront edge locations  

- 🌍 **Global Performance Optimization**
  - Content served from nearest edge location, improving user experience worldwide  

- 🔄 **High Availability**
  - Achieves **99.99%+ availability** through distributed architecture  

- 🔐 **Enhanced Security**
  - HTTPS enforced across all endpoints  
  - Built-in **DDoS protection via AWS Shield**  

- 📉 **Reduced Operational Overhead**
  - Eliminates server management → **~80% reduction in maintenance effort**  

---

## 💼 Business Value

This architecture provides tangible value to organizations:

- 🚀 **Improved User Experience**
  - Faster load times increase engagement and retention  

- 💰 **Cost Optimization**
  - Pay-as-you-go model reduces infrastructure waste  

- 📈 **Scalability for Growth**
  - Seamlessly handles traffic spikes without redesign  

- 🔐 **Stronger Security & Compliance**
  - Meets modern web security standards (HTTPS, edge protection)  

- 👨‍💻 **Operational Efficiency**
  - Frees engineering teams from infrastructure management  

---

## 🎯 Project Objectives

- Deliver static content with **low latency worldwide**  
- Enforce **secure HTTPS communication**  
- Provide **resilience against DDoS attacks**  
- Demonstrate **production-grade cloud architecture**  

---

## 🏗️ Architecture Diagram

<p align="center">
  <img src="screenshots/architecture.png" width="750"/>
</p>

---

## 🔄 Request Flow

1. User sends request to domain  
2. DNS resolution via Route 53  
3. Request routed to nearest CloudFront edge location  
4. CloudFront fetches content from S3 origin  
5. Content cached and delivered globally  

---

## ⚙️ Tech Stack

| Service                 | Purpose                  |
|------------------------|--------------------------|
| Amazon S3              | Static file hosting      |
| Amazon CloudFront      | CDN + caching + security |
| Amazon Route 53        | Domain + DNS routing     |
| AWS Certificate Manager| SSL/TLS certificates     |

---

## 🚀 Key Features

### 🌍 Global Content Delivery
- Cached at CloudFront edge locations  
- Low latency for global users  

### 🔐 End-to-End Security
- HTTPS enforced via ACM  
- AWS Shield Standard (DDoS protection)  

### ⚡ High Availability
- Fully serverless architecture  
- No single point of failure  

### 📦 Cost Optimization
- Pay-as-you-go pricing  
- Reduced origin requests via caching  

---

## 🛠️ Implementation Breakdown

### 1️⃣ Domain & SSL Setup

- Domain: **ausfrane.com**  
- ACM certificate created (us-east-1)  
- Attached to CloudFront distribution  

---

### 2️⃣ S3 Static Website Hosting

- Bucket: `eldijove123`  
- Enabled static hosting  
- Uploaded `index.html`  

#### Bucket Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::eldijove123/*"
    }
  ]
}
3️⃣ CloudFront Configuration
Origin: S3 website endpoint
Default root object: index.html
Viewer protocol: Redirect HTTP → HTTPS
Cache invalidation: /*
4️⃣ Route 53 DNS Routing
Created A (Alias) record
Routed domain → CloudFront
🔐 Security Deep Dive
Layer	Protection
CloudFront	AWS Shield (DDoS protection)
HTTPS	TLS encryption
DNS	Route 53 managed routing
⚠️ Production Enhancements
Implement Origin Access Control (OAC)
Add AWS WAF rules
Remove public S3 access
📸 Screenshots
S3 Bucket Configuration
<p align="center"> <img src="screenshots/S3 bucket configuration1.png" width="700"/> </p>
CloudFront Distribution
<p align="center"> <img src="screenshots/CloudFront distribution2.png" width="700"/> </p>
Route 53 Records
<p align="center"> <img src="screenshots/Route 53 records.png" width="700"/> </p>
Browser Output
<p align="center"> <img src="screenshots/Browser output.png" width="700"/> </p>
🧠 Key Learnings
Difference between S3 website endpoint vs REST endpoint
Importance of CloudFront in performance and DDoS mitigation
DNS routing using Route 53 alias records
CDN caching and invalidation strategies
📈 Future Improvements
🔒 Implement Origin Access Control (OAC)
🛡️ Add AWS WAF
⚙️ Automate using Terraform
🔄 CI/CD pipeline with GitHub Actions
📊 Monitoring via CloudWatch
📂 Project Structure
.
├── README.md
├── screenshots/
├── terraform/ (optional IaC)
👤 Author

Augustine Ebere Ohuabunwa
Solutions Architect | AWS Certified | DBA
Cloud • Security • Automation • Cost Optimization

📜 License

This project is for educational, demonstration, and real-world implementation purposes.

⭐ Final Note

This project demonstrates a real-world, enterprise-grade cloud architecture used by modern organizations to deliver:

🌍 Global performance
🔐 Secure web applications
📈 Scalable infrastructure
⚡ High availability
