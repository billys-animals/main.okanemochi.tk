---
title: Amazon MWS API FEED
author: スフィア
type: post
date: 2018-05-09T13:39:49+00:00
url: /web_tecnology/api/211/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/09/99095312_947217f5d3_o.png
categories:
  - API
  - GAS
  - PHP

---
```js
//Feed用
var namespace3 = "http://mws.amazonaws.com/doc/2009-01-01/";
var namespace4='"http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="amzn-envelope.xsd"';

/*************************************************************************
 SubmitFeed
 FeedType=_POST_INVENTORY_AVAILABILITY_DATA_
 
 ＜＜トランザクショ＞＞
 SubmitFeed　「リクエスト送信してFeedSubmissionIdを取得」
  =&gt;GetFeedSubmissionList(FeedSubmissionId)「FeedSubmissionIdにてオペレーション送信」
     =&gt;GetFeedSubmissionResult(FeedSubmissionId)「オペレーション完了する」
*************************************************************************/
function putFeedSubmit() {
    var u = "https://" + mws_address + "/?";

    //任意の値を設定します
    var sku1        = "test-6";
    var quantity1   = "1";
    var leadTimeToShip1 = "7";

    var AWS_KEYS = "XXXXXXXXXX";
    var AWS_SCEC="11444AAAAAAADDDDDD";
    var SellerId= "AAAAQ44444444";
    var MWS_VERSION="2009-01-01";
    var mws_address = "mws.amazonservices.jp";

    //XMLファイルのひな形にパラメータを埋め込む
    var payload = '&lt;?xml version="1.0" encoding="utf-8"?&gt;';
        payload += '&lt;AmazonEnvelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="amzn-envelope.xsd"&gt;';
        payload += "&lt;Header&gt;";
        payload += "&lt;DocumentVersion&gt;1.01&lt;/DocumentVersion&gt;";
        payload += "&lt;MerchantIdentifier&gt;"+SellerId+"&lt;/MerchantIdentifier&gt;";
        payload += "&lt;/Header&gt;";
        payload += "&lt;MessageType&gt;Inventory&lt;/MessageType&gt;";
        payload += "&lt;Message&gt;";
        payload += "&lt;MessageID&gt;1&lt;/MessageID&gt;";
        payload += "&lt;OperationType&gt;Update&lt;/OperationType&gt;";
        payload += "&lt;Inventory&gt;";
        payload += "&lt;SKU&gt;"+sku1+"&lt;/SKU&gt;";
        payload += "&lt;Quantity&gt;"+quantity1+"&lt;/Quantity&gt;";
        payload += "&lt;FulfillmentLatency&gt;"+leadTimeToShip1+"&lt;/FulfillmentLatency&gt;";
        payload += "&lt;/Inventory&gt;";
        payload += "&lt;/Message&gt;";
        payload += " &lt;/AmazonEnvelope&gt;";

    /*******************************************************************************
    　ContentMD5Value用のMD5ハッシュ（バイナリー値）取得の為にPHPプログラムを呼出しする（ここから）
　　　 Google Apps ScriptよりPHPを呼出しPOSTするサンプル
    *******************************************************************************/
    //＜＜＊＊　自運営サイト参照用　＊＊＞＞
    //var url = 'https://okanemochi.tk/md5/index5.php';
        //＜＜＊＊　heroku登録APP参照用　＊＊＞＞
    var url = 'https://getmd5hushed.herokuapp.com/';   
    
    var option = {
      "method":"POST",
      "Content-Type": "application/json",
      "payload": payload,
      "muteHttpExceptions" : true,
    }   
    var response = UrlFetchApp.fetch(url,option);  
    var data = JSON.parse(response.getContentText());
  　f_hush=data["message"];
   
    /*******************************************************************************
    　ContentMD5Value用のMD5ハッシュ（バイナリー値）取得の為にPHPプログラムを呼出しする（ここまで）
    *******************************************************************************/
     
    //　＊＊＊　以下、署名に必要なパラメーター　（ここから）＊＊＊
    var o1 = {
        "Version": MWS_VERSION,
        "Action": "SubmitFeed",
        "AWSAccessKeyId": AWS_KEYS,
        "Merchant": SellerId,
        "SignatureVersion": "2",
        "Timestamp": new Date().toISOString(),
        "SignatureMethod": "HmacSHA256",
        "MarketplaceIdList.Id.1": "A1VC38T7YXB528",
        "FeedType":"_POST_INVENTORY_AVAILABILITY_DATA_",
        //"FeedType":"_POST_PRODUCT_DATA_",
        "PurgeAndReplace":"false",
        "ContentMD5Value": f_hush
    }
    var a = Object.keys(o1).sort();
    a = a.map(function (key) {
        return key + "=" + encodeURIComponent(o1[key]);
    });   
    var sign  = "POST" + "\n";
    sign += mws_address + "\n";
    sign += "/\n";
    sign += a.join("&");
    var x = Utilities.base64Encode(Utilities.computeHmacSha256Signature(sign, AWS_SCEC));
    
    //　＊＊＊　署名作成(変数x)　（ここまで）＊＊＊
 
    //API接続用のURL生成
    var uri = "https://"+ mws_address +"/?";
    uri += a.join("&")+ "&Signature=" + encodeURIComponent(x);
    
    //API接続時のPOST情報生成
    var urlFetchOption = {
        "method" : "POST",
        "Content-Type": "application / xml; charset = utf-8 ",
        "payload": payload,
        "muteHttpExceptions" : true
    };
    
    var r = UrlFetchApp.fetch(uri, urlFetchOption);
    var document = XmlService.parse(r.getContentText());
    
    var root = document.getRootElement();
    var NS3 = XmlService.getNamespace(namespace3);
    var respone_node = root.getQualifiedName();
    
    //エラー確認
    if (respone_node == "ErrorResponse") {
        //var res = _sleep(10);
        return 9999;
    }

　　//データ取得
    var AttributeSets = root.getChild("SubmitFeedResult", NS3).getChild("FeedSubmissionInfo", NS3);
    var FeedSubmissionId = AttributeSets.getChild("FeedSubmissionId", NS3).getValue();
    var FeedType = AttributeSets.getChild("FeedType", NS3).getValue();
    var SubmittedDate = AttributeSets.getChild("SubmittedDate", NS3).getValue();
    var FeedProcessingStatus = AttributeSets.getChild("FeedProcessingStatus", NS3).getValue();

    return 0;
}

```


