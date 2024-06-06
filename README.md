## GraphQL参考記事
- [Notion](https://pinto-waltz-911.notion.site/Ariadne-122f3d9811d94bfd832c1e6dc88acc01) （変なテンションで書いたので語尾がおかしいです..）

## 立ち上げ方
1. ```docker-compose up```
2. [8888番ポート](http://localhost:8888/graphql)にアクセスする
3. Playgroundが立ち上がっているため、下記のクエリを実行できる

### 成功するクエリ
```
query {
  authenticateUser(request: {
    email: "user@example.com",
    password: "password"
  }) {
    isSuccess
    errorMessage
    data {
      id
      name
      email
    }
  }
}
```
### 失敗するクエリ
```
query {
  authenticateUser(request: {
    email: "user@example.com",
    password: "wrongpassword"
  }) {
    isSuccess
    errorMessage
    data {
      id
      name
      email
    }
  }
}
```

## Warning
- 実際のサーバーでは debug=False にして、middleware でCORSの設定をして起動する
