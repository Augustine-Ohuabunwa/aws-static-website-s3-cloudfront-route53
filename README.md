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
3. CloudFront Configuration
Origin: S3 website endpoint
Default root object: index.html
Viewer protocol: Redirect HTTP → HTTPS
Cache invalidation performed: /*
4. Route 53 DNS Routing
Created A (Alias) record
Routed domain → CloudFront distribution
🌍 Live Demo

👉 https://ausfrane.com

🔐 Security Deep Dive
Layer	Protection
CloudFront	AWS Shield (DDoS protection)
HTTPS	TLS encryption
DNS	Route 53 managed routing
⚠️ Production Enhancements (Planned)
AWS WAF integration
Private S3 bucket + Origin Access Control (OAC)
📸 Screenshots
Component	Preview
S3 Bucket	

CloudFront	

Route 53	

Live Site	
🧠 Key Learnings
Difference between S3 website endpoint vs REST endpoint
Importance of CloudFront in DDoS mitigation
DNS routing using Route 53 alias records
Cache invalidation strategies in CDN systems
📈 Future Improvements
🔒 Implement Origin Access Control (OAC) (remove public S3 access)
🛡️ Add AWS WAF rules
⚙️ Automate deployment using Terraform
🔄 CI/CD pipeline using GitHub Actions
📊 Monitoring via CloudWatch
📂 Project Structure
.
├── README.md
├── screenshots/
├── terraform/   (optional IaC)
👤 Author

Augustine Ohuabunwa
Cloud Engineer | DevOps Enthusiast
