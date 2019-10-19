---
title: Chatwork APIによる指定場所への書き込み
author: スフィア
type: post
date: 2018-06-01T22:14:49+00:00
url: /computer_language/gas/265/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/06/6185878460_81212fcc99_q.jpg
categories:
  - GAS

---
```js
// チャットワークAPIのAPIトークン
var api_token = 'チャットワークのAPIトークン';

// 送信先のチャットのID
var room_id = 送信先のチャットのID;

//メール送信先のアドレス
var toEmail = "メール送信先のアドレス";

//チャットワーク＆メールの本文
var txtbody = "処理が完了しました。インポートをお願いします。";

//チャットワーク＆メールのタイトル
var ss = SpreadsheetApp.getActiveSpreadsheet();
var subject = "【" + ss.getName() + "】";

function main() {

var cw = ChatWorkClient.factory({
token: api_token
});
var body = "[info][title]" + subject + "[/title]" + txtbody + "[/info]";
cw.sendMessage({
room_id: room_id,
body: body
});
sendMailForm();
Browser.msgBox('チャットワークへのメッセージ送信完了しました。');
}

/************************************************************************************
【関数概要】sendMailForm

メールを送信する。
引数のresultDataはメールのボディーに当たる内容

【引数】resultData

【戻り値】なし
***********************************************************************************/
function sendMailForm() {

// メール送信
try {
MailApp.sendEmail(toEmail, subject, txtbody);
} catch (e) {
var error = e;
Logger.log("message:" + error.message + "\nfileName:" + error.fileName + "\nlineNumber:" + error.lineNumber + "\nstack:" + error.stack);
}

}

```



<div class="chat_l ">
  <div class="talker">
    <b><img class="square" src="https://okanemochi.tk/wp-content/uploads/2018/07/%E3%82%AB%E3%83%B3%E3%83%8B%E3%83%B3%E3%82%B0-300x204.png" alt="もし、参考になったならTwitterシェアお願いします" />もし、参考になったならTwitterシェアお願いします </b>
  </div>
  
  <div class="bubble_wrap">
    <p>
    </p>
  </div>
</div>
