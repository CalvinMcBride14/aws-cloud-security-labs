##  Serverless Web Identity Federation Demo on AWS

This project demonstrates a simple **serverless application** that uses **Web Identity Federation** to authenticate users via Google, swap tokens using AWS Cognito, and securely access private images from S3.

I completed this project as part of an advanced AWS training series to deepen my understanding of **Identity Federation**, **IAM Roles**, and **temporary credential generation** for browser-based access.

---

##  Technologies & Services Used

- **Amazon S3** — for front-end app and image storage
- **Amazon CloudFront** — to serve content securely with HTTPS
- **AWS Cognito** — to manage identity pools and federated logins
- **IAM Roles & Policies** — to control access to private resources
- **Google OAuth 2.0** — as the Identity Provider (IdP)

---

## How It Works

1. The front-end app (HTML + JS) is hosted in a public S3 bucket and served via CloudFront.
2. Users sign in using a **Google account**, which returns an OAuth access token.
3. That token is exchanged via **Cognito Identity Pool** for temporary AWS credentials.
4. These credentials allow secure, **read-only access** to a private S3 bucket using **presigned URLs**.
5. Images from the private bucket are dynamically loaded in the browser.

---

## Project Breakdown

### Stage 1: Provision AWS Resources
- Used a CloudFormation stack to auto-deploy the required S3 buckets, CloudFront distribution, and IAM roles.
- Verified bucket policies and CloudFront configuration.

### Stage 2: Configure Google as IdP
- Created a **Google API Project** and set up the **OAuth 2.0 Client**.
- Configured the consent screen and added my CloudFront URL as an authorized JavaScript origin.

### Stage 3: Set Up Cognito Identity Pool
- Created a Cognito Federated Identity Pool linked to the Google Client ID.
- Attached IAM policies that grant read access to the private bucket.

### Stage 4: Connect Front-End to Cognito
- Updated `index.html` and `scripts.js` with:
  - My **Google Client ID**
  - My **Cognito Identity Pool ID**
  - The name of my **private S3 bucket**
- Uploaded the updated files back to the app bucket.

### Stage 5: Test the Application
- Opened the CloudFront URL in a browser.
- Signed in with Google and successfully loaded images from the private bucket.

---

## Screenshots & Proof of Work

All screenshots showing key steps (bucket setup, Cognito pool, CloudFront config, working app) are included in the [`/screenshots`](./screenshots) folder.

---

## What I Learned

- How to implement **Web Identity Federation** using Google and AWS Cognito
- How to securely expose **private S3 objects** to browser clients
- How IAM trust relationships and conditions enforce access control
- Hands-on experience with OAuth 2.0 in a real-world AWS use case

---

## 📎 Notes

> This project was inspired by a guided training series provided by [Adrian Cantrill](https://learn.cantrill.io), but all implementation, screenshots, and documentation reflect **my own hands-on work** and understanding.
