# 解説

通信パケットを傍受・解析するGUIソフトウェア。
**始めにView > Time Display Format > UTC Date and Time and Dayすること**

# 基本フィルタ構文

```[プロトコル] [比較演算子] [値]```

# 論理演算子

```and//&& or/|| not/! eq/== ne/!= contains など```

# 有用なディスプレイフィルタ設定

### アドレス・ポート設定

```ip.addr == <IP>``` 送信元・送信先いずれかのIPを指定
```ip.src == <IP>```   送信元IPを指定
```ip.dst == <IP>```   送信先IPを指定
```tcp.port == <PORT>``` 特定のTCPポート番号を指定
```udp.port == <PORT>``` 特定のUDPポート番号を指定

### プロトコル別

```http``` HTTPプロトコルのパケットのみ表示
```dns``` DNSクエリ・レスポンスを表示
```icmp``` Pingなどのicmpパケットを表示
```ssh / ftp / telnet``` 特定の通信サービスを表示

### 高度なフィルタ

```http.request.method == "GET"``` HTTPのGETリクエストのみ表示
```http.response.code == 404``` HTTP404エラーレスポンスのみ表示
```tcp.flags.syn == 1``` SYNフラグが建っているパケット（接続開始）を表示
```tcp.flags.reset == 1``` RST（強制切断）パケットを表示
```frame contains "password"``` パケット全体から特定の文字列を検索

# 右クリックメニュー

 - **Follow > TCP Stream:**
	 一連のTCPの流れをテキスト形式で再構成して表示する。
	 平文通信の中身を見るのに適する。
- **Conversation Filter**:
	選択したパケットの送信元・送信先ペアの通信に絞り込む。
- **File > Export Objects > HTTP**:
	通信経由でダウンロード・転送されたファイルを抽出・保存する。

# キャプチャフィルタ

```host <IP>``` 特定のIPのみキャプチャする。
```port <PORT>``` 特定のポートのみキャプチャする。
```not icmp``` ICMPを除外してキャプチャする。

# ショートカットキー

```Ctrl + F``` Find packet。フィルタ構文を使う。
```Ctrl + G``` Go to packet。指定した番号にジャンプする。
```Ctrl + M``` Mark Packet。指定したパケットをマークする。
