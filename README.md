<div align="center">
  <img src="https://raw.githubusercontent.com/your-username/your-repo/main/assets/header-light.svg#gh-light-mode-only" alt="Serverless Feedback Form" width="100%">
  <img src="https://raw.githubusercontent.com/your-username/your-repo/main/assets/header-dark.svg#gh-dark-mode-only" alt="Serverless Feedback Form" width="100%">
  
  # 📬 Serverless Feedback Form on AWS
  
  **A production-ready, cloud-native feedback system with PDF uploads & email alerts**
  
  [![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)](https://aws.amazon.com)
  [![Serverless](https://img.shields.io/badge/Serverless-FF6F61?style=for-the-badge&logo=serverless&logoColor=white)](https://www.serverless.com)
  [![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/features/actions)
  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
  
  <p align="center">
    <b>English</b> | <a href="#spanish">Español</a> | <a href="#french">Français</a>
  </p>
</div>

---

## ✨ Overview

Build a **real-world, serverless AWS project** that lets users submit feedback with optional PDF uploads — delivering admin alerts, secure storage, and fully automated deployment. Perfect for learning cloud architecture or as a template for production feedback systems.

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="https://img.icons8.com/fluency/48/000000/submit-progress.png"/><br/>
        <sub><b>1. User submits</b><br/>feedback + PDF</sub>
      </td>
      <td align="center">➡️</td>
      <td align="center">
        <img src="https://img.icons8.com/fluency/48/000000/api.png"/><br/>
        <sub><b>2. API Gateway</b><br/>REST endpoint</sub>
      </td>
      <td align="center">➡️</td>
      <td align="center">
        <img src="https://img.icons8.com/fluency/48/000000/lambda.png"/><br/>
        <sub><b>3. Lambda</b><br/>Python handler</sub>
      </td>
      <td align="center">➡️</td>
      <td align="center">
        <img src="https://img.icons8.com/fluency/48/000000/dynamodb.png"/><br/>
        <sub><b>4. DynamoDB</b><br/>Store data</sub>
      </td>
    </tr>
  </table>
</div>

## ✅ Features

<div align="center">
  <table>
    <thead>
      <tr>
        <th width="33%">📋 Core Functionality</th>
        <th width="33%">🔒 Security</th>
        <th width="33%">🚀 DevOps</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          • Feedback form with Name, Email, Message<br/>
          • PDF upload support (base64 encoding)<br/>
          • Data stored in DynamoDB<br/>
          • Emails via Amazon SES
        </td>
        <td>
          • Private S3 bucket for PDFs<br/>
          • IAM roles with least privilege<br/>
          • CORS-enabled API Gateway<br/>
          • No public exposure of Lambda
        </td>
        <td>
          • CI/CD with GitHub Actions<br/>
          • CloudFront invalidation<br/>
          • Infrastructure as Code ready<br/>
          • Zero-downtime deployments
        </td>
      </tr>
    </tbody>
  </table>
</div>

## 🏗️ Architecture

```mermaid
graph TB
    subgraph "🌍 User"
        A[Browser] --> B[CloudFront CDN]
    end
    
    subgraph "📦 Frontend Hosting"
        B --> C[S3 Bucket<br/>index.html]
    end
    
    subgraph "⚡ API Layer"
        A --> D[API Gateway<br/>POST /submit]
        D --> E[Lambda Function<br/>submit_feedback.py]
    end
    
    subgraph "🗄️ Storage & Notifications"
        E --> F[DynamoDB<br/>Feedback Table]
        E --> G[S3 Bucket<br/>PDF Uploads]
        E --> H[Amazon SES<br/>Email Notification]
    end
    
    subgraph "🔄 CI/CD Pipeline"
        I[GitHub Push<br/>main branch] --> J[GitHub Actions]
        J --> K[S3 Sync<br/>frontend/]
        J --> L[CloudFront<br/>Invalidation]
    end
    
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style D fill:#bbf,stroke:#333,stroke-width:2px
    style E fill:#bfb,stroke:#333,stroke-width:2px
    style F fill:#fbb,stroke:#333,stroke-width:2px
    style G fill:#fbb,stroke:#333,stroke-width:2px
    style H fill:#fbb,stroke:#333,stroke-width:2px
    style J fill:#ff9,stroke:#333,stroke-width:2px
