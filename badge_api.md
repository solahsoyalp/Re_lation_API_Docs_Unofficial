# バッジ (badge)

## バッジ一覧取得

### リクエスト

```bash
curl -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  https://<subdomain>.relationapp.jp/api/v2/customer_groups/<customer_group_id>/badges
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/customer_groups/<customer_group_id>/badges
```

### レスポンス

```json
[
  {
    "badge_id": 1,
    "name": "VIP"
  },
  {
    "badge_id": 2,
    "name": "要注意"
  }
]
```

---

## URI パラメータ

| 名前              | 内容               |
|-----------------|------------------|
| subdomain       | ご利用のサブドメイン  |
| customer_group_id | アドレス帳ID（数字） |

---

## リクエストパラメータ (application/json)

| 名前      | 型      | 必須 | 内容                                  |
|----------|--------|----|-----------------------------------|
| per_page | integer |    | 1ページに表示する件数（デフォルト30, 最大100） |
| page     | integer |    | ページ番号（デフォルト1）         |

---

## レスポンス (application/json)

| 名前       | 型       | 必須 | 内容      |
|----------|--------|----|---------|
| badge_id | integer | ○  | バッジID  |
| name     | string  | ○  | バッジ名  |
