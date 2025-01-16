# ラベル (label)

## 色 (color)

色は `(色)_(明度)` の形式で表されます。（例: `gray_01`, `red_03`）  
明度は `01` 〜 `04` まであり、`01` が明るく `04` が暗い色です。

| 文字列   | 意味    |
|----------|-------|
| gray     | グレー  |
| brown    | 茶色   |
| red      | 赤    |
| orange   | オレンジ |
| green    | 緑    |
| blue     | 青    |
| purple   | 紫    |

---

## ラベル一覧取得

### リクエスト

```bash
curl -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/labels
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/labels
```

### レスポンス

```json
[
  {
    "label_id": 1,
    "name": "お問い合わせ",
    "color": "red_01",
    "parent_id": null
  },
  {
    "label_id": 2,
    "name": "お問い合わせ/顧客",
    "color": "red_02",
    "parent_id": 1
  }
]
```

---

## URI パラメータ

| 名前          | 内容               |
|--------------|------------------|
| subdomain    | ご利用のサブドメイン  |
| message_box_id | 受信箱ID（数字） |

---

## リクエストパラメータ (application/json)

| 名前      | 型      | 必須 | 内容                                  |
|----------|--------|----|-----------------------------------|
| per_page | integer |    | 1ページに表示する件数（デフォルト30, 最大100） |
| page     | integer |    | ページ番号（デフォルト1）         |

---

## レスポンス (application/json)

| 名前       | 型       | 必須 | 内容                           |
|----------|--------|----|------------------------------|
| label_id | integer | ○  | ラベルID                      |
| name     | string  | ○  | ラベル名 (`親/子/孫` の形式)  |
| color    | string  | ○  | 色 (`色_明度` の形式)          |
| parent_id | integer |    | 親ラベルID                   |

---

## ラベル登録

### リクエスト

```bash
curl -v -H "Content-type: application/json" \
 -H "Authorization: Bearer <ACCESS_TOKEN>" \
 -XPOST \
 https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/labels \
 -d '{"name": "ラベルの名前", "color": "gray_01", "parent_id": 1}'
```

### エンドポイント

```
POST https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/labels
```

### レスポンス

```json
{
  "label_id": 1
}
```

---

## ラベル更新

### リクエスト

```bash
curl -v -H "Content-type: application/json" \
 -H "Authorization: Bearer <ACCESS_TOKEN>" \
 -XPUT \
 https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/labels/<label_id> \
 -d '{"name": "ラベルの名前", "color": "gray_01", "parent_id": 1}'
```

### エンドポイント

```
PUT https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/labels/<label_id>
```

### レスポンス

成功の場合、`204 No Content` が返ります。

レスポンスボディはありません。

---

## 更新時の注意事項

- `parent_id` に `null` を設定すると、自身を親ラベルにできます。
