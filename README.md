# IntelliJ IDEA(以下「IDEA」という)での作り方  
  
## 1. JDKをインストール  
  
## 2. IDEAをインストールする  
[公式ページ](https://www.jetbrains.com/ja-jp/idea/download/#section=windows)から、無料の Community 版をダウンロードする。  
  
## 3. IDEAのプラグインを導入する
- [Minecraft Development](https://plugins.jetbrains.com/plugin/8327-minecraft-development)  
- [Japanese Language Pack](https://plugins.jetbrains.com/plugin/13964-japanese-language-pack------)  
- [Rainbow Brackets](https://plugins.jetbrains.com/plugin/10080-rainbow-brackets)　(おすすめ)  
  
## 4. プロジェクトの新規作成  
Minecraft -- Paper Plugin
- GroupId　　com.---  
- ArtifactId　　testplugin  
- Version　　1.0.0  
  
- Plugin Name　　TestPlugin
  
## 5. 起動構成、デバック環境の設定
### 5.1 pom.xmlの編集  
生成された `pom.xml` の `<plugins></plugins>`の間に[コレ](pom.xml)を追加する。  
これでビルドしたときに自動で `server/plugins/~.jar` に上書きされる。
  
### 5.2 サーバーの配置  
PaperMCを[公式ページ](https://papermc.io/downloads#Paper-1.18)からダウンロードして、プロジェクトに `server` フォルダを作り、そこに配置する。  
  
PlugManXというプラグインを導入するととても便利
  
### 5.3 server.propertiesの編集
`server`フォルダに`server.properties`を作成し、[コレ](server/server.properties)をコピペする。  
  
### 5.4 起動構成を作成 (重要)  
実行/実行構成の編集 を押す  
  
a：ビルドのみ  
    Mavenの `install` を実行  
  
b：ビルド後サーバーの起動  
    `JAR アプリケーション` の構成を追加して、JARのパスをサーバーの.jarのパス  
    `作業ディレクトリ` をserverフォルダ  
    JREはインストールしたもの  
    起動前は `Maven ゴールの実行`  
    コマンドラインは `install`  
  
c：ビルドせずにサーバーの起動  
    b の構成をコピペして、起動前 を削除する  
  
---
以上で終了です。  
  
### おすすめのSpigotプラグイン  
- PlugManX (プラグインをコマンドで無効にしたり再読込することができる)  
- BileTools (自動でプラグインを再読込する。ビルド後に音を鳴らしてくれる)