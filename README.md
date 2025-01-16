# APIドキュメント

このドキュメントでは、各APIの概要、エンドポイント、および認証方法について説明します。

## 目次
1. [認証](#認証)
2. [アクセス制限（レートリミット）](#アクセス制限レートリミット)
3. [文字コード](#文字コード)
4. [基本エンドポイント](#基本エンドポイント)
5. [エラーレスポンス](#エラーレスポンス)
6. [APIリスト](#apiリスト)
   - [コンタクト (customer)](#コンタクト-customer)
   - [アドレス帳 (customer_group)](#アドレス帳-customer_group)
   - [チケット (ticket)](#チケット-ticket)
   - [チャット](#チャット)
   - [受信箱 (message_box)](#受信箱-message_box)
   - [保留理由 (pending_reason)](#保留理由-pending_reason)
   - [ユーザー (user)](#ユーザー-user)
   - [チケット分類 (case_category)](#チケット分類-case_category)
   - [ラベル (label)](#ラベル-label)
   - [バッジ (badge)](#バッジ-badge)
   - [送信メール設定 (mail_account)](#送信メール設定-mail_account)
   - [メール (mail)](#メール-mail)
   - [テンプレート (template)](#テンプレート-template)
   - [コメント (comment)](#コメント-comment)
   - [添付ファイル](#添付ファイル)
   - [更新履歴](#更新履歴)

## 認証
すべてのAPIの利用にはアクセストークンが必要です。Re:lationのシステム設定画面からAPIトークンを発行し、リクエスト時に `Authorization` ヘッダに `Bearer <ACCESS_TOKEN>` をセットしてください。

```
curl \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  https://*.relationapp.jp/..
```

## アクセス制限（レートリミット）
API の利用には1分あたり60回のリクエスト制限があります。

| ヘッダ | 内容 |
|--------|------|
| X-RateLimit-Limit | 期間内（1分）でリクエストできる最大回数 |
| X-RateLimit-Remaining | アクセス可能な残り回数 |
| X-RateLimit-Reset | アクセス数がリセットされる時刻（UNIX時間） |

## 文字コード
リクエストおよびレスポンスの文字コードは `UTF-8` を使用します。

## 基本エンドポイント
APIの基本エンドポイントは以下の形式です。
```
https://<subdomain>.relationapp.jp/api/v2/<message_box_id>/
```
| パラメータ | 説明 |
|------------|------|
| subdomain | ご利用のサブドメイン |
| message_box_id | 受信箱ID（数字） |

## エラーレスポンス
| HTTP ステータスコード | エラー内容 |
|----------------|----------------------------------|
| 400 | パラメータに誤りがある |
| 401 | アクセストークンが存在しない、または無効 |
| 403 | レートリミットを超過 |
| 404 | リソースまたはエンドポイントが存在しない |
| 415 | 無効なフォーマット（Content-type に application/json が指定されていない） |
| 500 | サーバーエラー |
| 503 | メンテナンス中 |

## APIリスト

### [コンタクト (customer)](contact_api.md)
顧客情報の検索、登録、更新、削除を行います。

### [アドレス帳 (customer_group)](customer_group_api.md)
顧客グループの管理を行います。

### [チケット (ticket)](ticket_api.md)
サポートチケットの管理を行います。

### [チャット](chat_api.md)
チャットメッセージの取得を行います。

### [受信箱 (message_box)](message_box_api.md)
受信箱の管理を行います。

### [保留理由 (pending_reason)](pending_reason_api.md)
保留理由の取得を行います。

### [ユーザー (user)](user_api.md)
ユーザー情報の取得を行います。

### [チケット分類 (case_category)](case_category_api.md)
チケットの分類を管理します。

### [ラベル (label)](label_api.md)
ラベルを管理します。

### [バッジ (badge)](badge_api.md)
バッジ一覧取得

### [送信メール設定 (mail_account)](mail_account.md)
送信メール設定

### [メール (mail)](mail_api.md)
メール送信

### [テンプレート (template)](template_api.md)
テンプレート一覧取得
テンプレート検索

### [コメント (comment)](comment_api.md)
コメント

### [添付ファイル](attachment_api.md)
添付ファイルの取得を行います。

### [更新履歴](update_history.md)
APIの更新履歴を記録します。

---

## ライセンス
このドキュメントは [https://developer.ingage.jp/](https://developer.ingage.jp/) をマークダウンファイルに変更したものです。全ての権利は **株式会社インゲージ** に帰属します。

以上がAPIの概要です。詳細は各APIのエンドポイントを参照してください。

