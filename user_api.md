# ユーザー (user)

## ユーザ状態 (status_cd)

| 文字列       | 意味                |
|------------|------------------|
| available  | 有効              |
| confirming | 本登録処理中       |
| locked     | アカウントロック中  |
| deleted    | 削除済み           |

---

## ユーザー一覧取得

### リクエスト

```bash
curl -X GET \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/users
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/users
```

### レスポンス

```json
[
  {
    "mention_name": "taro",
    "status_cd": "available",
    "first_name": "太郎",
    "last_name" : "大阪",
    "department_name": "本社",
    "employee_no": "100001",
    "email": "abc@example.com",
    "is_tenant_admin": true,
    "is_otp_required": false,
    "last_page_loaded_at": "2024-01-09T05:18:36Z"
  },
  {
    "mention_name": "hanako",
    "status_cd": "available",
    "first_name": "花子",
    "last_name" : "梅田",
    "department_name": "本社",
    "employee_no": "100002",
    "email": "efg@example.com",
    "is_tenant_admin": false,
    "is_otp_required": true,
    "last_page_loaded_at": "2024-01-09T05:20:36Z"
  }
]
```

---

## URI パラメータ

| 名前       | 内容               |
|-----------|------------------|
| subdomain | ご利用のサブドメイン |

---

## リクエストパラメータ (application/json)

| 名前      | 型      | 必須 | 内容                                  |
|----------|--------|----|-----------------------------------|
| per_page | integer |    | 1ページに表示する件数（デフォルト30, 最大100） |
| page     | integer |    | ページ番号（デフォルト1）         |

---

## レスポンス (application/json)

| 名前                | 型       | 必須 | 内容                           |
|-------------------|--------|----|------------------------------|
| mention_name      | string  | ○  | メンション名                   |
| status_cd        | string  | ○  | ユーザ状態                     |
| first_name       | string  | ○  | 名                             |
| last_name        | string  | ○  | 姓                             |
| department_name  | string  |    | 部署名                         |
| employee_no      | string  |    | 社員番号                        |
| email           | string  | ○  | メールアドレス                   |
| is_tenant_admin  | boolean | ○  | テナント管理者かどうか            |
| is_otp_required  | boolean | ○  | 多要素認証が有効かどうか          |
| last_page_loaded_at | string  |    | 最終アクセス日時（ISO 8601 形式） |
