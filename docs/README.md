## isucon

### 環境構築

AWS 環境を使うことが前提

##### TODO

- EC2 に置かれているソースを git で ssh 経由で管理する
- 個人の.gitconfig で仕込んでいる 設定を流し込む
- 個人の DB クライアントから MySQL に繋ぐ
- Ansible を使ってサーバに入れたいツールを流し込む
  - pt-query-digest
  - alp
- Go のアプリ解析用に pprof 入れるとか

### 計測

本番のアプリが Nginx と MySQL を使っていることが前提

#### スロークエリ

pt-query-digest を使う

##### TODO

- MySQL の設定でスロークエリを吐き出すようにする
- ログローテ
- ADMIN PREPARE 対策

#### Nginx のアクセスログ

alp を使う

##### TODO

- アクセスログのグルーピング

### 便利コマンド類

よく使うコマンドは、Makefile で完結するように

- top/htop
- systemctl
- journalctl
- alp
