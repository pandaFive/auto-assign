# テーブル定義書

## 1. ER図

ER図  
![ER図](../images/er.jpg)

## 2. テーブル定義書

### 2.1. accounts テーブル

アカウント情報を扱うテーブル

| カラム名   | 意味             | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| ---------- | ---------------- | --- | --- | -------- | -------- | ----- | ------- |
| id         | アカウントID     | 〇  |     | bigint   | 〇       | 〇    |         |
| name       | アカウント名     |     |     | string   | 〇       |       |         |
| password   | パスワード       |     |     | string   | 〇       |       |         |
| capacity   | キャパシティ     |     |     | integer  |          |       |         |
| role       | 撮影者か管理者か |     |     | string   | 〇       |       |         |
| created_at | 作成日           |     |     | datetime | 〇       |       |         |
| updated_at | 更新日           |     |     | datetime | 〇       |       |         |

### 2.2. tasks テーブル

タスク情報を扱うテーブル

| カラム名    | 意味           | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| ----------- | -------------- | --- | --- | -------- | -------- | ----- | ------- |
| id          | タスクID       | 〇  |     | bigint   | 〇       | 〇    |         |
| title       | タスクタイトル |     |     | string   | 〇       |       |         |
| area_id     | エリアID       |     | 〇  | bigint   | 〇       |       |         |
| is_complete | 完了したか     |     |     | boolean  | 〇       |       | false   |
| created_at  | 作成日         |     |     | datetime | 〇       |       |         |
| updated_at  | 更新日         |     |     | datetime | 〇       |       |         |

### 2.3. area テーブル

エリア情報を扱うテーブル

| カラム名   | 意味     | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| ---------- | -------- | --- | --- | -------- | -------- | ----- | ------- |
| id         | エリアID | 〇  |     | bigint   | 〇       | 〇    |         |
| name       | エリア名 |     |     | string   | 〇       |       |         |
| created_at | 作成日   |     |     | datetime | 〇       |       |         |
| updated_at | 更新日   |     |     | datetime | 〇       |       |         |

### 2.4. tags テーブル

タグ情報を扱うテーブル

| カラム名   | 意味   | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| ---------- | ------ | --- | --- | -------- | -------- | ----- | ------- |
| id         | タグID | 〇  |     | bigint   | 〇       | 〇    |         |
| name       | タグ名 |     |     | string   | 〇       |       |         |
| created_at | 作成日 |     |     | datetime | 〇       |       |         |
| updated_at | 更新日 |     |     | datetime | 〇       |       |         |

### 2.5. account_area テーブル

アカウントが撮影に行けるエリアを設定するための。アカウントとエリアの中間アイテム

| カラム名   | 意味         | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| ---------- | ------------ | --- | --- | -------- | -------- | ----- | ------- |
| id         | ID           | 〇  |     | bigint   | 〇       | 〇    |         |
| account_id | アカウントID |     | 〇  | bigint   | 〇       |       |         |
| area_id    | エリアID     |     | 〇  | bigint   | 〇       |       |         |
| created_at | 作成日       |     |     | datetime | 〇       |       |         |
| updated_at | 更新日       |     |     | datetime | 〇       |       |         |

### 2.6. assign_cycles テーブル

あるタスクの1周分のアサイン情報を管理するテーブル

| カラム名   | 意味     | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| ---------- | -------- | --- | --- | -------- | -------- | ----- | ------- |
| id         | ID       | 〇  |     | bigint   | 〇       | 〇    |         |
| task_id    | タスクID |     | 〇  | bigint   | 〇       |       |         |
| created_at | 作成日   |     |     | datetime | 〇       |       |         |
| updated_at | 更新日   |     |     | datetime | 〇       |       |         |

### 2.7. assign_history テーブル

アサイン履歴を管理するテーブル

| カラム名        | 意味               | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| --------------- | ------------------ | --- | --- | -------- | -------- | ----- | ------- |
| id              | ID                 | 〇  |     | bigint   | 〇       | 〇    |         |
| account_id      | アカウントID       |     | 〇  | bigint   | 〇       |       |         |
| assign_cycle_id | アサインサイクルID |     | 〇  | bigint   | 〇       |       |         |
| created_at      | 作成日             |     |     | datetime | 〇       |       |         |
| updated_at      | 更新日             |     |     | datetime | 〇       |       |         |


### 2.8. ng_history テーブル

NG履歴を管理するテーブル

| カラム名        | 意味               | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| --------------- | ------------------ | --- | --- | -------- | -------- | ----- | ------- |
| id              | ID                 | 〇  |     | bigint   | 〇       | 〇    |         |
| account_id      | アカウントID       |     | 〇  | bigint   | 〇       |       |         |
| assign_cycle_id | アサインサイクルID |     | 〇  | bigint   | 〇       |       |         |
| created_at      | 作成日             |     |     | datetime | 〇       |       |         |
| updated_at      | 更新日             |     |     | datetime | 〇       |       |         |

### 2.9. tag_account テーブル

アカウントが持つタグを設定する,アカウントとタグの中間テーブル

| カラム名   | 意味         | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| ---------- | ------------ | --- | --- | -------- | -------- | ----- | ------- |
| id         | ID           | 〇  |     | bigint   | 〇       | 〇    |         |
| tag_id     | タグID       |     | 〇  | bigint   | 〇       |       |         |
| account_id | アカウントID |     | 〇  | bigint   | 〇       |       |         |
| created_at | 作成日       |     |     | datetime | 〇       |       |         |
| updated_at | 更新日       |     |     | datetime | 〇       |       |         |

### 2.10 tag_task

タスクが持つタグを設定する,タスクとタグの中間テーブル

| カラム名   | 意味     | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| ---------- | -------- | --- | --- | -------- | -------- | ----- | ------- |
| id         | ID       | 〇  |     | bigint   | 〇       | 〇    |         |
| tag_id     | タグID   |     | 〇  | bigint   | 〇       |       |         |
| task_id    | タスクID |     | 〇  | bigint   | 〇       |       |         |
| created_at | 作成日   |     |     | datetime | 〇       |       |         |
| updated_at | 更新日   |     |     | datetime | 〇       |       |         |

### 2.11 completed_tasks テーブル

タスクの完了履歴を管理するテーブル

| カラム名   | 意味         | PK  | FK  | データ型 | NOT NULL | INDEX | DEFAULT |
| ---------- | ------------ | --- | --- | -------- | -------- | ----- | ------- |
| id         | ID           | 〇  |     | bigint   | 〇       | 〇    |         |
| account_id | アカウントID |     | 〇  | bigint   | 〇       |       |         |
| task_id    | タスクID     |     | 〇  | bigint   | 〇       |       |         |
| created_at | 作成日       |     |     | datetime | 〇       |       |         |
| updated_at | 更新日       |     |     | datetime | 〇       |       |         |
