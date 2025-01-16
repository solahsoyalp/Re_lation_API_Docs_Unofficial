# テンプレート (template)

## テンプレート一覧取得

### リクエスト

```bash
curl -X GET \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/templates
```

### エンドポイント

```
GET https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/templates
```

### レスポンス

```json
[
  {
    "template_id": 1,
    "template_category_name": "テンプレートカテゴリ名",
    "template_name": "テンプレート名",
    "from": "sample_from@sample.com",
    "to": "sample_to_1@sample.com, sample_to_2@sample.com",
    "cc": "sample_cc_1@sample.com, sample_cc_2@sample.com",
    "bcc": "sample_bcc_1@sample.com, sample_bcc_2@sample.com",
    "title": "件名",
    "html_body": "<div>本文です</div>",
    "text_body": "本文です",
    "case_category_ids": [1, 2],
    "label_ids": [1, 2],
    "questionnaire_name": "アンケートメール名"
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

| 名前                   | 型       | 必須 | 内容                                  |
|----------------------|--------|----|-----------------------------------|
| per_page           | integer |    | 1ページに表示する件数（デフォルト10, 最大30） |
| page               | integer |    | ページ番号（デフォルト1）         |

---

## レスポンス (application/json)

| 名前                   | 型       | 必須 | 内容                      |
|----------------------|--------|----|-------------------------|
| template_id         | integer | ○  | テンプレートID             |
| template_category_name | string  | ○  | テンプレートカテゴリ名         |
| template_name       | string  | ○  | テンプレート名             |
| from               | string  | ○  | メールの From             |
| to                 | string  | ○  | メールの To               |
| cc                 | string  | ○  | メールの Cc               |
| bcc                | string  | ○  | メールの Bcc              |
| title              | string  | ○  | 件名                      |
| html_body          | string  | ○  | HTML形式の本文             |
| text_body          | string  | ○  | TEXT形式の本文             |
| case_category_ids  | array[integer] | ○  | チケット分類IDの配列         |
| label_ids          | array[integer] | ○  | ラベルIDの配列             |
| questionnaire_name | string  |    | アンケートメール名          |

---

## テンプレート検索

### リクエスト

```bash
curl -XPOST \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/templates/search \
  -d '{"template_category_name":"テンプレートカテゴリ名"}'
```

### エンドポイント

```
POST https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/templates/search
```

### レスポンス

```json
[
  {
    "template_id": 1,
    "template_category_name": "テンプレートカテゴリ名",
    "template_name": "テンプレート名",
    "from": "sample_from@sample.com",
    "to": "sample_to_1@sample.com, sample_to_2@sample.com",
    "cc": "sample_cc_1@sample.com, sample_cc_2@sample.com",
    "bcc": "sample_bcc_1@sample.com, sample_bcc_2@sample.com",
    "title": "件名",
    "html_body": "<div>本文です</div>",
    "text_body": "本文です",
    "case_category_ids": [1, 2],
    "label_ids": [1, 2],
    "questionnaire_name": "アンケートメール名"
  }
]
```
