# チケット分類 (case_category)

## チケット分類一覧取得

### リクエスト

```bash
curl -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/case_categories
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/case_categories
```

### レスポンス

```json
[
  {
    "case_category_id": 1,
    "name": "お問い合わせ",
    "parent_id": null,
    "archived": false
  },
  {
    "case_category_id": 2,
    "name": "お問い合わせ > 顧客",
    "parent_id": 1,
    "archived": true
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

| 名前              | 型       | 必須 | 内容                           |
|-----------------|--------|----|------------------------------|
| case_category_id | integer | ○  | チケット分類ID                 |
| name           | string  | ○  | チケット分類名 (`親 > 子 > 孫` の形式) |
| parent_id      | integer |    | 親チケット分類ID               |
| archived       | boolean |    | アーカイブされているかどうか     |

---

## チケット分類登録

### リクエスト

```bash
curl -v -H "Content-type: application/json" \
 -H "Authorization: Bearer <ACCESS_TOKEN>" \
 -XPOST \
 https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/case_categories \
 -d '{"name": "チケット分類の名前", "parent_id": 1}'
```

### エンドポイント

```
POST https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/case_categories
```

### レスポンス

```json
{
  "case_category_id": 1
}
```

---

## チケット分類更新

### リクエスト

```bash
curl -v -H "Content-type: application/json" \
 -H "Authorization: Bearer <ACCESS_TOKEN>" \
 -XPUT \
 https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/case_categories/1 \
 -d '{"name": "チケット分類の名前", "parent_id": 1, "archived": true }'
```

### エンドポイント

```
PUT https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/case_categories/<case_category_id>
```

### レスポンス

成功の場合、`204 No Content` が返ります。

レスポンスボディはありません。

---

## 更新時の注意事項

### アーカイブ時の注意点

- 更新するチケット分類に子チケット分類や孫チケット分類が存在する場合、それらもアーカイブされます。

### アーカイブ復活時の注意点

- 親チケット分類がアーカイブされている場合、その分類は復活できません。

