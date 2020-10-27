# EKS環境構築
まずは大前提としてAWSのアカウントを登録してください。

## AWS CLIのインストール及び設定
以下のコマンドでインストールしてください。

```shell
$ brew install awscli
```

そして、以下のコマンドでAWSのアカウントを設定します。
```shell
$ aws configure
```

最後に現在設定されているawsアカウントを確認します。

```shell
$ aws sts get-caller-identity
```
この様な出力で、現在指定しているアカウントが表示されます。

```shell
$ aws sts get-caller-identity
00000000000    arn:aws:iam::00000000000:user/hogehogehoge    FUGAFUGAFUGAFUGAFUGA
$
```

# aws-iam-authenticatorのインストール
以下コマンドでインストール。
```shell
$ brew install aws-iam-authenticator
```

# eksctlをインストール
以下コマンドでインストール。
```shell
$ brew tap weaveworks/tap
$ brew install weaveworks/tap/eksctl
$ eksctl version
```

eksctlが既にインストールされている場合は以下でアップグレードできます。
```shell
$ brew upgrade eksctl && brew link --overwrite eksctl
```

# eksクラスターを作成する
EC2インスタンスにSSHするための公開鍵を作成しましょう。
```
$ ssh-keygen
```

```
$ eksctl create cluster \
--name eksdemo \
--version 1.16 \
--region ap-northeast-1 \
--nodegroup-name workers \
--node-type t3.medium \
--nodes 1 \
--nodes-min 1 \
--nodes-max 4 \
--ssh-access \
--ssh-public-key ~/.ssh/eks-demo.pem.pub \
--managed

```
