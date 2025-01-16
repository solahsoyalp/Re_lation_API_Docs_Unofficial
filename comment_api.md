# コメント (comment)

## コメント作成

### リクエスト

```bash
curl -XPOST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/comments \
  -d '{"message_id": 1,"comment":"コメントの内容"}'
```

### エンドポイント

```
POST https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/comments
```

### 機能概要
メッセージに対してコメントを作成します。

---

## URI パラメータ

| 名前          | 内容               |
|--------------|------------------|
| subdomain    | ご利用のサブドメイン  |
| message_box_id | 受信箱ID（数字） |

---

## リクエストヘッダ

| ヘッダ         | 必須 | 内容 |
|--------------|----|-------------------------|
| Content-Type | ○  | `application/json` を指定します |

---

## リクエストパラメータ (application/json)

| 名前        | 型       | 必須 | 内容                        |
|------------|--------|----|---------------------------|
| message_id | integer | ○  | メッセージID                |
| comment    | string  | ○  | コメント内容（最大文字数: 1000） |

---

## レスポンス

| ステータスコード | 内容       |
|-------------|----------|
| 201 Created | 成功時に返ります |
| (レスポンスボディなし) |  |

