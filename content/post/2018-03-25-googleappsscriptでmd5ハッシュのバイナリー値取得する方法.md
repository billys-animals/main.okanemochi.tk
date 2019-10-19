---
title: GoogleAppsScriptでMD5ハッシュのバイナリー値取得する方法
author: スフィア
type: post
date: 2018-03-25T13:03:11.000Z
categories:
  - GAS
tags:
  - MD5
  - PHP
  - google apps script
  - ハッシュ
  - バイナリー値
---
アマゾンMWSで<a href="https://docs.developer.amazonservices.com/ja_JP/feeds/Feeds_SubmitFeed.html" target="_blank" rel="noopener">SubmitFeed</a>というAPIがあります。このAPI、「ContentMD5Value」というMD5ハッシュ値をパラメータに沿える必要があったりします。

GoogleAppsScriptでMD5ハッシュ値を取得するなら以下でOKです。
```html
https://gist.github.com/mogsdad/5464686
```
このモジュールの例で言えば、（変数xmlに対象のファイル内容を保有）

```js
var payload = xml;
var md5_hush = Utilities.base64Encode(signMd5(payload));
```

普通はこれでOKです。でも、今回のAPIで必要なのは↑のMD5ハッシュ値でなく、対象のファイルのバイナリー値に対するMD5ハッシュ値が必要なんです。

色々と調べましたが、上記で言うpayloadのバイナリー値に対するMD5ハッシュが必要なので、

```javascript
var blob1 = Utilities.newBlob(payload).getBytes();
var md5_hush = Utilities.base64Encode(signMd5(blob1 ));
```

こんな事も試しましたがうまくいきませんでした。

今回の問題の内容は以下のサイトの記事が解決方法を記載しています。

http://cloudway.io/post/base64-encoded-128-bit/



ですが、やはりGoogleAppsScriptでは無理なのか？も知れないと思い、諦めてPHPを利用する事にしました。

https://stackoverflow.com/questions/29820014/issue-calculating-md5-hash-of-amazon-marketplace-feed

```php
Content-MD5 => base64_encode(md5($xml, true))
```

GASからPHPが使えるサーバ上の↑のコードを仕込んだPHPファイルを呼出し、MD5ハッシュしたいファイルの中身をPOSTしてハッシュ値をGASに戻してあげればOKです。

でも、できればPHPを使わないで目的が達成できると嬉しいですね。


追記

上記の総合的な記載記事を追加しました。

[Amazon MWS API FEED][1]

<div class="chat_l ">
  <div class="talker">
    <b><img class="square" src="https://okanemochi.tk/wp-content/uploads/2018/07/%E3%82%AB%E3%83%B3%E3%83%8B%E3%83%B3%E3%82%B0-300x204.png" alt="もし、参考になったならTwitterシェアお願いします" />もし、参考になったならTwitterシェアお願いします </b>
  </div>
  
  <div class="bubble_wrap">
    <p>
    </p>
  </div>
</div>

 [1]: https://okanemochi.tk/api/211/
