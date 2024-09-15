# 自己ホスト型同期サーバー

AnkiWebを使用できない、または使用したくない上級ユーザーは、自己ホスト型の同期サーバーを使用することができます。

注意点：

- これはネットワーキングやコマンドラインに慣れているユーザーを対象とした上級機能です。これを使用する場合、設定やネットワーク、ファイアウォールの問題を自分で解決できることが期待されており、使用は完全に自己責任です。
- 新しいクライアントは同期プロトコルの変更に依存することがあるため、Ankiクライアントを更新してもサーバーを更新しないと同期が停止することがあります。
- サードパーティの同期サーバーも存在しますが、それらに対するテストは行われておらず、同期プロトコルが変更された際に追従するのに時間がかかる傾向があるため、推奨されません。
- Anki内のメッセージはカスタムサーバーが設定されていても「AnkiWeb」という用語を使用します（例：「サーバーがダウンしているときに「AnkiWebに接続できません」と表示される」）。

## インストール/実行

サーバーをインストールして実行する方法はいくつかあります。以下のいずれかを使用できます：
- デスクトップ版Ankiに同梱されている同期サーバー
- AnkiのGUI依存関係を含まない、別の最小限の同期サーバー。PythonとRustの実装が利用可能です。

### パッケージビルドから

これは、バージョン2.1.57以降のデスクトップ版Ankiに組み込まれている同期サーバーを使用します。

Windowsでは、cmd.exeセッションで以下を実行します：
```
set SYNC_USER1=user:pass
"\Program Files\anki\anki.exe" --syncserver
```

またはMacOSでは、Terminal.appで以下を実行します：

```
SYNC_USER1=user:pass /Applications/Anki.app/Contents/MacOS/anki --syncserver
```

またはLinuxでは：
```
SYNC_USER1=user:pass anki --syncserver
```

### Pipを使用する場合

デスクトップ版AnkiのGUI依存関係をダウンロードしないようにするために、PyPIからダウンロードしたPythonパッケージを使用してスタンドアロンのAnki同期サーバーを実行できます。
Python 3.9以上がインストールされていることを確認してください。

```
python3 -m venv ~/syncserver
~/syncserver/bin/pip install anki
SYNC_USER1=user:pass ~/syncserver/bin/python -m anki.syncserver
```

### Cargoを使用する場合

Anki 2.1.66以降では、以下のコマンドを使用してスタンドアロン同期サーバーのRust実装をビルドすることもできます。
Rustupがインストールされていることを確認してください。

```
cargo install --git https://github.com/ankitects/anki.git --tag 2.1.66 anki-sync-server
```

2.1.66を最新のAnkiバージョンに置き換えてください。

Protobuf（protoc）をインストールする必要があります。

ビルド後、以下のコマンドで実行できます：
```
SYNC_USER1=user:pass anki-sync-server
```

### ソースチェックアウトから

GitHubからAnkiリポジトリをクローンした場合、そこからインストールできます：

```
./ninja extract:protoc
cargo install --path rslib/sync
```

## 複数ユーザー

SYNC_USER1は最初のユーザーとパスワードを宣言し、必ず設定する必要があります。
複数のアカウントを設定したい場合は、オプションでSYNC_USER2、SYNC_USER3などを宣言することができます。

## 保存場所

サーバーはコレクションとメディアのコピーをフォルダーに保存する必要があります。
デフォルトでは ~/.syncserver に保存されますが、`SYNC_BASE` 環境変数を定義することで変更できます。これは通常のAnkiデータフォルダーと同じ場所にしてはいけません。サーバーとクライアントは別々のコピーを保存する必要があります。

## 公開アクセス

サーバーは暗号化されていないHTTP接続でリッスンするため、直接インターネットに公開するのは良い考えではありません。使用をローカルネットワークに制限するか、VPN（Tailscaleが簡単だと言われています）やHTTPSリバースプロキシなどの暗号化手段をサーバーの前に配置する必要があります。

`SYNC_HOST` と `SYNC_PORT` を定義することで、サーバーがバインドするホストとポートを変更できます。

## クライアント設定

コンピュータのネットワークIPアドレスを確認し、各Ankiクライアントをそのアドレスに向ける必要があります。例えば、`http://192.168.1.200:8080/` のようになります。URLは設定で構成できます。

AnkiMobileを使用していてローカルネットワーク上のサーバーに接続できない場合は、iOSの設定に移動し、下部にあるAnkiを見つけて、「Ankiにローカルネットワークへのアクセスを許可」をオフにしてから再度オンにしてください。

古いデスクトップクライアントでは、SYNC_ENDPOINTとSYNC_ENDPOINT_MEDIAを定義する必要がありました。古いクライアントを使用している場合、それぞれ `http://192.168.1.200:8080/sync/` および `http://192.168.1.200:8080/msync/` のように設定します。AnkiDroidクライアントのバージョン2.16以前では、2つのエンドポイントを別々に設定する必要があります。

## リバースプロキシ

リバースプロキシを使用してHTTPSアクセスを提供する場合（例：nginx）、サブパスにバインドする場合（例：`http://example.com/custom/` -> `http://localhost:8080/`）、Ankiを構成する際に末尾のスラッシュを含める必要があります。`http://example.com/custom` と設定すると、動作しません。

iOSではTLS 1.3がサポートされていないため、リバースプロキシでTLS 1.2を有効にする必要があります。そうしないと、「エラーコード -9836」が表示されます。

## 大きなリクエスト

標準のAnkiWebのアップロード制限がデフォルトで適用されます。制限を増やしたい場合は、MAX_SYNC_PAYLOAD_MEGSを100以上に設定することができます。ただし、リバースプロキシを使用している場合、そちらの制限も調整する必要があるかもしれません。

## 変更の貢献

このサーバーはAnkiにバンドルされているため、シンプルさが設計目標です。個人や家族での使用を対象としており、REST APIや外部データベースなどを追加するPRは現時点では受け入れられない可能性が高いです。疑問がある場合は、PRの作業を開始する前にご連絡ください。

既存のAPIソリューションをお探しの場合は、AnkiConnectアドオンがニーズを満たすかもしれません。