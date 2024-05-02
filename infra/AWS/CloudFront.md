# CloudFrontとは

- CloudFrontはフルマネージドのCDNサービスである。世界各地にあるエッジロケーションという箇所にコンテンツデータをコピーしておき、ユーザーからのアクセスに対して高速な
コンテンツ配信を実現している。

# CloudFrontの基本機能
<img src="https://github.com/hiddy0329/TIL/assets/91509668/034c97d5-bca0-4648-a7a0-66d433b3937c" width="50%" height="50%">

# CloudFront設定手順

1. オリジンの作成（コンテンツの配信元となるサービス）を行う。対象サービスとしてはS3, EC2, ELBなどがある。
2. CloudFrontのディストリビューションを作成する。
3. ディストリビューションにおいて、オリジンの設定をする。（どのオリジンを対象とするのか）
4. ディストリビューションにおいて、ビヘイビアーの設定をする。（CloudFrontがリクエストを受けた時の挙動をどうするのか）
    4_1. HTTP圧縮をするかどうか（「する」の場合、エッジロケーションにおいてコンテンツが圧縮された状態でビューワーにレスポンスされるようになる）
    4_2. ビューワーのリクエストの動作設定をする（HTTTPかHTTPSか、許可するHTTPメソッドはなにか）
1. 番号付きリスト1
    1. 番号付きリスト1_1