# input

## KVSメリット

### 外部通信の負担を減らすことができる
- DBサーバーや外部APIにアクセスするとき、DBサーバーや外部APIの負荷が上がってしまう。
特にDBサーバーの場合は、毎回重いクエリを投げてしまうとCPU負荷が上昇し障害に繋がる可能性がある。その時、KVSを使ってクエリの結果を保存しておけば、重いクエリを毎回実行する必要がないため、DBに対する負荷を軽減することができる。

### 高速にデータを読み書きすることができる
- KVSの中でもRedisなどは「インメモリ型」のKVSでメインメモリ上で保存したデータを管理している。そのため、RDBのようにDBサーバーにアクセスするよりも高速にデータ操作を行うことが可能。データの取得速度が上がるということは、Webサイトの場合、「ページの表示速度」も向上するということ。ページの表示速度は広告収益に直結する要素の一つでもあるため、ビジネスの収益的にもKVSを使うメリットは大きい。

### シンプルな仕組み
- KVSは「keyとvalueでデータを管理する」というシンプルな構造。
SQLのように複雑なクエリを書く必要もない。

## KVSデメリット

### コンテンツが即座に更新されない可能性がある
- KVSを使ってRDBから取得したデータを一定時間保存（キャッシュ）している場合、DBを更新してもコンテンツには即座に反映されない可能性がある。
  
### 実装が複雑になる可能性がある
- KVSにデータを保存するということは、その処理を実装する必要がある。
そのため、場合によってはコードの行数が増えて可読性が低下したり、テストが複雑になる可能性もある。

### 大容量のデータは扱えない
- KVSの中でも例えばRedisなどはメモリ上で動作するため、気を付けないと大量にメモリを消費してしまう可能性がある。
そのため、大容量のデータを一度に取り扱うような処理はKVSでは行えない。

## Kubernetes特徴・何ができるか

### コンテナオーケストレーション
- コンテナのデプロイメントと管理。アプリケーションのコンテナ化（Dockerなど）をサポートしている。複数のコンテナを単一または複数のホスト上で効果的に実行できる。

### オートスケーリング
- 負荷に合わせてアプリケーションを自動的にスケーリングできる。リクエスト数、CPU使用率などのメトリクスに基づいて、新しいインスタンスを追加、削除できる。

### セルフヒーリング
- クラスタ内のコンポーネントに障害が発生した場合、Kubernetesは自動的に障害の再調整を行い、アプリケーションの可用性を維持する。



