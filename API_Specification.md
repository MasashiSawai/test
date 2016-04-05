# API
Synco API仕様書

## Version
1.0

## 1. API一覧

### ガントチャートAPI
- [ガントチャート取得]
- [ガントチャート保存]

### XXXX API
- [追記していく、、、]
 

## 2. 共通仕様
### 2.1. リクエスト
- TODO 以下を検討して決める
- 日本語の文字コード(UTF8?)
- セッションの有効期限(1日?)
- 他諸々

### 2.2. レスポンス
HTTP Response BodyはJSON形式
HTTP Status Codeは以下参照

<table>
  <tr>
    <td>Status Code</td>
    <td>意味</td>
  </tr>
  <tr>
    <td>200 ok</td>
    <td>Requestはサーバー上で処理された</td>
  </tr>
  <tr>
    <td>401 Unauthorized</td>
    <td>CSRFトークン不正など認証にかかるエラー</td>
  </tr>
  <tr>
    <td>404 Not Found</td>
    <td>該当のデータが存在しない</td>
  </tr>
  <tr>
    <td>500 Internal Server Error</td>
    <td>サーバーエラー発生</td>
  </tr>
</table>
