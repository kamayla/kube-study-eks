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