外部からPOSTされた文字列に対するMD5ハッシュ値を呼出し元に返す関数は以下に記載。

上記の62行目の

```php3
var response = UrlFetchApp.fetch(url,option);</pre>
```

で呼ぶ

```php3
var url = 'https://getmd5hushed.herokuapp.com/';
```

このサイトのindex.phpが以下です。
```php3
<?php

/* 外部からPOST呼出しされた場合の$_POST変数の取得方法 */
$request_body = file_get_contents('php://input');
/* 「$request_body」に対してデコードが必要な場合もある */

$xml=$request_body;
$data = array(
  'message' =&gt; base64_encode(md5($xml, true))
);
header('Content-Type: application/json');
echo json_encode($data);
?>
```


GASからのPOST変数(payload)を受けてMD5ハッシュ値を呼び出し元のGASに返します。

<a href="https://px.a8.net/svt/ejp?a8mat=2ZH6XJ+E4HG5E+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fudemy-images.udemy.com%2Fcourse%2F240x135%2F647944_cb57_2.jpg" target="_blank" rel="nofollow noopener">今日から実践で使える！Google アナリティクス講座</a>
  
<img src="https://www12.a8.net/0.gif?a8mat=2ZH6XJ+E4HG5E+3L4M+BW8O2" alt="" width="1" height="1" border="0" />

<div class="chat_l ">
  <div class="talker">
    <b><img class="square" src="https://okanemochi.tk/wp-content/uploads/2018/07/%E3%82%AB%E3%83%B3%E3%83%8B%E3%83%B3%E3%82%B0-300x204.png" alt="もし、参考になったならTwitterシェアお願いします" />もし、参考になったならTwitterシェアお願いします </b>
  </div>
  
  <div class="bubble_wrap">
    <p>
    </p>
  </div>
</div>
