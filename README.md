# Go Gin Get Started

Go 言語の基本的なセットアップと、簡単な API サーバー構築の手順を初歩から説明します。

---

## 1. **Go 言語のセットアップ**

### a. **インストール**

- [公式サイト](https://go.dev/dl/)から最新バージョンをダウンロードしてインストールします。
- インストール後、コマンドラインで以下を実行して確認：

  ```bash
  go version
  ```

  バージョン情報が表示されれば成功です。

### b. **プロジェクトの準備**

1. プロジェクト用のディレクトリを作成します：

   ```bash
   mkdir my-first-api
   cd my-first-api
   ```

2. Go モジュールを初期化：

   ```bash
   go mod init my-first-api
   ```

   これで`go.mod`ファイルが生成され、依存管理が可能になります。

---

### 2. **Go の基本構文**

Go を理解するために基本的なコードを見てみましょう。

#### a. **「Hello, World!」**

以下のコードを`main.go`という名前で保存します：

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

実行方法：

```bash
go run main.go
```

#### b. **基本構造**

- **パッケージ宣言**: `package main`
  - Go プログラムのエントリーポイントは`main`パッケージ。
- **インポート**: 標準ライブラリや外部ライブラリを使うための宣言。
- **関数**: `func`キーワードを使って関数を定義。

---

### 3. **簡単な API サーバーを構築**

最初は軽量なフレームワーク「Gin」を使って API サーバーを作ります。

#### a. **Gin のインストール**

以下を実行して依存をインストール：

```bash
go get github.com/gin-gonic/gin@latest
```

#### b. **サーバーコードを書く**

`main.go`に以下のコードを書きます：

```go
package main

import "github.com/gin-gonic/gin"

func main() {
	r := gin.Default()
	r.GET("/ping", func(c *gin.Context) {
		c.JSON(200, gin.H{
			"message": "pong",
		})
	})
	r.Run() // listen and serve on 0.0.0.0:8080
}

```

#### c. **サーバーを実行**

以下のコマンドでサーバーを起動：

```bash
go run main.go
```

ブラウザで`http://localhost:8080/ping`にアクセスすると、以下のレスポンスが返ってきます：

```json
{
  "message": "pong"
}
```

---

### 4. **コードの解説**

- **ルーターの作成**:

  ```go
  r := gin.Default()
  ```

  Gin のルーターを作成し、ミドルウェア（ロギングやリカバリ）が自動で設定されます。

- **エンドポイントの登録**:

  ```go
  r.GET("/ping", func(c *gin.Context) { ... })
  ```

  HTTP メソッドとパス（`/ping`）を指定して処理を定義。

- **レスポンスの送信**:

  ```go
  c.JSON(200, gin.H{"message": "pong"})
  ```

  ステータスコード 200 と JSON 形式のレスポンスを返します。

---

### 5. **次に進むには**

- **ルーティングの学習**: パラメータ付きのルートや、POST リクエストの処理。
- **データベースの接続**: MySQL や PostgreSQL との連携。
- **設定ファイルの管理**: 環境変数や`.env`ファイルを使った設定。

他にも詳しく知りたいことがあれば教えてください！一緒に進めていきましょう。
