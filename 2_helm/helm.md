# helmについて
kubernetesは様々なリソースの複合で構成されています。

これら複数のリソースを一つの圧縮ファイルにバンドルすることが出来るのがhelmチャートで。

# helmをインストール

```
brew install helm
```

versionの確認

```
helm version
```

私の場合の出力

```
version.BuildInfo{Version:"v3.3.1", GitCommit:"249e5215cde0c3fa72e27eb7a30e8d55c9696144", GitTreeState:"dirty", GoVersion:"go1.15"}
```

# 独自Chartを作成する

```
helm create mychart
```

このコマンドを実行すると、このドキュメントがあるディレクトリにmychartというディレクトリがありますが、これと同一のファイルが生成されます。

今回は独自チャートの作り方については話が脱線してしまうので割愛しますが、helm独自チャートからpodやserviceが起動する様を確認しましょう。

```
helm install mychart ./mychart
```

これは
```
helm install [リリース名] [チャートのディレクトリパス]
```

uninstallは
```
helm uninstall mychart
```

 これは
 ```
 helm uninstall [リリース名]
 ```

今回のeks編での主なhelmの用途は、リポジトリから必要なhelmチャートをインストールすることです。（例えばPrometheusやGrafana）