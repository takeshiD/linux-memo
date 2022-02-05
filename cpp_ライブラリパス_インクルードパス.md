# aptでインストールしたライブラリ読み込みデフォルトパス
基本的には`/usr/lib/x86_x64-linux-gnu`にある。

## ライブラリ読み込みパスの確認
`/etc/ld.so.conf`に書かれている。

```sh
$ cat /etc/ld.so.conf
include /etc/ld.so.conf.d/*.conf
```

と書かれていたのでさらにたどってみる

```sh
$ cat /etc/ld.so.conf.d/*.conf
usr/lib/x86_64-linux-gnu/libfakeroot                                             
# libc default configuration
/usr/local/lib$
# Multiarch support
/usr/local/lib/x86_64-linux-gnu
/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu
```
ここに書かれているものはgccで-Lに入れなくてOK
