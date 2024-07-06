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
  <br/>
  * Windows Explorer integration : OFF（任意）  
    右クリックのコンテキストメニューに追加される
    <br/>
  * Check dialy for Git for Windows updates : ON（推奨）
    勝手にアップデートしてくれる設定
    <br/>
  * Add a Git Bash Profile to Windows Terminal : ON（推奨）
    Windows Terminal に Git Bash を追加してくれる
    <br/>

* Choosing the default editor used by Git
  Git のデフォルトエディタを選択
  <br/>
  * Use Visual Studio Code as Git's default editor
    VSCode をデフォルトエディタとして選択
    <br/>

* Adjusting the name of the initial branch in new repository
  git init で新しいリポジトリ作成時の初期ブランチ名について
  <br/>
  * 新しいリポジトリのデフォルトブランチ名を 'main' にする
    <br/>

* Adjusting your PATH environment
  PATH 環境について
  <br/>
  





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
