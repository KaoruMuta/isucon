# isucon

## 流れ

- 環境構築
- 計測方法

## 環境構築

AWS 環境を使うことが前提。

### 本戦 (WIP)

配布された CloudFormation から EC2 立てるだけ？
そこに、各種ツールを流し込めるようにすれば OK?

### 過去問 (WIP)

[aws-isucon](https://github.com/matsuu/aws-isucon) を参考に、過去問環境の構築ができる

#### AMI から EC2 インスタンスのセットアップ (WIP)

1. [AMI](https://github.com/matsuu/aws-isucon?tab=readme-ov-file#ami) から試したい過去問のものを選択
2. AWS コンソールから「AMI からインスタンスを起動」を選択
3. インスタンスの各種設定して起動 (TODO: c5.large を選択する理由/key pair 周り/セキュリティグループの話など詳しく書けたら書く)

#### ローカルから isucon ユーザーとして ssh で繋ぐ (WIP)

ローカルにある手元の秘密鍵で ssh できるようにしたい時
基本はこれ

- https://github.com/sonots/isucon3_cheatsheet/blob/master/01.ssh.md#1-etcsshssh_config-%E3%81%AE%E8%A8%AD%E5%AE%9A%E7%A2%BA%E8%AA%8D
- https://github.com/sonots/isucon3_cheatsheet/blob/master/01.ssh.md#2-ssh-keygen-if-you-do-not-have-a-key

#### EC2 に置かれているソースを git で ssh 経由で管理する (WIP)

ローカルにある手元の秘密鍵で ssh 経由で git を扱いたい時
基本はこれ

- https://github.com/sonots/isucon3_cheatsheet/blob/master/01.ssh.md#3-ssh-agent-%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%A6%E3%83%AA%E3%83%A2%E3%83%BC%E3%83%88%E3%81%A7%E3%82%82%E8%87%AA%E5%88%86%E3%81%AE%E7%A7%98%E5%AF%86%E9%8D%B5%E3%81%A7-github-%E3%81%AB%E3%82%A2%E3%82%AF%E3%82%BB%E3%82%B9%E3%81%99%E3%82%8B

#### 個人の.gitconfig で仕込んでいる 設定を流し込む (WIP)

isucon ユーザーに切り替えて、home directory 直下に.gitconfig を作成して流し込むのみ (scp するなりコピペするなりそこはよしなに)

#### 個人の DB クライアントから MySQL に繋ぐ (WIP)

ssh 経由で、ローカルの秘密鍵を使って繋ぐ

参考

- [DBeaver を使って ssh で DB に繋ぐ方法](https://yoshinorin.net/articles/2022/02/11/dbeaver-ssh-tunnering/)

#### Ansible を使ってサーバに入れたいツールを流し込む (WIP)

- pt-query-digest
- alp

#### Go のアプリ解析用に pprof 入れる (WIP)

### 計測

本番のアプリが Nginx と MySQL を使っていることが前提

#### スロークエリ (WIP)

pt-query-digest を使う

TODO

- MySQL の設定でスロークエリを吐き出すようにする
- ログローテ
- ADMIN PREPARE 対策

#### Nginx のアクセスログ (WIP)

alp を使う

TODO

- アクセスログのグルーピング

### 便利コマンド類 (WIP)

よく使うコマンドは、Makefile で完結するように

- top/htop
- systemctl
- journalctl
- alp
