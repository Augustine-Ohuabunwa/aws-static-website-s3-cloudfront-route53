# 🌐 Production-Ready Static Website Hosting on AWS  
**S3 + CloudFront + Route 53 + HTTPS + Edge Security**

---

## 📌 Overview

This project implements a **secure, scalable, and globally distributed static website hosting architecture** on AWS using industry best practices.

It leverages:
- **Amazon S3** for object storage
- **Amazon CloudFront** for global content delivery
- **Amazon Route 53** for DNS routing
- **AWS Certificate Manager (ACM)** for HTTPS encryption

---

## 🎯 Project Objectives

- Deliver static content with **low latency worldwide**
- Enforce **secure HTTPS communication**
- Provide **resilience against DDoS attacks**
- Demonstrate **production-grade cloud architecture**

---

## 🏗️ Architecture Diagram

![Architecture](screenshots/architecture.png)

### 🔄 Request Flow

1. User sends request to domain
2. DNS resolution via Route 53
3. Request routed to CloudFront edge location
4. CloudFront fetches content from S3 origin
5. Content cached and delivered globally

---

## ⚙️ Tech Stack

| Service | Purpose |
|--------|--------|
| Amazon S3 | Static file hosting |
| Amazon CloudFront | CDN + caching + security |
| Amazon Route 53 | Domain + DNS routing |
| AWS Certificate Manager | SSL/TLS certificates |

---

## 🚀 Key Features (What Makes This Stand Out)

### 🌍 Global Content Delivery
- Content cached at **CloudFront edge locations**
- Reduced latency for global users

### 🔐 End-to-End Security
- HTTPS enforced using ACM certificate
- CloudFront provides **AWS Shield Standard (DDoS protection)**

### ⚡ High Availability
- Fully serverless architecture
- No single point of failure

### 📦 Cost Optimization
- Pay-as-you-go pricing
- Efficient caching reduces origin requests

---

## 🛠️ Implementation Breakdown

### 1. Domain & SSL Setup
- Registered domain: **ausfrane.com**
- Created ACM certificate (us-east-1)
- Attached certificate to CloudFront

---

### 2. S3 Static Website Hosting

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

### 3. CloudFront Configuration

- **Origin:** S3 website endpoint  
- **Default root object:** `index.html`  
- **Viewer protocol:** Redirect HTTP → HTTPS  
- **Cache invalidation performed:** `/*`  

---

### 4. Route 53 DNS Routing

- Created **A (Alias) record**  
- Routed domain → CloudFront distribution  

---

## 🌍 Live Demo

👉 https://ausfrane.com  

---

## 🔐 Security Deep Dive

| Layer        | Protection                     |
|-------------|-------------------------------|
| CloudFront  | AWS Shield (DDoS protection)  |
| HTTPS       | TLS encryption                |
| DNS         | Route 53 managed routing      |

### ⚠️ Production Enhancements (Planned)

- AWS WAF integration  
- Private S3 bucket + Origin Access Control (OAC)  

---

## 📸 Screenshots

| Component   | Preview |
|------------|--------|
| S3 Bucket  | ![](screenshots/s3.png) |
| CloudFront | ![](screenshots/cloudfront.png) |
| Route 53   | ![](screenshots/route53.png) |
| Live Site  | ![](screenshots/output.png) |

---

## 🧠 Key Learnings

- Difference between **S3 website endpoint vs REST endpoint**  
- Importance of **CloudFront in DDoS mitigation**  
- DNS routing using **Route 53 alias records**  
- Cache invalidation strategies in CDN systems  

---

## 📈 Future Improvements

- 🔒 Implement **Origin Access Control (OAC)** (remove public S3 access)  
- 🛡️ Add **AWS WAF rules**  
- ⚙️ Automate deployment using **Terraform**  
- 🔄 CI/CD pipeline using GitHub Actions  
- 📊 Monitoring via CloudWatch  

---

## 📂 Project Structure

├── README.md
├── screenshots/
├── terraform/ (optional IaC)


---

## 👤 Author

**Augustine Ohuabunwa**  
Cloud Engineer | DevOps Enthusiast
