# Windows11 + WSL + Ubuntu + VSCode + Git + Github + Docker で開発環境構築
参考資料
* <https://www.youtube.com/watch?v=2l_nSudnKs4>
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
