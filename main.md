# CircleCI 2.0

---

## CircleCIとは
- CIのマネージドサービス
- 競合だとTravisCIとかある
- ymlに適当書いたらCIできる

自前サーバだとJenkinsが有名

### CIとは
- 継続的インテグレーション
- ビルド・テストなどを継続的に行う
- 人間はズボラなので自動化しよう

---

## CircleCI2.0
Docker移行しただけなのだが

- 当然1から書き直し
- 別サービスだと思うべき

移行で得られるもの

- 速度
- ローカル実行
- 高いカスタマイズ性

---

## Docker image
- Dockerなのでimageが必要
- DockerHubのものが使える
- publicなもののみ(重要)
- circleci公式がお勧め

### 公式のメリット
- SSHデバッグができる
- 127.0.0.1で繋げる

---

## Cache
2.0の速度向上の半分がCacheによるもの

1.0で自動で遅かったCacheは

2.0でシンプルなImmutable Cacheになった

---

### 具体的に
- nameを指定する
  - `v1-bundler-{{ arch }}-{{ checksum Gemfile.lock }}`
- restore時にnameがヒットしたら展開
- nameがヒットしなければ新規作成
- cache clearしたいときはv2にする

immutableなので、消さない、変更しない

---

## 御託はいいから
実物見せればいいんじゃね、と思ったんだ

---

## CircleCI2.0まとめ
- dockerで速い
- immutable cacheで速い
