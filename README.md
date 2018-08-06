# dockerでビルド環境を構築するためのセット

## 前提条件

Dockerをよしなにインストール

## 使い方

```
$ git clone 
$ cd buildservers
$ docker-compose up -d --build
```

## どうなる？

Dockerコンテナが2つ立ち上がります。

1. Jenkins ( http://localhost:8080 )
2. Docker-Registroy ( http://localhost:5000 )

### Jenkins

おじさんです。
2種類のジョブを作成することになります。

1. プロジェクトをclone後、Docker imageをビルドし、Registoryにpushするジョブ
  * ジョブタイプは Multiplebranch Pipeline
  * プロジェクトには Jenkinsfile-for-project を参考に Jenkisfile を作成してください
2. Registoryからimageをpullして、runするジョブ
  * ジョブタイプは Pipeline
  * パラメータ付きビルドでブランチ名 `BRANCH_NAME` を指定できるようにする

### Docker-Registory

Docker Imageをホストするサーバです。

