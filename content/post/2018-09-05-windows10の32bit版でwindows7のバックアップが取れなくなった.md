---
title: Windows10の32bit版でWindows7のバックアップが取れなくなった
author: スフィア
type: post
date: 2018-09-05T09:45:35+00:00
url: /windows/751/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/09/version02-246x200.png
category_relation:
  - 'n'
tag_relation:
  - 'n'
disp_description_relation:
  - 'n'
menu_view:
  - 'y'
side:
  - 'y'
fullscreen_view:
  - 'n'
index:
  - index
follow:
  - follow
title_view:
  - 'y'
page_layout:
  - def
toc:
  - def
primary_category:
  - 148
pvc_views:
  - 74
categories:
  - Windows

---
Windows10の32bit版でWindows7のバックアップを取得しようとしたら直ぐに以下のエラー画面が出ました。

<img class="alignnone size-medium wp-image-752" src="https://okanemochi.tk/wp-content/uploads/2018/09/version02-300x161.png" alt="" width="300" height="161" srcset="https://okanemochi.tk/wp-content/uploads/2018/09/version02-300x161.png 300w, https://okanemochi.tk/wp-content/uploads/2018/09/version02.png 545w" sizes="(max-width: 300px) 100vw, 300px" />

証拠として以下にバージョンを表示します。

<img class="alignnone size-medium wp-image-754" src="https://okanemochi.tk/wp-content/uploads/2018/09/version01-300x212.png" alt="" width="300" height="212" srcset="https://okanemochi.tk/wp-content/uploads/2018/09/version01-300x212.png 300w, https://okanemochi.tk/wp-content/uploads/2018/09/version01-768x543.png 768w, https://okanemochi.tk/wp-content/uploads/2018/09/version01.png 839w" sizes="(max-width: 300px) 100vw, 300px" />

日本国内では解決できていない様で外国のテックネットのほうでバグの修正方法が載っていたので試してみました。結果、

<img class="alignnone size-medium wp-image-755" src="https://okanemochi.tk/wp-content/uploads/2018/09/version03-300x166.png" alt="" width="300" height="166" srcset="https://okanemochi.tk/wp-content/uploads/2018/09/version03-300x166.png 300w, https://okanemochi.tk/wp-content/uploads/2018/09/version03.png 550w" sizes="(max-width: 300px) 100vw, 300px" />

こんな感じでwindows10の32bitでRPCエラーにならずにバックアップを取る事ができました。

参照してのは以下のページの一番下の書き込みです。

> https://social.technet.microsoft.com/Forums/en-US/a8b8fe72-7e85-4e3d-beba-19c84c620dc8/the-backup-failed-the-rpc-server-is-unavailable-0x800706ba

書かれている内容を要約すると、c:\windows\system32/wbengine.exeが今回のバグの原因だという事。それをFIXしたバージョンをOnedrive上に置いておくからご利用下さいという事。その際に対象のファイルは「Trustedinstaller」というアカウントグループがオーナーになっているので自身のアカウントをオーナーに変更するなどの処置をして書き換える必要があると。

そういう内容でした。

### c:\windows\system32/wbengine.exeのオーナーを変更する

結構面倒なのですが、以下のページが参考になりました。

> https://freesoft.tvbok.com/win10/tips\_and\_tools/windows_1081trustedinstaller.html

上記の手順通りに、c:\windows\system32/wbengine.exeのオーナーを自分のユーザーに移し、ダウンロードした対象ファイルを上書きする事で正常にバックアップを取る事ができました。

最も、取得したバックアップからのリストアをまだ確認していないのでちゃんと取れているエビデンスはまだありません。

### 後処理もきちんとした方が良いです

c:\windows\system32/wbengine.exeのオーナーを自分のユーザーに移してバグFIX版に変更した後、再度、c:\windows\system32/wbengine.exeのオーナーをTrustedinstallerに戻す作業をしておいた方がセキュリティー上安全というのは言うまでも無いことです。お忘れなきようお願い致します。

### 最後に

同じ問題でお悩みの方は是非ご参考にしてみて下さい。最後になりますがくれぐれも自己責任でお願い致します。責任の所在は常に自分も含め実行したご本人様にございます。よろしくお願い致します。