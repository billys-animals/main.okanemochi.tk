---
title: Zenfone５(A500KL)やZenfone２(ZE551ML)の文鎮化復旧に関する情報のまとめ
author: スフィア
type: post
date: 2018-04-18T07:30:23+00:00
url: /mov_smaho/zenfone/146/
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
pvc_views:
  - 826
ampforwp-amp-on-off:
  - default
primary_category:
  - 13
keni_layout_post:
  - layout-basic
keni_layout_post_sidebar:
  - layout-sidebar-basic
keni_layout_post_navigation:
  - layout-navigation-show
keni_primary_category_post:
  - 13
keni_relation_post:
  - 'a:0:{}'
keni_post_fb_time:
  - 1568386223
  - 1568386223
  - 1568386223
categories:
  - ZenFone
  - 文鎮化

---
AsusのZenfone5（A500KL）とZenfone2（ZE551ML)を所有しています。昔、A500KLを使っていて壊れてしまい急遽購入したのでZenfone2です。そのZenfone2も先日カスタムロム焼き後に文鎮化してしまい。いろいろと情報を探ったので、そこからわかった事をまとめておこうと思います。

Zenfone2に関しては凡ミスで、関係ないimgファイルを焼いてしまい、画面が真っ暗状態になってしまったのです。起動はしている様だが画面が真っ暗で何も見えない状態でした。

これに関しては、

http://doplxyz.livedoor.biz/archives/52097110.html

ここにある手法をそのまま使い、見事に生還する事が出来ました。

> ※xfstk-downloader_v1.7.0については、いろいろな環境で試しました。
> 
> Windows10 64bit ×
> 
> Windows10 32bit ×
> 
> Windows7 64bit ○
> 
> Windows7 32bit ○
> 
> WindowsXP 32bit ○（但し、当方環境では肝心のZenfone2がUSB経由でうまく認識しないので×）

上記の様にxfstk-downloader_v1.7.0でブートローダーを復活させてから、Asus Flash Toolで書き込み復活させます。

Asus Flash Toolで読み込むROMはRAWデータが必要で、以下より取得します。

<blockquote class="wp-embedded-content" data-secret="ODQYR4htd3">
  <p>
    <a href="https://addrom.com/rom-raw-unbrick-asus-zenfone-2-ze551ml/">ROM raw unbrick for Asus Zenfone 2 (ZE551ML)</a>
  </p>
</blockquote>

<iframe class="wp-embedded-content" sandbox="allow-scripts" security="restricted" style="position: absolute; clip: rect(1px, 1px, 1px, 1px);" src="https://addrom.com/rom-raw-unbrick-asus-zenfone-2-ze551ml/embed/#?secret=ODQYR4htd3" data-secret="ODQYR4htd3" width="600" height="338" title="&#8220;ROM raw unbrick for Asus Zenfone 2 (ZE551ML)&#8221; &#8212; addROM.com" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

&nbsp;

じゃあ同じAsusだし、Asus Flash Toolの端末リストにZenfone5(A500KL)もあるので同じように復活出来るかというとそうでもありません。

正確には、Asus Flash Toolの利用はたぶん出来ます（RAWファイルでなくZIP形式での利用）

但し、Asus Flash Toolは最低限ブートローダーが復活している状態でないと利用出来ません。当方のZenfone5(A500KL)は起動時にError Invaild boot image!!というメッセージが出て停止してしまい、電源＋ボリューム↑矢印でリカバリーモードが動かずにCSCモードで立ち上がります。

電源＋ボリューム↓矢印で選択メニューが開きますが、１のSDダウンロードモードを選んでも、２のモードを選んでも最初のError Invaild boot image!!の画面に戻ります。

思うに、boot.imgやsystem.imgが壊れているか？ハード本体が壊れているかのどちらかが原因だと思います。

原因で前者であるならば何とか直したいと思い、上記のZenfone2を復活させたxfstk-downloaderの利用が出来ないか調査実験しました。

結果、駄目でした。xfstk-downloaderというツールはインテルのCPU専用に作られているのでスナップドラゴンのCPUであるZenfone5(A500KL)では基本的に使えないのです。

