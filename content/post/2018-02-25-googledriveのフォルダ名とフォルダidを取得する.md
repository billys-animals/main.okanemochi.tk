---
title: GoogleDriveのフォルダ名とフォルダIDを取得する
author: スフィア
type: post
date: 2018-02-25T09:59:16+00:00
url: /computer_language/gas/64/
category_relation:
  - 'n'
  - 'n'
tag_relation:
  - 'n'
  - 'n'
disp_description_relation:
  - 'n'
  - 'n'
menu_view:
  - 'y'
  - 'y'
side:
  - 'y'
  - 'y'
fullscreen_view:
  - 'n'
  - 'n'
index:
  - index
  - index
follow:
  - follow
  - follow
title_view:
  - 'y'
  - 'y'
catch_text:
  - 
  - 
header_image:
  - 
  - 
page_layout:
  - def
toc:
  - def
primary_category:
  - 27
pvc_views:
  - 279
ampforwp-amp-on-off:
  - default
keni_post_fb_time:
  - 1568356555
categories:
  - GAS

---
件名の通り「GoogleDriveのフォルダ名とフォルダID」を取得するサンプルコートを掲載します。

<pre class="lang:js decode:true ">function getAllFolderID(){
  var all_folders = DriveApp.getFolders();
  
  while (all_folders.hasNext()){
     var folder = all_folders.next();
       Logger.log('Folder名:'+folder.getName() + 'FolderID:' + folder.getId());
   }
}</pre>

GoogleDrive系の処理はフォルダIDを取得しないと操作出来ないものばかりなので最初にKey,Value形式でフォルダ名とフォルダIDを連想配列にもっておくと後の処理がスピーディーになれるかもです。