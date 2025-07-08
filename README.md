
# 🌐 AWS CloudFront Demo with Amazon S3

This project demonstrates how to use **Amazon CloudFront** to cache and serve static content from an **Amazon S3 bucket** efficiently across the globe, reducing latency and improving performance.

---

## 📌 Features Covered

- ✅ Setup of an Amazon S3 bucket for hosting static assets
- ✅ Configuration of an AWS CloudFront distribution
- ✅ Cache behavior with TTL (Time to Live)
- ✅ Manual Cache Invalidation using the AWS Console
- ✅ Integration with AWS SSL/TLS, CloudWatch
- ✅ Use Case: Image delivery with version updates

---

## 🔧 Technologies Used

- **Amazon S3**
- **Amazon CloudFront**
- **AWS IAM (for access control)**
- **CloudWatch (monitoring)**
- **HTTPS (with SSL/TLS)**

---

## 📁 Project Structure

```
aws-cloudfront-demo/
├── README.md
├── screenshots/
│   ├── s3-upload.png
│   ├── cloudfront-config.png
│   ├── edge-access-url.png
│   ├── cache-invalidation.png
```

---

## 🚀 Getting Started

### 1. Create an S3 Bucket
- Go to the S3 Console.
- Create a new bucket with default settings.
- Upload a static file (`car.jpg`) into the bucket.

### 2. Configure S3 Bucket Policy

To allow public read access, use this policy (replace `your-bucket-name`):

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

### 3. Create a CloudFront Distribution

- Go to the CloudFront Console.
- Create a new distribution and set the **origin domain** as your S3 bucket.
- Leave "Origin Path" empty to cache everything.
- Enable compression.
- Allow HTTP and HTTPS (or enforce HTTPS for production).

### 4. Access the File

Once the distribution is deployed, use the generated domain:

```
https://your-distribution-id.cloudfront.net/car.jpg
```

---

## 🌀 Cache Behavior & Invalidation

- CloudFront caches objects for 24 hours by default.
- If you update the image (e.g., upload a red car instead of a blue one), the cache won’t update immediately.

### 🧹 To Invalidate Cache:
- Navigate to the **Invalidations** tab in the CloudFront console.
- Create a new invalidation:
  - To invalidate one file: `/car.jpg`
  - To invalidate all: `/*`

---

## 📷 Screenshots

Screenshots are available in the `screenshots/` folder for reference:
- S3 upload confirmation
- CloudFront setup
- Cache invalidation result

---

## ✅ Use Cases for CloudFront

| Use Case          | Example                              |
|------------------|--------------------------------------|
| Static Websites   | HTML, CSS, JS delivery               |
| Video on Demand   | Streaming pre-recorded content       |
| Media Delivery    | PDFs, images, and downloadable files |

---

## 📚 Resources

- [Amazon CloudFront Docs](https://docs.aws.amazon.com/cloudfront/)
- [AWS S3 Docs](https://docs.aws.amazon.com/s3/)
- [AWS CloudFront Pricing](https://aws.amazon.com/cloudfront/pricing/)

---

## 🙌 Final Words

CloudFront helps reduce latency by caching files closer to users around the globe. A great fit for static websites, APIs, or media-heavy applications.

🔗 Happy caching and building!
