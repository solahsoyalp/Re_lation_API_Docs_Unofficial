# 添付ファイル (Attachments)

## メッセージ添付ファイルダウンロードURL発行

### リクエスト

```bash
curl -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/messages/attachments/<attachment_id>
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/messages/attachments/<attachment_id>
```

### 機能概要
メッセージに添付されているファイル1件をダウンロードできる URL を発行します。  
発行された URL に別途 GET アクセスしてファイルダウンロードしてください。  
URL には有効期限があるので期限内にダウンロードリクエストを開始してください（ダウンロードレスポンス終了までの期限ではありません）。

---

## URI パラメータ

| 名前           | 内容               |
|--------------|------------------|
| subdomain    | ご利用のサブドメイン  |
| message_box_id | 受信箱ID（数字） |
| attachment_id  | メッセージ添付ファイルID（数字） |

---

## レスポンス (application/json)

| 名前           | 型       | 必須 | 内容                                         |
|--------------|--------|----|------------------------------------------|
| url         | string  | ○  | 発行された添付ファイルダウンロード用URL (GET アクセスでダウンロード可) |
| file_name   | string  | ○  | 添付ファイル名                                 |
| expires_in_sec | integer | ○  | ダウンロード可能な有効期間（秒） (期限内にダウンロード開始必要) |

---

### レスポンス例

```json
{
  "url": "https://example.com/presigned-url",
  "file_name": "sample.pdf",
  "expires_in_sec": 30
}
```
