# 内容

- 業務において、**AWSクライアントVPN通信の廃止**と**サイトSSL化対応**が必要になったため、その作業記録を残していく。

# おまかな環境構成
<img src="https://github.com/hiddy0329/TIL/assets/91509668/7a2b0673-68ea-4de0-aa6b-e24423d2a67a" width="50%" height="50%">

# 詳細手順
1. Route 53でドメイン取得を行う
2. ドメインのEメール検証を行う
3. Route53でドメインのホストゾーンにサブドメインのAレコードを追加
4. ACMでSSL/TLS証明書を発行（指定したドメインを保護するよう申請）
5. 証明書のDNSレコードをRoute53にて登録し、自身がドメイン取得者であることを検証する
6. CloudFrontでディストリビューションを作成する
    - ViewerからCloudfrontへの通信は「HTTP redirect to HTTPS」に設定
    - CloudfrontからOrigin(今回はEC2)への通信は「HTTP」のみに設定
    - AWS WAFとの連携は特に設定なし 
8. Route 53でDNSのAレコードを更新し、ドメインの向き先をCloudFrontに向けるように設定を更新する。
9. EC2のセキュリティグループを更新し、CloudFrontからのHTTP通信のみを許可するよう設定する。
10. Laravelの設定を更新（CSSなどの参照パスを全てhttpsに変更）
11. 接続テストを実施する

# 参考情報
- [CloudFront Distribution for EC2, Step-by-Step Guide](https://medium.com/@diyar.parwana/step-by-step-guide-to-create-a-cloudfront-distribution-for-ec2-cbf5b7862c41)
- [LaravelでHTTPSに対応するための設定とコーディング](https://egatech.net/laravel-https/#toc7)
    - 今回はこちらで紹介されている方法のうち、環境の違いに影響を受けない「**URLジェネレーターの使用**」を採用
