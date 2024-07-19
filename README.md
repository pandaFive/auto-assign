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

ER図  
![ER図](./images/er.jpg)

## インフラ構成図

インフラ構成図  
![インフラ構成図](./images//infrastructure.jpg)

## 機能一覧

### Member側機能

#### ログイン機能

- jwtを用いたログイン

#### アサインタスク確認機能

- アサインされたタスクを一覧表示
- PDFのURLを取得しPDFを表示する機能
- アサインされたタスクをNGする機能
- アサインされたタスクの完了登録する機能
- タスクにコメントを登録する機能
- アサインされたタスクをエリアかアサイン日でソートする機能

### Admin側機能

#### ログイン機能

- jwtを用いたログイン

#### ダッシュボード

- タスク登録機能
- 完了タスクチャート表示
- 日達成タスク数表示機能
- member簡易データ表、表示

#### member管理

- アカウント登録機能
- アカウント削除機能
- member 詳細表示機能

#### タスク管理

- NGされたタスクの再アサイン機能
- タスクのコメント登録機能
- PDFのURLを取得しPDFを表示する機能
- タスクのソート機能
- NGタスクの抽出機能

## 工夫

<details>
<summary>1. データベースの効率化</summary>

- 正規化
- `account_areas`などの中間テーブルを用いた最適化
</details>

<details>
<summary>2. ユーザビリティ</summary>

- 表やチャート、グラフを用いたデータの可視化
- インタラクティブなUI
- 一画面内の要素数の削減

</details>

<details>
<summary>3. GitHub Actions</summary>

- GitHub Actionsを用いたCIの構築
- push前のテスト通過の必須化
</details>

<details>
<summary>4. セキュリティ</summary>

- APIへの通信を行う関数をserverサイド
- AWSのセキュリティグループを用いたアクセス制限
</details>

<details>
<summary>5. 開発環境</summary>

- Dockerを用いてコンテナ化
- Dev Containerによる開発環境の作成
</details>
