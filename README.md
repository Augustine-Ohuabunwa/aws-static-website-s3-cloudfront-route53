🌐 Static Website Hosting on AWS (S3 + CloudFront + Route 53)

📌 Project Overview



This project demonstrates how to host a static website using Amazon S3, deliver it globally via Amazon CloudFront, and map it to a custom domain using Amazon Route 53, with SSL/TLS encryption for secure access.



The architecture improves:



Performance (low latency via CDN)

Security (HTTPS + DDoS mitigation via CloudFront)

Scalability (serverless infrastructure)

🏗️ Architecture

User → Route 53 (DNS)

&#x20;    → CloudFront (CDN + SSL + DDoS Protection)

&#x20;    → S3 Bucket (Static Website Hosting)

⚙️ Technologies Used

Amazon S3 (Static Website Hosting)

Amazon CloudFront (Content Delivery Network)

Amazon Route 53 (DNS Management)

AWS Certificate Manager (SSL/TLS Certificate)

🚀 Implementation Steps

1\. Domain \& SSL Certificate

Registered domain: ausfrane.com

Created SSL certificate using AWS Certificate Manager

Certificate attached to CloudFront distribution

2\. S3 Bucket Configuration

Bucket Name: eldijove123

Region: us-east-1

Steps:

Uploaded website files (index.html)

Disabled Block Public Access

Added bucket policy:

{

&#x20; "Version": "2012-10-17",

&#x20; "Statement": \[

&#x20;   {

&#x20;     "Sid": "PublicReadGetObject",

&#x20;     "Effect": "Allow",

&#x20;     "Principal": "\*",

&#x20;     "Action": "s3:GetObject",

&#x20;     "Resource": "arn:aws:s3:::eldijove123/\*"

&#x20;   }

&#x20; ]

}

3\. Enable Static Website Hosting

Enabled in S3 → Properties

Index document: index.html

4\. CloudFront Distribution Setup

Key Configurations:

Origin: S3 Bucket

Origin Type: Website Endpoint

Default Root Object: index.html

Viewer Protocol Policy: Redirect HTTP to HTTPS

SSL Certificate: Attached from ACM

Additional Steps:

Created distribution



Ran cache invalidation:



/\*

5\. Route 53 Configuration

Steps:

Navigated to Hosted Zone: ausfrane.com

Created A Record (Alias)

Record Details:

Type: A (IPv4)

Alias Target: CloudFront Distribution

Routing Policy: Simple

6\. Testing



Accessed website via:



https://ausfrane.com

Confirmed:

Website loads successfully

HTTPS is active

Content delivered via CloudFront

🔐 Security Considerations

HTTPS enforced via SSL/TLS

CloudFront provides:

DDoS protection (AWS Shield Standard)

Edge caching for reduced attack surface

(Optional for production)

AWS WAF integration recommended

📈 Key Benefits

Global Performance: Cached at edge locations

High Availability: Fully managed AWS services

Cost Efficiency: Pay-as-you-go model

Security: Encrypted traffic + AWS Shield protection

📸 Screenshots (Optional)



Add screenshots here:



S3 bucket configuration

CloudFront distribution

Route 53 records

Final website output

🧠 Lessons Learned

Importance of using S3 website endpoint with CloudFront

Proper configuration of bucket policies

DNS routing using Route 53 alias records

Role of CloudFront in security and performance optimization

📚 Future Improvements

Integrate AWS WAF for advanced security

Use CI/CD pipeline (e.g., GitHub Actions)

Automate deployment using Terraform or CloudFormation

Enable logging and monitoring (CloudWatch)

👤 Author



Your Name

Cloud / DevOps Enthusiast

