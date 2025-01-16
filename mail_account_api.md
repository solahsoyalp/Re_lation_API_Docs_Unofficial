# 送信メール設定 (mail_account)

## 送信メール設定一覧取得

### リクエスト

```bash
curl -X GET \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/mail_accounts
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/mail_accounts
```

### レスポンス

```json
[
  {
    "mail_account_id": 1,
    "name": "カスタマーサポートセンター",
    "email": "info1@example.com"
  },
  {
    "mail_account_id": 2,
    "name": "株式会社xxx",
    "email": "info2@example.com"
  }
]
```

---

## URI パラメータ

| 名前          | 内容               |
|--------------|------------------|
| subdomain    | ご利用のサブドメイン  |
| message_box_id | 受信箱ID（数字） |

---

## リクエストパラメータ (application/json)

| 名前      | 型      | 必須 | 内容                                  |
|----------|--------|----|-----------------------------------|
| per_page | integer |    | 1ページに表示する件数（デフォルト30, 最大100） |
| page     | integer |    | ページ番号（デフォルト1）         |

---

## レスポンス (application/json)

| 名前               | 型       | 必須 | 内容                      |
|------------------|--------|----|-------------------------|
| mail_account_id | integer | ○  | メールアカウントID         |
| name           | string  | ○  | メールアカウント名         |
| email          | string  | ○  | メールアカウントEmail      |
