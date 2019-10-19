---
title: Yahoo API ItemSeach 覚書
author: スフィア
type: post
date: 2018-02-21T06:41:48.000Z
categories:
  - API
  - VBA
---
以前、開発でYahoo APIのitemSearchを扱う機会がありました。エクセルのVBAでの開発だったのですが、APIの戻りをパースする際にNamespaceが上手く動作せずに困った時に以下のページに救われました。

<a href="http://blog.apitore.com/2016/08/04/yahoo-itemsearch-api/" target="_blank" rel="noopener"><i class="icon_point"></i>Yahooの商品検索APIを使ってみた</a>

具体的には_**記事の最後に配置されている「itemSearch.xsd」**_に救われました。

公式の「itemSearch.xsd」は以下ですが、

```vim
http://shopping.yahooapis.jp/ShoppingWebService/V1/itemSearch.xsd
```

これだと、targetNamespaceが無いのでVBAでパースする事が出来ませんでした。

なので、プログラムからは公式でなく、ローカルファイルの「itemSearch.xsd」(<span>修正版のxsdファイル</span>)を参照してパースしました。

```vbs
Dim xmlschema As MSXML2.XMLSchemaCache60
Dim xmldom As MSXML2.DOMDocument60

Set xmlschema = New MSXML2.XMLSchemaCache60
Set xmldom = New MSXML2.DOMDocument60

xmlschema.Add "urn:yahoo:jp:itemSearch", ActiveWorkbook.Path & "\itemSearch.xsd"
Set xmldom.Schemas = xmlschema

xmlNamespaces = "urn:yahoo:jp:itemSearch"
strBaseUrl = "https://shopping.yahooapis.jp/ShoppingWebService/V1/itemSearch?appid=" & strAppID

    objXMLHTTP.Open "GET", strBaseUrl, False  '&lt;&lt;EDIT: GET the site
    objXMLHTTP.send
    
    objxmldoc.LoadXML (objXMLHTTP.responseText)
    objxmldoc.async = False
    objxmldoc.validateOnParse = False
    objxmldoc.resolveExternals = False
    objxmldoc.SetProperty "SelectionLanguage", "XPath"
    objxmldoc.SetProperty "SelectionNamespaces", "xmlns:defalt='urn:yahoo:jp:itemSearch'"

    Set objXMLNodexbrl = objxmldoc.SelectNodes("//defalt:ResultSet")
    
    totalResultsAvailable = objXMLNodexbrl.Item(0).Attributes(3).nodeTypedValue
```

おおよそこんな感じのVBAコードとなります。
