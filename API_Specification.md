# API
Synco API仕様書

## Version
1.0

## 1. API一覧

### ガントチャートAPI
- ガントチャート取得
- ガントチャート保存

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

レスポンスJSON例
```
{
  "result": true, // -> APIでの実行結果(共通)
  "data": [],     // -> APIからクライアントへ返却する値で(APIにより異なる)
  "message": ""   // -> ユーザーへ通知したいメッセージなど(共通)
}
```

## 3. 詳細仕様
### 3.1.1. ガントチャート取得
<table>
  <tr>
    <td>URL</td>
    <td>http://domain/gantt/load</td>
  </tr>
  <tr>
    <td>メソッド</td>
    <td>POST</td>
  </tr>
</table>

!!! 
TODO 検討、URLは次のような形式にするか？
http://domain/api/v1/gantt/load


#### リクエストパラメータ

| パラメータ名 | 型 | 説明 |
|:-|:-|:-|
| project_id | Number | プロジェクトを特定するための値 |
| hoge | String | 他何かあれば追記 |









////////////////////////////////////////////////
// 記述例

| Left align | Right align | Center align |
|:-----------|------------:|:------------:|
| This       |        This |     This     |
| column     |      column |    column    |
| will       |        will |     will     |
| be         |          be |      be      |
| left       |       right |    center    |
| aligned    |     aligned |   aligned    |