なので、Asusのスマホで型番の末尾がKLで終わる製品に対しては使えません。(A500KL *KL型番は皆（Qualcomm® Snapdragon）)

ちなみに、↑のZenfone2はMLでIntelのCPUなので使えます。

&nbsp;

**_xfstk-downloaderの一番下のタブと利用出来る機種の対応関係を調査しました。_**

**_　★MFD C0/D0/D1 + CLV A0_**
  
**_　　*CG型番は皆（Intel® Atom™ Z ）＊_**

**_    ★MRD A0/B0 + MOOR A0 + CRC_**
  
**_        *ML型番(Merrifield)は皆（Intel® Atom™ Quad Core Z ）＊_**
  
**_        ZE551ML , DELL venu8 3840_**

**_   ★BAYTRAIL B0_**
  
**_        *Intel Bay Trail-M SoC Celeron_**

**_   ★CLV B0/C0_**
  
**_        *Intel® Atom™ Multi-Core Z_**

**_   ★CLVP A0/B0/B1_**
  
**_        Applicable devices : zenfone 4,zenfone 5, zenfone 6 ( CG versions)_**
  
**_       *CG型番は皆（Intel® Atom™ Z ）＊_**
  
**_       なので型番の最後がCGの場合は使用可能_**

&nbsp;

以上の様にA500KLはxfstk-downloaderでは復活させることは出来ません。

それもさらに調査を行い、xfstk-downloader以外の方法を探しました。

http://en.miui.com/thread-275645-1-1.html

要は↑でやっている様にすればよいのですが、一つ問題があります。

現在のZenfone5はブートローダーが立ち上がらないわけで、事前にAPKをインストールして「ブートローダーをアンロックしていない」のです。

壊れる前にOEMロックを解除してあれば↑の方法も使えますが、ロックされたままなのでROMの書き換えが出来ないのでお手上げです。

なので、完全に諦めです。

蛇足ですが、↑で示した「ZenFone5LTEStock.img」をダウンロードして、

壊れたA500KLをUSBでつないで、CSCモードの状態であれば、

<pre class="lang:vim decode:true ">fastboot boot ZenFone5LTEStock.img</pre>

&nbsp;

でリカバリーメニューは起動します。がエラーだらけで何もつかません。

<pre class="lang:vim decode:true ">fastboot flash boot ZenFone5LTEStock.img</pre>

&nbsp;

これも一見はエラーなく書き込める様に見えますが実際には書き込めていません。

EDLモードも少しは試しましたがやはり駄目（結局のところ、EDLモード＝CSCモードなのか？）出来る事に変わりはないと感じました。

Zenfone5（A500KL)に関しては、今動いている人は早めに

Unlock Device App: Unlock boot loader

http://dlcdnet.asus.com/pub/ASUS/ZenFone/A500KL/0530-1020\_SIGNED\_UnLock.zip?_ga=2.193392557.168829003.1523662140-2014318853.1523662140

これをインストールしてブートローダーのロックを解除しておいたほうがよいでしょう。

そうしないと先の「Error Invaild boot image!!」が出た時に自力では復活不可能な状態になります。

ブートローダーが解除されていれば、ストックROMを焼き直し自力での復活もそう難しい作業ではないと思われます。

&nbsp;

ちなみに我が家では当方が中古のZenfone5を利用し始めて６ヶ月で、嫁が新古のZenfone5を利用し始めて②年弱で「Error Invaild boot image!!」の状態になり再起不能です。

ちなみにカスロムに焼き直したりせずメーカーのOTAアップデートのみの運用で堅実に使っていて突然に「Error Invaild boot image!!」この状態です。

娘は新品で購入したもので、もう４年も使っていますが今のところ大丈夫です。ロットにより当たり外れが大きいのかもです。

&nbsp;

ちなみに、XiaoMiFlashというツールを使えば一応USBにつながったZenfone5を認識はしますが、いかんせん、Xiaomiのスマホ用のフラッシュツールなのでZenfone5のROMでは書き込みは当然出来ません。さすがに、スナップドラゴンCPU用のツールなので、ブートローダーが立ち上がらないZenfone5でもCOM3等で認識はします。でもそれだけです、、、。

&nbsp;