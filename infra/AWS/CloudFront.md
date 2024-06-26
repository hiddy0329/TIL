# CloudFrontとは

- フルマネージド型のCDN（Contents Delivery Network）サービスである
- 世界中のエッジロケーションにコンテンツをコピーし、アクセス元のユーザーに効率よくコンテンツ配信をすることを実現する
- AWS Certificate Managerとの連携によるSSL認証機能の提供、AWS WAFとの連携によるセキュリティの強化など、他サービスとの連携機能が充実している

# CloudFrontの基本機能

<img src="https://github.com/hiddy0329/TIL/assets/91509668/034c97d5-bca0-4648-a7a0-66d433b3937c" width="50%" height="50%">

- コンテンツのコピーを「**キャッシュ**」として世界中のエッジロケーション（＝効率よくコンテンツ配信を実施するために整備された施設群）に共有し、ユーザーからの効率良い
アクセスを実現させる。
- サーバー側には毎回毎回コンテンツをレスポンスする手間がなくなり、負荷の軽減につながる。
- ユーザー側にはキャッシュを利用した高速なコンテンツ配信を体験できるようになる。

# CloudFront設定手順

<img width="50%" height="50%" src="https://github.com/hiddy0329/TIL/assets/91509668/d6baebad-908d-4930-b6a7-6cec8b257afd">

[(公式)AmazonCloudFrontとは何ですか?](https://docs.aws.amazon.com/ja_jp/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)

- CloudFrontを利用してコンテンツの配信を実現するためには、「**ディストリビューション**」というコンテンツ配信の追跡・管理用サービスを作成する必要がある。以下はディストリビューションで設定する基本的な内容となる。

1. オリジンの作成（コンテンツの配信元となるサービス）を行う。対象サービスとしてはS3, EC2, ELBなどがある。
2. オブジェクト（主に静的コンテンツ）をオリジンにアップロードする。
3. CloudFrontのディストリビューションを作成する。
4. CloudFrontにドメインが割り当てられる。
5. ディストリビューションにおいて、オリジンの設定をする。（どのオリジンを対象とするのか）
6. ディストリビューションにおいて、ビヘイビアー（＝動作）の設定をする。（CloudFrontがリクエストを受けた時の挙動をどうするのか）
    - HTTP圧縮をするかどうか（「する」の場合、エッジロケーションにおいてコンテンツが圧縮された状態でビューワーにレスポンスされるようになる）
    - ビューワープロトコルポリシーにおいてリクエストの動作設定をする（HTTTPかHTTPSか、許可するHTTPメソッドはなにか）
    - キャッシュに関する各種設定を入れる（キャッシュキーの設定、TTL設定など）

# 参考情報
- [(公式)AmazonCloudFrontとは何ですか?](https://docs.aws.amazon.com/ja_jp/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)
