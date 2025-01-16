# チャット (chat)

## 会話種別

| 種別                     | 内容               |
|-------------------------|------------------|
| text                   | テキスト         |
| file                   | ファイル         |
| image                  | 画像             |
| video                  | 動画             |
| audio                  | 音声             |
| location               | 位置情報         |
| sticker                | スタンプ         |
| chatplus_textform      | テキストフォーム |
| chatplus_carousel      | カルーセル       |
| chatplus_chatbot       | ChatPlusパーツ   |
| chatplus_imagemap      | イメージマップ   |

---

## ChatPlus取得

### リクエスト

```bash
curl -XPOST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/<ticket_id>/messages/<message_id>/chatplus
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/<ticket_id>/messages/<message_id>/chatplus
```

### レスポンス

```json
{
  "account": "test-account",
  "account_key": "xxxxxxxx",
  "email": "test@example.com",
  "company_name": "ingage",
  "site": "chatplus_site",
  "conversations": [
    {
      "chatplus_conversation_id": 1,
      "action_cd": "received",
      "speaker_name": "太郎",
      "sent_by": null,
      "auto_send": false,
      "sent_at": "2024-04-05T13:30:00Z",
      "conversation_type": "text",
      "note": "チャットの発言内容1",
      "file_name": null
    }
  ]
}
```

---

## Yahoo!ショッピング取得

### リクエスト

```bash
curl -XPOST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/<ticket_id>/messages/<message_id>/yahoo
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/<ticket_id>/messages/<message_id>/yahoo
```

### レスポンス

```json
{
  "account": "test-account",
  "store_account": "xxxx-xxxxxxxx",
  "email": "test@eample.com",
  "inquiry_status": "未完了",
  "inquiry_kind": "注文前（非公開）",
  "inquiry_category": "その他ストアへの連絡事項",
  "order_id": "xxxx-xxxxxxx_xxxxxxx",
  "order_url": "https://xxxx.xxxxxxxx.xxxxx.xx.xx/xxxxxxx.xxxx",
  "item_number": "item_number",
  "item_url": "https://xxxx.xxxxxxxx.xxxxx.xx.xx/xxxxxxx/xxxxxxx.xxxx",
  "conversations": [
    {
      "yahoo_conversation_id": 1,
      "action_cd": "received",
      "speaker_name": "太郎",
      "sent_by": null,
      "sent_at": "2024-04-05T13:30:00Z",
      "conversation_type": "テキスト",
      "note": "チャットの発言内容1",
      "file_name": null
    }
  ]
}
```

---

## R-Messe取得

### リクエスト

```bash
curl -XPOST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/<ticket_id>/messages/<message_id>/r_messe
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/<ticket_id>/messages/<message_id>/r_messe
```

### レスポンス

```json
{
  "account": "test-account",
  "email": "test@example.com",
  "inquiry_status": "完了",
  "inquiry_category": "配送",
  "inquiry_type": "店舗問い合わせ",
  "inquiry_number": "xxxxxxx-xxxxxxxx-xx",
  "inquiry_url": "https://xxxxxx.xxx.xxxxxxx.xx.xx/xxxxxxx/xxxxxxxx-xxxxxxxx-xx",
  "order_number": "xxxxxxx_xxxxxxx",
  "item_number": "1",
  "item_name": "商品A",
  "item_url": "https://xxxx.xxxxxxx.xx.xx/xxxxxxxxxxxxxx/",
  "conversations": [
    {
      "r_messe_conversation_id": 1,
      "action_cd": "received",
      "speaker_name": "太郎",
      "sent_by": null,
      "sent_at": "2024-04-05T13:30:00Z",
      "conversation_type": "text",
      "note": "チャットの発言内容1",
      "file_name": null
    }
  ]
}
```

---

## LINE取得

### リクエスト

```bash
curl -XPOST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/<ticket_id>/messages/<message_id>/line
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/tickets/<ticket_id>/messages/<message_id>/line
```

### レスポンス

```json
{
  "account": "test-account",
  "channel_id": "xxxxxxxxxx",
  "group_name": "テストグループ名<xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx>",
  "conversations": [
    {
      "line_conversation_id": 1,
      "action_cd": "received",
      "speaker_name": "太郎",
      "sent_by": null,
      "auto_send": false,
      "sent_at": "2024-04-05T13:30:00Z",
      "conversation_type": "text",
      "note": "チャットの発言内容1",
      "file_name": null
    }
  ]
}
```
