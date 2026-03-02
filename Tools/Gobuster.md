# 解説

URI（ディレクトリ・ファイル）、DNSサブドメイン、仮想ホストなどの総当りツール。

# 基本構文
```
gobuster [モード] [オプション]
```

# 主要なモード

## dirモード

```
gobuster dir -u <URL> -w <wordlist> [オプション]
```
- ```-x <extensions  ``` 拡張子（php, html, txt, js）を指定
- ```-k  ``` SSL証明書のエラー（自己署名など）を無視
- ```-s <status_codes>  ``` 表示するステータスコードを指定
- ```-b <status_codes>  ``` 除外するステータスコードを指定

## dnsモード
```
gobuster dns -d <domain> -w <wordlist>
```
- ```-i  ``` 発見したサブドメインのIPアドレスも表示する
- ```-c  ``` CNAMEレコードも表示する

## vhostモード
```
gobuster vhost -u <URL> -w <wordlist> --domain<domain> (--append-domain)
```
HTTPのHOSTヘッダーを書き換え、同一IPでの別サイトを探索する

# 共通オプション

```-t <threads>``` 同時実行数を管理。デフォルトは10。
```-o <file>``` スキャン結果を指定ファイルに保存
```-z``` 進捗状況を表示しない
```--exclude-length``` サイズ除外

# コマンド例

```
gobuster dir -u http://10.10.10.10/ -w /usr/share/wordlists/dirb/common.txt -x php,html
```
```
gobuster dns -d example.com -w /usr/share/wordlists/dns/subdomains-top1mil-5000.txt -i
```