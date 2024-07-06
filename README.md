# Windows11 + WSL + Ubuntu + VSCode + Git + Github + Docker で開発環境構築
参考資料
* <https://www.youtube.com/watch?v=2l_nSudnKs4>
* <https://www.youtube.com/watch?v=6kCZJLZBVpQ>

## 1. Windows Terminal
* [Windows Terminal](https://apps.microsoft.com/detail/9n0dx20hk701?hl=ja-jp&gl=JP)アプリで PowerShell の起動確認
* ない場合は Microsoft Store で入手

## 2. Visual Studio Code
VSCode 本体のインストール：
* [Visual Studio Code](https://code.visualstudio.com/) 公式サイトからインストーラをダウンロード
  （Microsoft Store から入手でも可）
* VSCode のインストール
  * オプションはデフォルトのまま
* VSCode をスタートやタスクバーにピン留め（任意）
<br/>

拡張機能のインストール：
* Japanese Language Pack for Visual Studio Code（日本語化のため）
* WSL（WSL 環境に接続するため）

## 3. Git for Windows
実質的に [Git Credential Manager](https://docs.github.com/ja/get-started/getting-started-with-git/caching-your-github-credentials-in-git)（GCM，Git 資格情報マネージャー）を使うためだけに、Windows 側に Git を入れる
<br/>

WSL Ubuntu に直接 GCM をインストールすることもできるが、Microsoft 公式で推奨している Git for Windows を使う方式を採用

### 3.1. ダウンロード
* [Git](https://git-scm.com/download/win) 公式サイトから [64-bit Git for Windows Setup](https://github.com/git-for-windows/git/releases/download/v2.44.0.windows.1/Git-2.44.0-64-bit.exe) をダウンロード

### 3.2. インストールウィザード
* Select Components
  * Windows Explorer integration : OFF（任意）  
    右クリックのコンテキストメニューに追加される
    <br/>
    
  * Check dialy for Git for Windows updates : ON（推奨）  
    勝手にアップデートしてくれる設定
    <br/>
    
  * Add a Git Bash Profile to Windows Terminal : ON（推奨）  
    Windows Terminal に Git Bash を追加してくれる

* Choosing the default editor used by Git  
  Git のデフォルトエディタを選択
  <br/>
  
  * Use Visual Studio Code as Git's default editor  
    VSCode をデフォルトエディタとして選択

* Adjusting the name of the initial branch in new repository  
  git init で新しいリポジトリ作成時の初期ブランチ名について
  <br/>
  
  * 新しいリポジトリのデフォルトブランチ名を 'main' にする

* Adjusting your PATH environment  
  PATH 環境について
  <br/>
  
  * Git from the command line and also from 3rd-party software  
    推奨。PATH に最小限の Git ラッパーだけを追加  
    Git Bash、コマンドプロンプト、Windows PowerShell などから Git を使えるようにする

* Choosing the SSH executable
  <br/>
  
  * Use bundled OpenSSH  
    Git に付属の ssh.exe を使用

* Choosing HTTPS transport backend  
  Git の HTTPS 接続に使う SSL/TLS ライブラリ
  <br/>
  
  * Use the Open SSL library  
    サーバ証明書は、ca-bundle.crt ファイルを使って認証

* Configuring the line ending conversations  
  改行文字の設定
  <br/>
  
  * Checkout as-is, commit as-is  
    テキストファイルのチェックアウトやコミットの際に、改行文字の変換を行わない  
    "core.autocrlf false" の設定

* Configuring the terminal emulator to use with Git Bash  
  Git Bash で使う端末エミュレータの設定
  <br/>
  
  * Use MinTTY (the default terminal of MSYS2)  
    MinTTY（MSYS2 のデフォルト端末）を使う

* Choose the default behavior of 'git pull'  
  'git pull' のデフォルトの動作を選択する
  <br/>
  
  * Only ever fast-forward  
    Fast-forward のみ  
    これは 'git pull' の標準的な動作

* Choose a credential helper  
  資格情報ヘルパーの選択
  <br/>
  
  * [Git Credential Manager](https://docs.github.com/ja/get-started/getting-started-with-git/caching-your-github-credentials-in-git)  
    Git 資格情報マネージャー

* Configuring extra options  
  追加オプションの設定
  <br/>
  
  * Enable file system caching  
    ファイルシステムのキャッシュを有効にする

### 3.3. '.gitconfig' の設定
Git 環境の設定を行う
<br/>

参考：[Git - 最初の Git の構成](https://git-scm.com/book/ja/v2/%E4%BD%BF%E3%81%84%E5%A7%8B%E3%82%81%E3%82%8B-%E6%9C%80%E5%88%9D%E3%81%AEGit%E3%81%AE%E6%A7%8B%E6%88%90)
<br/>

* 'C:\Users{username}.gitconfig' ファイルを作成
  ※ Git のインストールで、エディタの指定のために自動で '.gitconfig' ファイルは作成されている
<br/>

* 設定を記入
* Git ユーザ名：'{username}' を自分の Git ユーザ名に変更
* コミットメールアドレス：'{email}' を自分のメールアドレスに変更
```
[core]
	editor = \"C:\\Users\\{username}\\AppData\\Local\\Programs\\Microsoft VS Code\\bin\\code\" --wait
[user]
    name = {username}
    email = {email}
[pull]
    ff = only
    rebase = false
[core]
    eol = lf
    ignorecase = false
    quotepath = false
[init]
    defaultBranch = main
[fetch]
    prune = true
[rebase]
    autosquash = true
```

## 4. WSL
WSL のインストールを行う
<br/>

* PowerShell を管理者モードで開く
* 'wsl --install' コマンドを入力
* パソコンを再起動
<br/>

参考：[WSL のインストール | Microsoft Learn](https://learn.microsoft.com/ja-jp/windows/wsl/install)

## 5. Ubuntu

### 5.1. 初期設定
* Microsoft Store から Ubuntu を入れる  
  通常は 'wsl --install' コマンドで一緒に Ubuntu も入る
  <br/>
  
* Windows Terminal から Ubuntu を初回起動  
  通常は 'wsl --install' コマンドで同時に進行する
  <br/>

* ユーザ名を入力
* パスワードを入力

参考：[WSL 開発環境を設定する | Microsoft Learn](https://learn.microsoft.com/ja-jp/windows/wsl/setup/environment)

### 5.2. パッケージ更新
これ以降は、VSCode で WSL Ubuntu を開いてもよい
<br/>

* パッケージを更新およびアップグレードして、ディストリビューションを最新の状態にする
```
# Ubuntu, Debian の場合
sudo apt update && sudo apt upgrade

# Ubuntu バージョン確認のコマンド
lsb_release -a
```

### 5.4. Git インストール
```
# できるだけ新しいバージョンの Git にするため、 ppa を設定
sudo add-apt-repository ppa:git-core/ppa

# Git を更新
sudo apt update; sudo apt install git
```
<br/>

参考：[Git - Download for Linux and Unix](https://git-scm.com/download/linux)

### 5.5. Git Credential Manager
Git for Windows の Git Credential Manager で、資格情報を登録できるようにされている
<br/>

WSL と Windows ホストの間で資格情報と設定を共有するために、'.gitconfig' に設定を追加する
<br/>

'.gitconfig' は、Windows と WSL 内で引継ぎは行われないので、WSL Ubuntu のホームに '.gitconfig' ファイルを作成し、設定を書く



## 1. Dockerのインストール
## 2. .devcontainer上に'devcontainer.json', 'Dockerfile', 'requirements.txt'を用意する
## 3. 
```
cd /home/{name}/.cevcontainer
docker build -t {dockerのイメージ名}
docker run --name {dockerのイメージ名} -it -d {サーバ名}
```
### 4.
リモートエクスプローラー⇒開発コンテナ⇒ウィンドウをアタッチで完成
