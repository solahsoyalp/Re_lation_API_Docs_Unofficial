# 受信箱 (message_box)

## 受信箱一覧取得

### リクエスト

```bash
curl -H 'Authorization: Bearer <ACCESS_TOKEN>' \
 https://<subdomain>.relationapp.jp/api/v2/message_boxes
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/message_boxes
```

### レスポンス

```json
[
  {
    "name": "受信箱1",
    "color": "green",
    "message_box_id": 1,
    "last_updated_at": "2021-01-05T13:31:56Z",
    "customer_group_id": 1
  },
  {
    "name": "受信箱2",
    "color": "orange",
    "message_box_id": 2,
    "last_updated_at": "2021-01-12T16:07:26Z",
    "customer_group_id": 2
  },
  {
    "name": "受信箱3",
    "color": "blue",
    "message_box_id": 3,
    "last_updated_at": "2021-01-12T16:07:22Z",
    "customer_group_id": 3
  }
]
```

---

## URI パラメータ

| 名前       | 内容             |
|-----------|----------------|
| subdomain | ご利用のサブドメイン |

---

## レスポンス (application/json)

| 名前              | 型       | 必須 | 内容                                                   |
|-----------------|--------|----|------------------------------------------------------|
| message_box_id  | integer | ○  | 受信箱ID                                              |
| name           | string  | ○  | 受信箱名                                              |
| color         | string  | ○  | 受信箱の色 (`red`, `orange`, `green`, `blue`, `purple`, `brown`) |
| last_updated_at | string  | ○  | 更新日時（ISO 8601 形式）                             |
| customer_group_id | integer | ○  | アドレス帳ID                                          |
