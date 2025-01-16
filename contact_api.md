# コンタクト (customer)

## 検索

### リクエスト

```bash
curl -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  "https://<subdomain>.relationapp.jp/api/v2/customer_groups/<customer_group_id>/customers/search?customer_ids[]=1&gender_cds[]=1&system_id1s[]=12345&default_assignees[]=user1&emails[]=example1%40email.com&emails[]=example2%40email.com&emails[]=example3%40email.com&tels[]=09012345678&badge_ids[]=101"
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/customer_groups/:customer_group_id/customers/search
```

### URI パラメータ

| 名前               | 内容                         |
|-------------------|---------------------------|
| subdomain        | ご利用のサブドメイン        |
| customer_group_id | アドレス帳ID（数字）        |

### クエリパラメータ

| 名前              | 型              | 必須 | 内容                        |
|------------------|---------------|----|-----------------------------|
| customer_ids     | array[integer] |    | 顧客IDの配列                |
| gender_cds       | array[integer] |    | 性別コードの配列 (1: 男性, 2: 女性, 9: 不明) |
| system_id1s      | array[string]  |    | 顧客コードの配列            |
| default_assignees | array[string]  |    | 担当者のメンション名の配列   |
| emails          | array[string]  |    | メールアドレスの配列（部分一致検索対応） |
| tels            | array[string]  |    | 電話番号の配列（部分一致検索対応） |
| badge_ids       | array[integer] |    | バッジIDの配列              |
| per_page        | integer        |    | ページごとの件数 (1-50)     |
| page           | integer        |    | ページ番号 (1以上)         |

### レスポンス (application/json)

| 名前               | 型              | 必須 | 内容                        |
|------------------|---------------|----|-----------------------------|
| customer_id     | integer       | ○  | 顧客ID                     |
| name           | string        | ○  | 顧客名                      |
| gender_cd      | integer       |    | 性別コード (1: 男性, 2: 女性, 9: 不明) |
| system_id1     | string        |    | 顧客コード                   |
| default_assignee_id | integer       |    | 担当者ID                   |
| emails         | array[string]  |    | メールアドレスの配列         |
| tels           | array[string]  |    | 電話番号の配列               |
| badge_ids      | array[integer] |    | バッジIDの配列              |
| last_updated_at | string        | ○  | 更新日時（ISO 8601 形式）   |

---

## 登録

### リクエスト

```bash
curl -v -H "Content-type: application/json" \
 -H "Authorization: Bearer <ACCESS_TOKEN>" \
 -XPOST \
 https://<subdomain>.relationapp.jp/api/v2/customer_groups/<customer_group_id>/customers/create \
 -d '{"last_name": "大阪", "first_name": "太郎", "last_name_kana": "おおさか", "first_name_kana": "たろう", "company_name": "株式会社インゲージ", "title": "執行役員", "url": "https://ingage.jp/", "gender_cd": 1, "default_assignee": "taro", "emails":[ { "email":"osaka@example.com" } ], "archived_emails":[ { "email":"archived_osaka@example.com" } ], "tels":[ { "tel": "09000000000" } ], "archived_tels":[ { "tel": "09011111111" } ], "badge_ids":[ 1, 2 ], "system_id1": "EMP0001" }'
```

### エンドポイント

```
POST https://<subdomain>.relationapp.jp/api/v2/customer_groups/<customer_group_id>/customers/create
```

### リクエストヘッダ

| ヘッダ         | 必須 | 内容                              |
|--------------|----|--------------------------------|
| Content-Type | ○  | application/json を指定します |

---

## 取得 (system_id1 をキーに)

### リクエスト

```bash
curl -H 'Authorization: Bearer <ACCESS_TOKEN>' \
 https://<subdomain>.relationapp.jp/api/v2/customer_groups/<customer_group_id>/customers/system_id1/EMP0001
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/customer_groups/<customer_group_id>/customers/system_id1/<system_id1>
```

### レスポンス

```json
{
  "customer_id": 1,
  "last_name": "大阪",
  "first_name": "太郎",
  "company_name": "株式会社インゲージ",
  "gender_cd": 1,
  "url": "https://ingage.jp/",
  "system_id1": "EMP0001",
  "emails": [
    { "email": "osaka@example.com" }
  ],
  "badge_ids": [1, 2]
}
```

---

## 削除 (system_id1 をキーに)

### リクエスト

```bash
curl -X DELETE -H 'Authorization: Bearer <ACCESS_TOKEN>' \
 https://<subdomain>.relationapp.jp/api/v2/customer_groups/<customer_group_id>/customers/system_id1/EMP0001
```

### エンドポイント

```
DELETE https://<subdomain>.relationapp.jp/api/v2/customer_groups/<customer_group_id>/customers/system_id1/<system_id1>
```

---

## アドレス帳 (customer_group)

### 一覧取得

```bash
curl -H 'Authorization: Bearer <ACCESS_TOKEN>' \
 https://<subdomain>.relationapp.jp/api/v2/customer_groups
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/customer_groups
```

### レスポンス

```json
[
  {
    "customer_group_id": 1,
    "name": "アドレス帳1",
    "message_box_ids": [1],
    "last_updated_at": "2024-01-05T13:31:56Z"
  }
]
```
