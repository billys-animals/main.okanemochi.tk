---
title: Python3.6をVPS(Comoha)にインストール
author: スフィア
type: post
date: 2018-02-21T05:50:27.000Z
categories:
  - 設定
tags:
  - APACHE
  - Python3
---
■apacheからPythonをCGIとして利用できる様にする。

以下より引用

> https://ponvire.com/2017/11/05/awsec2%E3%81%A8apache%E3%81%A7python%E3%82%92cgi%E3%81%A7%E5%8B%95%E3%81%8B%E3%81%99%E6%96%B9%E6%B3%95/
  
> awsec2とapacheでpythonをcgiで動かす方法

&nbsp;

### <span id="Apache1" class="ez-toc-section">Apacheの設定</span>

<pre class="lang:vim decode:true EnlighterJSRAW">下記コマンドでApacheの設定ファイルを開きます。
sudo vi /etc/httpd/conf/httpd.conf
332行目の&lt;Directory “/var/www/html”&gt;のOptionsを下記のように「ExecCGI」を追加します。
Options Indexes FollowSymLinks
↓
Options Indexes FollowSymLinks ExecCGI
797行目を下記のようにコメントを削除し、「.py」を追加します。
#AddHandler cgi-script .cgi
↓
AddHandler cgi-script .cgi .py</pre>

&nbsp;

■まずはpython3.6をソースよりインストール

<pre class="lang:vim decode:true EnlighterJSRAW">cd /usr/local/src
wget https://www.python.org/ftp/python/3.6.1/Python-3.6.1.tgz
tar -xzvf Python-3.6.1.tgz
cd Python-3.6.1
./configure --enable-shared --prefix=/usr/local LDFLAGS="-Wl,-rpath /usr/local/lib"
make
make altinstall</pre>

■次にシンボリックリンクの設定

<pre class="lang:vim decode:true EnlighterJSRAW">ln -s /usr/local/bin/python3.6 /usr/local/bin/python3
ln -s /usr/local/bin/pip3.6 /usr/local/bin/pip3</pre>

python2がyumやら色々と参照したりしているのでpythonのシンボリックリンクはそのまま2.7を残す。

インストールしたパスを1行目に書くことでPython3.6を使うことが出来る

<pre class="lang:python decode:true EnlighterJSRAW ">#!/usr/local/bin/python3
# coding:utf-8

def main():
    # HTMLに出力
    print("Content-Type: text/html\n");
    print("Hello World!!");

if __name__ == "__main__":
    main()</pre>

&nbsp;

この状態から↑のプログラムを実行する。

を実行する事で、Pythonの拡張子のまま(.py)ブラウザからプログラムを実行させる事が出来ます。Python3.6を指定しているのでバージョンも2.7でなく3.6で実行が可能となります。

<a href="https://px.a8.net/svt/ejp?a8mat=2ZH6XJ+E4HHOY+3L4M+6MROH" target="_blank" rel="nofollow noopener"><br /> <img src="https://www28.a8.net/svt/bgt?aid=180521047854&wid=061&eno=01&mid=s00000016735001114000&mc=1" alt="" width="300" height="250" border="0" /></a>
  
<img src="https://www11.a8.net/0.gif?a8mat=2ZH6XJ+E4HHOY+3L4M+6MROH" alt="" width="1" height="1" border="0" />
