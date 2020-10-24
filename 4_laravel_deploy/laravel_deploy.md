# 手順
今回は、既存で走っているサービスをk8sへ移行することを想定し、k8sクラスターとは別のvpcで走っているRDSとk8sClusterをVPCピアリング接続で接続してClusterからRDSへアクセスできるようにします。

# アーキテクチャー図解

まずはk8s以前のアーキテクチャー図解

<img src="../asset/img/laravel_before.png">

上図の様に、同一VPC内でpublic subnetとprivate subnetで分割し、それぞれにlaravelの動いているEC2インスタンス、RDSを配置しています。

同一VPC内なのでlaravelからRDSに対してルーティングが届きます。

<img src="../asset/img/laravel_after.png">

ところが、上図のようにEKSでクラスターを作成すると、既存のRDSとVPCが異なってしまうため、そのままではRDSへ通信が届きません。

そこでVPC Peeringで下図のようにVPC間のネットワークを繋ぎます。
<img src="../asset/img/laravel_next.png">


