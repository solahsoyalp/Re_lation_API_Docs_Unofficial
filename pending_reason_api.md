# 保留理由 (pending_reason)

## スヌーズから復帰する日時（定義済み）

| 文字列        | 意味                  |
|--------------|----------------------|
| no_term      | 設定なし              |
| today        | 今日の17時            |
| tomorrow     | 明日の8時             |
| weekend      | 今週末の8時           |
| next_monday  | 来週月曜の8時         |
| next_week    | 1週間後の8時          |
| next_month   | 来月1日の8時          |
| after_month  | 1ヶ月後の8時         |

---

## 保留理由一覧取得

### リクエスト

```bash
curl -X GET \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/pending_reasons
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/pending_reasons
```

### レスポンス

```json
[
  {
    "name": "スヌーズ中",
    "snooze_term": "today",
    "pending_reason_id": 1,
    "is_snoozed": true
  },
  {
    "name": "確認待ち",
    "snooze_term": "no_term",
    "pending_reason_id": 2,
    "is_snoozed": false
  }
]
```

---

## URI パラメータ

| 名前          | 内容                 |
|--------------|----------------------|
| subdomain    | ご利用のサブドメイン  |
| message_box_id | 受信箱ID（数字）    |

---

## レスポンス (application/json)

| 名前               | 型       | 必須 | 内容                          |
|------------------|--------|----|-----------------------------|
| pending_reason_id | integer | ○  | 保留理由ID                    |
| name            | string  | ○  | 保留理由名                     |
| is_snoozed      | boolean | ○  | スヌーズするかどうか           |
| snooze_term     | string  |    | スヌーズから復帰する日時（定義済み） |

