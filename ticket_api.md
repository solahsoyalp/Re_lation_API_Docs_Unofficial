# チケット (ticket)

## ステータス (status_cd, status_cds)

| 文字列     | 意味      |
|------------|---------|
| open      | 未対応  |
| ongoing   | 保留    |
| closed    | 対応完了 |
| unwanted  | 対応不要 |
| trash     | ゴミ箱  |
| spam      | 迷惑メール |

---

## 色 (color_cd, color_cds)

| 文字列   | 意味    |
|----------|-------|
| red      | 赤    |
| orange   | オレンジ |
| yellow   | 黄色  |
| blue     | 青    |
| pink     | ピンク |

---

## 種別（チャネル） (method_cd, method_cds)

| 文字列      | 意味          |
|------------|--------------|
| mail       | メール        |
| tweet      | ツイート      |
| twitter_dm | Twitter DM   |
| record     | 応対メモ      |
| line       | LINE         |
| chatplus   | ChatPlus    |
| r_messe    | R-Messe     |
| yahoo      | Yahoo!ショッピング |
| sms        | SMS         |
| call       | 通話メモ      |

---

## メッセージの状態 (action_cd, action_cds)

| 文字列         | 意味            |
|--------------|----------------|
| received    | 受信          |
| sent        | 送信済み       |
| draft       | 下書き         |
| requested   | 承認依頼       |
| approved    | 承認済み       |
| rejected    | 差し戻し       |
| sending     | 送信中         |
| scheduled   | 予約済み       |
| send_error  | 送信エラー     |
| conversation | チャット中     |
| end_conversation | チャット終了 |

---

## コメントの種類 (comment_type)

| 文字列           | 意味                    |
|----------------|----------------------|
| comment       | コメント              |
| request       | 承認依頼              |
| approve       | 承認                  |
| reject        | 差戻し                |
| pullback      | 承認依頼キャンセル    |
| assign        | 担当者設定            |
| snooze        | スヌーズ              |
| canceled_snooze | スヌーズ（キャンセル済み） |

---

## チケットの検索

### リクエスト

```bash
curl -XPOST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/search \
  -d '{"status_cds":["open"]}'
```

### エンドポイント

```
POST https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/search
```

### レスポンス

```json
[
  {
    "ticket_id": 12,
    "assignee": null,
    "status_cd": "open",
    "created_at": "2020-10-23T05:07:25Z",
    "last_updated_at": "2020-10-23T05:07:25Z",
    "title": "subj9",
    "color_cd": null,
    "case_category_ids": [1, 2],
    "label_ids": [1, 2],
    "pending_reason_id": 1
  }
]
```

---

## チケットの取得

### リクエスト

```bash
curl -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/12
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/<ticket_id>
```

### レスポンス

```json
{
  "ticket_id": 12,
  "assignee": "admin",
  "status_cd": "closed",
  "created_at": "2020-10-23T05:07:25Z",
  "last_updated_at": "2020-11-13T01:39:38Z",
  "title": "応対メモ",
  "color_cd": null,
  "messages": [
    {
      "message_id": 31,
      "sent_at": "2020-11-13T01:39:22Z",
      "title": "応対メモ",
      "body": "<div>これは応対メモです。</div>",
      "method_cd": "record",
      "action_cd": "sent",
      "comments": [
        {
          "commenter": "y.suzuki",
          "comment_type": "request",
          "comment": "承認よろしくお願いします。",
          "commented_at": "2020-11-13T00:30:12Z"
        }
      ]
    }
  ]
}
```

---

## チケットの更新

### リクエスト

```bash
curl -H "Content-Type: application/json" \
 -H "Authorization: Bearer <ACCESS_TOKEN>" \
 -X PUT \
 https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/1 \
 -d '{
  "status_cd": "ongoing",
  "pending_reason_id": 1,
  "snooze_time": "2021-01-05T13:31:56+09:00",
  "label_ids": [1,2],
  "assignee": "mention name",
  "color_cd": "red",
  "case_category_ids": [1,2]
}'
```

### エンドポイント

```
PUT https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/<ticket_id>
```

---

## 応対メモ作成

### リクエスト

```bash
curl -XPOST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/records \
  -d '{"subject":"応対メモ","status_cd":"open",
       "operated_at":"2020-11-13T10:34:56+09:00","operator":"admin",
       "duration":300,"body":"応対メモ本文","icon_cd":"sales"}'
```

### エンドポイント

```
POST https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/records
```

### レスポンス

```json
{
  "message_id": 33,
  "ticket_id": 16
}
```
