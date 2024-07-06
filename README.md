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
