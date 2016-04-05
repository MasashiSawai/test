# Synco API仕様書
Version 0.1 (2016/03/31)


## 1. API一覧

### ガントチャートAPI
- ガントチャート取得
- ガントチャート保存

### XXXX API
- [追記していく、、、]
 

## 2. 共通仕様
### 2.1. リクエスト
!!! TODO 以下を検討して決める
リクエストヘッダーで必須とするもの

| 名称 | 型 | 説明 |
|:--|:--|:--|
| X-Synco-Application | String | クライアント認証用の値を設ける？ |

!!! TODO 以下を検討して決める
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
    <td>http://domain/gantt/load/{project_id}</td>
  </tr>
  <tr>
    <td>メソッド</td>
    <td>GET</td>
  </tr>
</table>

!!! 
TODO 検討、URLは次のような形式にするか？
http://domain/api/v1/gantt/load/{project_id}


#### URLパラメータ

| パラメータ名 | 型 | 説明 |
|:--|:--|:--|
| project_id | Number | プロジェクトを特定するための値 |

#### レスポンス

| パラメータ名 | 型 | 説明 |
|:--|:--|:--|
| gantt | Gantt[] | ガントチャートの配列データ |
| timespan | Timespan | 本日の列をハイライトさせるオブジェクト |

レスポンス例
```
# データ取得成功
{"success":"ログインしました"}
# ログインに失敗した場合
{"errors":[{"message":"メールアドレスまたはパスワードが違います。"}]}
# セッションが切れた場合
{"errors":[{"message":"セッションがタイムアウトしました。もう一度ログインしてください。"}]}
```

### 3.1.2. ガントチャート保存




## 4. オブジェクト
ライブラリで用いられるオブジェクトなど、固有のものをまとめます。

### Gantt
| プロパティ名 | 型 | 説明 |
|:--|:--|:--|
| id | String | 後で |
| name | String | 後で |
| tasks | Task | 後で |

### Task
| プロパティ名 | 型 | 説明 |
|:--|:--|:--|
| id | String | 後で |
| name | String | 後で |

### Timespan
| プロパティ名 | 型 | 説明 |
|:--|:--|:--|
| ?? | ?? | 後で |
| ?? | ?? | 後で |










<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
////////////////////////////////////////////////
// example

| Left align | Right align | Center align |
|:-----------|------------:|:------------:|
| This       |        This |     This     |

