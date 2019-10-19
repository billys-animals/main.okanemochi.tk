---
title: GoogleDriveのフォルダ名とフォルダIDを取得する
author: スフィア
type: post
date: 2018-02-25T09:59:16+00:00
url: /computer_language/gas/64/
categories:
  - GAS

---
件名の通り「GoogleDriveのフォルダ名とフォルダID」を取得するサンプルコートを掲載します。

```js
function getAllFolderID(){
  var all_folders = DriveApp.getFolders();
  
  while (all_folders.hasNext()){
     var folder = all_folders.next();
       Logger.log('Folder名:'+folder.getName() + 'FolderID:' + folder.getId());
   }
}
```

GoogleDrive系の処理はフォルダIDを取得しないと操作出来ないものばかりなので最初にKey,Value形式でフォルダ名とフォルダIDを連想配列にもっておくと後の処理がスピーディーになれるかもです。
