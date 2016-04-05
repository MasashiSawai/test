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
  <tr><td>Status Code</td><td>意味</td></tr>
  <tr><td>200 ok</td><td>Requestはサーバー上で処理された</td></tr>
  <tr><td>401 Unauthorized</td><td>CSRFトークン不正など認証にかかるエラー</td></tr>
  <tr><td>404 Not Found</td><td>該当のデータが存在しない</td></tr>
  <tr><td>500 Internal Server Error</td><td>サーバーエラー発生</td></tr>
</table>

レスポンスJSON例
```
{
  "result": true, // -> APIでの実行結果(共通)
  "Any_Data": {}, // -> APIからクライアントへ返却する値で(APIにより異なる)
  "message": ""   // -> ユーザーへ通知したいメッセージなど(共通)
}
```


## 3. 詳細仕様
### 3.1.1. ガントチャート取得
<table>
  <tr><td>URL</td><td>http://domain/gantt/load/{project_id}</td></tr>
  <tr><td>メソッド</td><td>GET</td></tr>
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
| timespan | Timespan[] | 本日の列をハイライトさせる配列データ |

レスポンス例
```
# データ取得成功
{
    "result":true,
    "message":"",
    "gantt":[
        {
            "id":"id_00001",
            "name":"Milestones",
            "height":"3em",
            "sortable":false,
            "classes":"gantt-row-milestone",
            "color":"#45607D",
            "tasks":[
                {
                    "name":"Kickoff",
                    "color":"#93C47D",
                    "from":"2013-10-06T06:00:00",
                    "to":"2013-10-06T07:00:00",
                    "data":"Can contain any custom data or object",
                    "id":"c1a2b140-2af0-a7b2-e206-193004ab3b88"
                },
                {
                (省略)行の中のタスクが繰り返す
                }
            ],
            "data":"Can contain any custom data or object"
        },
        {
            (省略)行が繰り返す
        }
    ],
    "timespan":[
        {
            "from":"2013-10-21T08:00:00",
            "to":"2013-10-25T15:00:00",
            "name":"Sprint 1 Timespan"
        }
    ]
}

# データ取得失敗
{
    "result":false,
    "message":"チャートデータの取得に失敗しました",
    "gantt":[],
    "timespan":[]
}
```

### 3.1.2. ガントチャート保存
<table>
  <tr><td>URL</td><td>http://domain/gantt/save/</td></tr>
  <tr><td>メソッド</td><td>POST</td></tr>
</table>

#### リクエストパラメータ

| パラメータ名 | 型 | 説明 |
|:--|:--|:--|
| project_id | Number | プロジェクトを特定するための値 |
| gantt | String | $scope.data をJSONエンコードした値 |
| _token | String | Laravelが出力したCSRFトークン値 |

#### レスポンス

| パラメータ名 | 型 | 説明 |
|:--|:--|:--|
| result | Bool | 実行結果 |
| message | String | ユーザーへ通知するメッセージ |

レスポンス例
```
# データ保存成功
{
    "result":true,
    "message":"チャートデータを保存しました"
}

# データ保存失敗
{
    "result":false,
    "message":"チャートデータの保存に失敗しました"
}
```



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

