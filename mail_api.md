# メール (mail)

## メール送信

### リクエスト (TEXT 形式・未対応)

```bash
curl -X POST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/mails \
  -d '{"status_cd":"open",
       "mail_account_id":1,
       "to":"abc@example.com","cc":"def@example.com","bcc":"ghi@example.com",
       "subject":"メール送信件名","body":"メール送信本文です。\n2行目\n3行目","is_html":false}'
```

### エンドポイント

```
POST https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/mails
```

### レスポンス

```json
{
    "message_id": 111,
    "ticket_id": 222
}
```

---

## URI パラメータ

| 名前          | 内容               |
|--------------|------------------|
| subdomain    | ご利用のサブドメイン  |
| message_box_id | 受信箱ID（数字） |

---

## リクエストパラメータ (application/json)

| 名前               | 型       | 必須 | 内容                                  |
|------------------|--------|----|-----------------------------------|
| status_cd       | string  | ○  | ステータス                          |
| pending_reason_id | integer |    | 保留理由ID（任意）                  |
| mail_account_id | integer | ○  | メールアカウントID                   |
| to             | string  | ○  | メールの To                         |
| cc             | string  |    | メールの Cc                         |
| bcc            | string  |    | メールの Bcc                        |
| subject        | string  | ○  | 件名（最大200文字）                   |
| body           | string  | ○  | 本文                                  |
| is_html        | boolean | ○  | HTML かどうか                        |

---

## メール返信

### リクエスト (TEXT 形式・未対応)

```bash
curl -X POST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/mails/reply \
  -d '{"message_id":1,
       "status_cd":"open",
       "mail_account_id":1,
       "to":"abc@example.com","cc":"efg@example.com","bcc":"ghi@example.com",
       "subject":"メール送信件名","body":"メール送信本文です。\n2行目\n3行目","is_html":false}'
```

### エンドポイント

```
POST https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/mails/reply
```

### レスポンス

```json
{
    "message_id": 111,
    "ticket_id": 222
}
```

---

## メール下書き作成

### リクエスト (TEXT 形式・未対応)

```bash
curl -X POST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/mails/draft \
  -d '{"message_id":1,
       "status_cd":"open",
       "mail_account_id":1,
       "to":"abc@example.com","cc":"efg@example.com","bcc":"ghi@example.com",
       "subject":"メール送信件名","body":"メール送信本文です。\n2行目\n3行目","is_html":false}'
```

### エンドポイント

```
POST https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/mails/draft
```

### レスポンス

```json
{
    "message_id": 111,
    "ticket_id": 222
}
```

---

## レスポンス (application/json)

| 名前         | 型       | 必須 | 内容                           |
|------------|--------|----|------------------------------|
| message_id | integer | ○  | メッセージID                    |
| ticket_id  | integer | ○  | チケットID                      |

