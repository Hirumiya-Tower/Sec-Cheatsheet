# 解説

ハッシュクラックツール。辞書攻撃やブルートフォースを用いて、ハッシュ化されたパスワードなどを復元する。

# 基本構文

```john [オプション] [ハッシュファイル]```

# 主要なモード・オプション

### 辞書を指定

```e.g. --wordlist=/usr/share/wordlists/rockyou.txt``` 

### ハッシュタイプを指定

```e.g. --format=raw-md5 / raw-sha256 / bcrypt / NT``` 

### 結果の確認

```--show``` クラック済みのパスワードを表示する
```--list=formats``` 対応しているハッシュ形式を一覧表示

### ユーザーを指定

```
john --users=admin mypasswd.txt
```
# 解読前の準備

### Linuxシステムパスワード（unshadow）

```
unshadow /etc/passwd /etc/shadow > mypasswd.txt
john mypasswd.txt
```

### ssh, zip, rarの変換

```
ssh2john id_rsa > rsa_hash.txt
```
```
zip2john data.zip > zip_hash.txt
```
```
rar2john data.rar > rar?hash.txt
```
```
pdf2john document.pdf > pdf_hash.txt
```
変換後、生成されたテキストファイルをjohnで解読する。

