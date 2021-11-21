# sample-vue-trade-supporter-frontend
Vue.js でのサンプルプロジェクトとして、ゲーム等でよくあるアイテム作成/販売のトレードをサポートするアプリを開発します

## 開発環境
| 名前 | バージョン |
|-|:-:|
| VirtualBox | 6.1 |
| ubuntu | 20.04.3 server |
| Visual Studio Code | 1.61.0 |
| nodenv | 1.4.0+3.631d0b6 |
| node | 17.0.1 |
| @vue/cli | 4.5.15 |
| vue | 3.0.0 |
| vue-router | 4.0.0-0 |
|  |  |

## 実行手順
本プロジェクトを実行する場合、[環境構築](#環境構築) を行った後に下記を実行してください

### 構築/設定
```sh
# 1. ソース取得
git clone https://github.com/k-shiroma/sample-vue-trade-supporter-frontend.git

# 2. ライブラリ取得
cd sample-vue-trade-supporter-frontend
npm install
```

### 実行
1. 起動
    ```sh
    npm run serve
    ```
1. http://localhost:8080 をブラウザで開く

## 開発手順
本プロジェクトの作成手順です

### 環境構築
```sh
# 1. nodenv
## apt アップデート
### install の前にはやっておいたほうがいい
sudo apt update

## 開発ツールインストール (nodenv ビルド時に使用)
sudo apt install build-essential

## nodenv ダウンロード
git clone https://github.com/nodenv/nodenv.git ~/.nodenv

## nodenv ビルド
cd ~/.nodenv && src/configure && make -C src

## PATHを通す
echo 'export PATH="$HOME/.nodenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(nodenv init -)"' >> ~/.bashrc

## シェル再起動
exec $SHELL -l

## Node.js インストール用プラグイン インストール
git clone https://github.com/nodenv/node-build.git $(nodenv root)/plugins/node-build

## インストール確認
curl -fsSL https://github.com/nodenv/nodenv-installer/raw/master/bin/nodenv-doctor | bash

## こうなっていたらOK
## Checking for `nodenv' in PATH: /home/ubuntu/.nodenv/bin/nodenv
## Checking for nodenv shims in PATH: OK
## Checking `nodenv install' support: /home/ubuntu/.nodenv/plugins/node-build/bin/nodenv-install (node-build 4.9.57)
## Counting installed Node versions: none
##   There aren't any Node versions installed under `/home/ubuntu/.nodenv/versions'.
##   You can install Node versions like so: nodenv install 2.2.4
## Auditing installed plugins: OK

# 2. Node.js
## インストール可能なバージョンのリスト確認
nodenv install -l

## インストール(最新)
nodenv install 17.0.1

## システム全体で使用する Node.js 設定
nodenv global 17.0.1

## 確認
node -v
nodenv versions

# 3. Vue CLI
## インストール
npm install -g @vue/cli
nodenv rehash
```

### 設定
```sh
# 5. プロジェクト生成
## プロジェクト生成
cd ~/projects/
vue create sample-vue-trade-supporter-frontend
cd ~/projects/sample-vue-trade-supporter-frontend
### ? Please pick a preset:
### ❯ Manually select features
### 
### ? Check the features needed for your project: 
###  ◉ Choose Vue version
###  ◉ Babel
###  ◯ TypeScript
###  ◯ Progressive Web App (PWA) Support
### >◉ Router
###  ◯ Vuex
###  ◯ CSS Pre-processors
###  ◉ Linter / Formatter
###  ◯ Unit Testing
###  ◯ E2E Testing
###
### ? Choose a version of Vue.js that you want to start the project with
### > 3.x
###
### ? Use history mode for router? (Requires proper server setup for index fallback in production)
### y
### 
### ? Pick a linter / formatter config:
### ❯ ESLint with error prevention only 
###
### ? Pick additional lint features: (Press <space> to select, <a> to toggle all, <i> to invert selection)
### ❯◉ Lint on save
###
### ? Where do you prefer placing config for Babel, ESLint, etc.? (Use arrow keys)
### ❯ In dedicated config files
###
### ? Save this as a preset for future projects?
### n

# 6. プロジェクト設定
## デフォルトの設定では起動時に下記エラーとなるため回避策
### 10% building 2/5 modules 3 active ...end/node_modules/eslint-loader/index.js??ref--14-0!/home/ubuntu/projects/sample-vue-trade-supporter-frontend/src/main.jsError: error:0308010C:digital envelope routines::unsupported
### 参考: https://stackoverflow.com/questions/69692842/error-message-error0308010cdigital-envelope-routinesunsupported
export NODE_OPTIONS=--openssl-legacy-provider

## プロジェクトで使用する Node.js 設定
nodenv local 17.0.1

## Node.js バージョン確認
node -v
nodenv versions

## ライブラリ取得
npm install
```

## 開発メモ
### xxx
