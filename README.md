# pana
Anonymization of Linux communications.  
  
Tor Transparent Proxy & DNS over HTTPS over Tor & Kill Switch  
and Disable IPv6, Block global access.  
  
operating environment: Debian/Ubuntu, Python3
  
----
### インストールも利用も簡単
ワンライナーでインストール完了、再起動後は常時有効で何も意識する必要はありません。  
万が一プログラムが落ちてもキルスイッチが通信をブロックします。

### OS丸ごと全ての通信をTor経由にします
ネットワーク構築前にKillSwitchが開始します。  
なおTor経由なのでUDPでの通信はローカルネットワーク内に制限されます。  

### 接続先毎に異なるIPを使用します  
但しTorサーキットの都合で同じIPになる事もあります。  

### DNS over HTTPS over Torを使用します
全てのDNSリクエストは、DNS over HTTPS over Torになります。  
更にDNS over HTTPSを独自実装していない多くのクライアントは、Cloudflareの.onionサーバーを利用する事になります。  
また同時にDNS over HTTPSを独自実装していない全てのクライアントは.onionの正引きが可能になります。  

### グローバルからの外部アクセスを遮断します  
オプションでポートを開く事も可能ですが、非推奨です。

### StrictNodesは無効です
StrictNodesは必須とされていますが、作成者個人は、   
・無効にする事による利便性向上  
・同じ経路を強制しない事による匿名性の向上  
という認識です。  
***Torは我々よりも断然賢く***無闇に設定を無視する事はありません。  

### その他
IPv6が無効化されます。  

### ※注意：.onionへのアクセスについて
ブラウザで.onionを閲覧する為にはブラウザ側の設定変更が必要な場合があります。  
但し匿名性の観点からTorBrowser以外でWEBサイトにアクセスを行う事は大きなリスクを伴います。  
またTorBrowserを利用する際はOS側のTor経由になるのを防ぐ為に"nopana"を利用して下さい。  

----
## Install/Update
```
curl -sS https://raw.githubusercontent.com/zeppachi/pana/main/pana -o pana && sudo python3 pana install
```
\* It will be automatically enabled when the installation is completed.  
\* After installation is complete, the program is not required.  

## Rebuild the Tor Circuit
```
sudo pana renew
```
or
```
sudo systemctl restart pana
```

## How to Enable/Disable
```
sudo pana [enable|disable]
```
\* It also disables KillSwitch!

## Disable only some app
```
nopana <appname>
```
\* sudo pwd is required (stdin support)
