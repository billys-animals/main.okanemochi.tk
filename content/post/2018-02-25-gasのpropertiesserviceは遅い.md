---
title: GASのPropertiesServiceは遅い
author: スフィア
type: post
date: 2018-02-25T10:16:05.000Z
categories:
  - プログラム言語
tags:
  - GAS
---
簡易データベース的に使えるかも知れないと思い、PropertiesServiceを試してみました。A列にAmazon ASINコードを100件入力して、そのASINコードの行番号をPropertiesServiceで覚えさせようとプログラムで書き込みました。ASINの処理を行った際に１件ずるでなく、10件処理や複数処理をした際のAPIの戻りをセットする際にどの行に戻せば良いか連想配列に入っていると便路だと思い試してみましたがちょと厳しいみたいです。

`var dp = PropertiesService.getScriptProperties();`

`/`` `_`最終列を取得する関数を呼び出す`_` ``/
var lastRows = getLastRowNum();`

`var clsRange = "A2:A"+ String(lastRows);
var dataRange = sheet_main.getRange(clsRange);
var data = dataRange.getValues();`

`for(i=2;i&lt;=lastRows;i++){
  /`` `_`プロパティーにINDEX番号を書き込む処理`_` ``/
  dp.setProperty(data[i-2], i);
}`

プロパティーにINDEX番号を書き込む処理があるとこの処理は１分くらいかかります。プロパティーにINDEX番号を書き込む処理をコメントアウトすると２秒か３秒で終わります。

なので、数個の定数的な値の保持には重宝しますが、大量の情報をハッシュデータベース的に使う目的には向かないという事が確認出来ました。
