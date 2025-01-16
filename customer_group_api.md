# アドレス帳 (customer_group)

## 一覧取得

### リクエスト

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
  },
  {
    "customer_group_id": 2,
    "name": "アドレス帳2",
    "message_box_ids": [1, 2],
    "last_updated_at": "2024-01-12T16:07:26Z"
  },
  {
    "customer_group_id": 3,
    "name": "アドレス帳3",
    "message_box_ids": [],
    "last_updated_at": "2024-01-12T16:07:22Z"
  }
]
```

---

## URI パラメータ

| 名前       | 内容               |
|-----------|------------------|
| subdomain | ご利用のサブドメイン |

---

## レスポンス (application/json)

| 名前              | 型             | 必須 | 内容                      |
|-----------------|--------------|----|-------------------------|
| customer_group_id | integer      | ○  | アドレス帳ID              |
| name            | string       | ○  | アドレス帳名              |
| message_box_ids | array[integer] | ○  | 紐づいている受信箱IDの配列 |
| last_updated_at | string       | ○  | 更新日時（ISO 8601 形式） |
