# sshを使う

## Shell(RSA)

* client
  1. ssh-keygenして`~/.ssh/`に秘密鍵・公開鍵を保存する。
  1. `~/.ssh/config`に接続時の設定を書く(細かいプロトコルの設定・鍵の使い分けをしないならなしでもよい)。

* server
  1. `/etc/ssh/sshd_config`(opensshの場合)に設定を書く。
  1. `~/.ssh/authorized_keys`(opensshのデフォルト)にclient側で生成した公開鍵を追記する。
  1. sshdを起動する。
