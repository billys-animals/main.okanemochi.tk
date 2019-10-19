---
title: KUSANAGIで常時SSL化＆WWW無し設定の統一
author: スフィア
type: post
date: 2018-06-25T05:53:29.000Z
categories:
  - wordpress
---
Apacheの場合は.htaccessでhttpをhttpsに書き換えたりしますが、KUSANAGIは仮想空間ですし、nginxで動いているので正直なところ、httpでアクセスされた場合にhttpsに変換する手法が調べても分からず迷っていました。

## KUSANAGIで、nginx環境の時のhttp->https処理

ネットでは色々な人が色々書いていてどれも本当なのでしょうが、バージョンが古かったり、スペルの打ち間違いたオプションの書き間違いがあった様で上手く機能しませんでしたが、先ほど出来たので備忘の為に残しておきます。

出来てしまえばコマンド一発で簡単なのですが、分かるまでに時間がたくさんかかりました。同じお悩みの方のお力になれれば嬉しいです。

&nbsp;

<img class="alignnone wp-image-506" src="https://okanemochi.tk/wp-content/uploads/2018/06/kusanagi_ssl-1-300x125.png" alt="" width="564" height="235" srcset="https://okanemochi.tk/wp-content/uploads/2018/06/kusanagi_ssl-1-300x125.png 300w, https://okanemochi.tk/wp-content/uploads/2018/06/kusanagi_ssl-1.png 717w" sizes="(max-width: 564px) 100vw, 564px" />

```vim
cd /home/kusanagi/該当するプロビジョン

常時SSL化するプロビジョンディレクトリ内で以下を実行

kusanagi ssl --https redirect プロビジョン名
```


## KUSANAGIで、nginx環境の時の常時www無しの設定

加えて、常時www無しの設定にするには、当サイトで言えば、

```vim
server {
    listen       80;
    server_name  okanemochi.tk;
    return       301 https://okanemochi.tk$request_uri;
}
```

上の様に書いたものを以下のファイルの先頭に加える。
```vim
/etc/nginx/conf.d/プロビジョンのhttp.conf
```

加えた後で、nginx を再起動します。

```bash
/bin/systemctl restart nginx.service
```
