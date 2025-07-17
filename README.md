# ☁️ AWS S3 Public Bucket Misconfiguration Lab (Cloud Security Project)

This hands-on lab simulates a **real-world AWS S3 security misconfiguration**, where an S3 bucket is made public—exposing sensitive data to the internet. The project demonstrates both the **vulnerability** and the **remediation**, following best practices in cloud security.

## 📌 Scenario

An S3 bucket was configured with **public access** enabled. A sensitive file (`secret.txt`) containing fake credentials was uploaded. This file became accessible to **anyone on the internet** without authentication.

This simulates a common mistake made by developers or misconfigured CI/CD pipelines, and is frequently exploited in real-world breaches.

## 🛠️ Lab Steps

### 1. Create S3 Bucket (Public Misconfiguration)
📸 Screenshot:  
![Public Access Unchecked](./screenshots/00-bucket-public-setting.png)

### 2. Upload Sensitive File
📸 Screenshot:  
![Uploading File](./screenshots/01-upload-file.png)

### 3. Apply Insecure Bucket Policy
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::insecure-demo-bucket-vaibhav/*"
    }
  ]
}
```
📸 Screenshot:  
![Insecure Policy](./screenshots/02-bucket-policy-public.png)

### 4. Access File from Internet (No Login)
📸 Screenshot:  
![Public File Access](./screenshots/03-public-access-browser.png)

## 🔐 Remediation

### 5. Remove Bucket Policy
📸 Screenshot:  
![Policy Removed](./screenshots/04-bucket-policy-removed.png)

### 6. Validate Fix (Access Denied from Internet)
📸 Screenshot:  
![Access Denied](./screenshots/05-access-denied-browser.png)

### 7. Bucket Overview in S3 Console
📸 Screenshot:  
![Bucket List View](./screenshots/06-bucket-list-view.png)

## ✅ Lessons Learned

- **Always keep “Block All Public Access” enabled** unless there's a justified reason.
- Never upload sensitive data into buckets with public permissions.
- Use **S3 Access Analyzer** and **IAM policies** to manage secure access.
- This kind of misconfiguration has led to real-world leaks (e.g., Uber, FedEx, Accenture).

## 🧠 What I Gained

- Hands-on AWS S3 configuration experience
- Understanding of public access vs. bucket policies
- How attackers discover misconfigured buckets
- How to remediate cloud misconfigurations like a pro

## 📁 Project Structure

```
aws-s3-security-lab/
├── secret.txt
├── README.md
└── screenshots/
    ├── 00-bucket-public-setting.png
    ├── 01-upload-file.png
    ├── 02-bucket-policy-public.png
    ├── 03-public-access-browser.png
    ├── 04-bucket-policy-removed.png
    ├── 05-access-denied-browser.png
    ├── 06-bucket-list-view.png
```

## 🚀 Author

**Vaibhav S** — aspiring cloud & cybersecurity engineer  
🔗 [LinkedIn](https://linkedin.com/in/vaibhav-satish)  
📍 Bangalore, India  



