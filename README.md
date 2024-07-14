# Photo-in

撮影タスクを自動的に割り振るアプリ

- [フロントエンド](https://github.com/pandaFive/photo-in-frontend)
- [バックエンド](https://github.com/pandaFive/photo-in-backend)

## サービスURL

https://photo-in-app.com/

### アドミンアクセス

Account name  
管理者

password  
password

### メンバーアクセス

Account name  
鈴木、高木、佐藤　など

password  
password

## 概要

タスクの概要が書かれたPDFをアップロードすることで、file名に含まれる分類に従ってタスクを自動的に割り振るアプリケーション。

## 使用技術

- Frontend: Next.js (eslint/prettier)
- Backend: Ruby on Rails (API mode/Rspec/rubocop ) + Nginx
- Infrastructure:
    AWS (Amplify/ECS Fargate/ECR/RDS/ALB/Route53), Docker & docker-compose & Dev Container
- Database: PostgreSQL

### 使用言語

- Ruby 3.3.0
- TypeScript

### Frontend (Next.js)

- aws-sdk
- mui
- eslint
- prettier
- jest

### Backend (Rails + Nginx)

- puma
- jwt
- rubocop
- rspec-rails
- factory_bot_rails

### Infrastructure

- Docker/docker-compose
- AWS
  - Frontend
    - Amplify
  - Backend
    - ECS Fargate
    - ECR
    - ALB
    - Route53
    - RDS(PostgreSQL)
  - Storage
    - S3
  - Other
    - ACM

### CI

- GitHub Actions

### Others

- Git, GitHub

## ER図

ER図を貼る

## インフラ構成図

インフラ構成図を貼る
