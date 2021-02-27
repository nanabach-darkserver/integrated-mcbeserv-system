# README #

マインクラフト統合版サーバーをできるだけ簡単にインストールするスクリプト。  
マインクラフト統合版サーバー本体だけでなく、  

* マインクラフトサーバーをsystemctlで起動・停止する機能  
* Linux起動時に自動起動  
* 自動定期バックアップ機能  
* 自動アップデート機能  

がインストールできます。  

統合版サーバーのインストール前に以下の規約やプライバシーポリシーに同意する必要があります。  
必ずチェックしてください。  

https://account.mojang.com/terms  
https://privacy.microsoft.com/ja-jp/privacystatement  

なお、このスクリプトはMinecraft公式のものではありません。    

## 想定環境 ###

### 統合版サーバーをインストールするマシン(以下A)

* Ubuntu 18以降
* WSL環境不可(v2含む)。

### このスクリプトを動かすマシン(以下B)

* UbuntuかDebian
* Aにssh接続可能であること(公開鍵認証かつ.ssh/configに設定済み、もしくはパスワード認証)

なお、パスワード認証かつ.ssh/configを設定している場合は、.ssh/configのHostNameを使わないでください。   

## 簡単な使い方 ###

とにかく簡単にインストールする場合、Bで以下を実行してください。(git clone不要)    
wget http://www8.dodomore.tokyo/auto_install.sh && bash auto_install.sh    

なお、インストールスクリプト内にはsudo必要な箇所とsudoでやってはいけない箇所があります(.ssh/configの都合)。  
そのため、上のコマンドはsudoで実行せず、一般ユーザーで実行してください。
　 

## 実行中の入力項目について解説

### 最初のsudoパスワード要求（設定によっては表示されない）
> [sudo] password for ・・・   

が表示されたら、作業マシン(B)のsudoパスワード入力画面です。   
AのsudoパスワードなのかBなのか間違えないように注意してください。  

### ホスト名入力画面

> インストールするサーバーのIPもしくはドメインを入力  
> （ssh/configを設定済みの場合はHostNameを入力）  

IPかドメイン名、もしくは.ssh/configで設定したHostNameを指定してEnterしてください。  

もし統合版サーバーをインストールする先のサーバー(A)のSSHポートを22以外にしていて、パスワード認証を使用する場合は、
ここでexample.com:1022のように:の後にポート番号を入れてください。  
公開鍵認証を使用する場合で、.ssh/configで設定している場合はここでポートの指定は不要です。    

### 統合版サーバーをインストールするサーバー(A)のsudoパスワード有無
> インストール先サーバーでsudoにパスワード必要ですか  
> はい: y  
> いいえ: nか何か  

sudo時にパスワード要求される場合は、y、それ以外はnを入力してEnterしてください。  

### ログイン方法の選択
> SSHアクセス方法の選択  
> 公開鍵認証でSSHログイン（.ssh/configを設定済み）: y  
> パスワード認証でSSHログイン: n  
> キャンセル: cか何か  

BからAへのSSH接続方法を選択してください。cの場合はキャンセルされて終了します。

### ユーザー名入力(上でパスワード認証を選択した場合のみ)
> ユーザー名を入力してください  

ユーザー名を入力してください。  

### その他 
パスワード認証を選択した場合は  
> SSH password:  

が表示されます。SSH接続のパスワードを入力してください。    

sudoパスワードありの場合は  
> SUDO password[defaults to SSH password]:   

が表示されます。Aのsudoパスワードを入力してください。  
 
## 謝辞

Almost all functions of integrated-mcbeserv-system are provided by MCscripts.
https://github.com/TapeWerm/MCscripts
Thanks to TapeWerm for distributing good codes!

## その他
もしgithubで報告できない内容や、AGPL以外のライセンスでの使用などを相談したい場合は  
Twitter: @nanabach5  
にご連絡ください。  

公開リポジトリ作った経験は全然ですので、良い対応や早い対応は期待しないでください。  
