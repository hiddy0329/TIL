# 内容

- 業務において、**AWSクライアントVPN通信の廃止**と**サイトSSL化対応**が必要になったため、その作業記録を残していく。

# おまかな環境構成
<img src="https://i.gyazo.com/7470be4f342b251e68d1b05e88981a86.png" width="50%" height="50%">

# 詳細手順
1. Route 53でドメイン取得を行う
2. ドメインのEメール検証を行う
3. Route53でドメインのホストゾーンにサブドメインのAレコードを追加
4. ACMでSSL/TLS証明書を発行（指定したドメインを保護するよう申請）
5. 証明書のDNSレコードをRoute53にて登録し、自身がドメイン取得者であることを検証する。
6. CloudFrontディストリビューションの設定
  - ポリシー設定などの各種設定をチュートリアルに沿って実施する（https://medium.com/@diyar.parwana/step-by-step-guide-to-create-a-cloudfront-distribution-for-ec2-cbf5b7862c41)
  - Route 53でDNS設定を更新し、ドメインの向き先をCloudFrontに向けるように設定を更新する。
  - EC2のセキュリティグループを更新し、CloudFrontからのHTTP通信のみを許可するよう設定する。
  - Laravelの設定を更新（主にCSSの参照パスをhttpsに変更）
  - 接続テストを実施する


