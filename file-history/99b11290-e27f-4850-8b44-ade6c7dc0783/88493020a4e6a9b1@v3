# CIマイグレーション廃止 & 手動マイグレーション手順書作成

## Context

同僚からのフィードバック:
- CIでmigrationを実行する必要がない（頻繁にやらない）
- CIでseedを実行するのはschema.sqlとは別にDDLを書くことになり破綻しやすい
- 手順書ベース + レビューで手動実行する運用に切り替える

現状、`db-migration.yaml`はdev/production両方の`deploy-backend-*.yaml`から呼ばれているが、どちらもコメントアウト済みで実質使われていない。

## 変更内容

### 1. `db-migration.yaml` を削除
- **ファイル**: `.github/workflows/db-migration.yaml`
- reusable workflowごと削除

### 2. `deploy-backend-dev.yaml` からmigration関連のコメントを削除
- **ファイル**: `.github/workflows/deploy-backend-dev.yaml`
- 行49-61のコメントアウトされたmigrationジョブを削除

### 3. `deploy-backend-production.yaml` からmigration関連のコメントを削除
- **ファイル**: `.github/workflows/deploy-backend-production.yaml`
- 行44-56のコメントアウトされたmigrationジョブを削除
- 行59の `# needs: migration` コメントを削除

### 4. マイグレーション手順書を作成
- **ファイル**: `docs/migration/README.md`
- 内容:
  - **前提条件**: 必要なツール（Cloud SQL Proxy, Prisma, psqldef）
  - **ローカル環境マイグレーション手順**
    - Prisma: `pnpm --filter backend prisma:migrate:deploy`
    - psqldef: `cd packages/api && make migrate`
  - **Dev環境マイグレーション手順**
    - Cloud SQL Proxy起動
    - Prisma（Node.js backend）: `DATABASE_URL=... pnpm prisma:migrate:deploy`
    - psqldef（Go backend）: `make migrate POSTGRES_HOST=... POSTGRES_USER=... POSTGRES_PASSWORD=...`
  - **Production環境マイグレーション手順**
    - 同上（接続先が異なる）
    - dry-runで確認 → レビュー → 適用
  - **運用ルール**
    - マイグレーション実行前にチームへ共有
    - @kodai にレビューをもらう
    - dry-runで確認してから適用
  - **Cloud SQL接続情報** (workflowファイルから抽出)
    - Dev: `utage3-dev:asia-northeast1:utage3`
    - Production: `utage3:asia-northeast1:utage3`

## 対象ファイル

| 操作 | ファイル |
|------|---------|
| 削除 | `.github/workflows/db-migration.yaml` |
| 編集 | `.github/workflows/deploy-backend-dev.yaml` |
| 編集 | `.github/workflows/deploy-backend-production.yaml` |
| 新規 | `docs/migration/README.md` |

## 検証

- `deploy-backend-dev.yaml`と`deploy-backend-production.yaml`にmigration関連の記述が残っていないことをgrepで確認
- 手順書の接続情報が既存のworkflowファイルと一致していることを確認
