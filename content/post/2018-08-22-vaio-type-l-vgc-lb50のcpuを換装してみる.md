---
title: VAIO TYPE L VGC-LB50のCPUを換装してみる
author: スフィア
type: post
date: 2018-08-22T00:40:25+00:00
url: /雑学/719/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/08/celeron420-246x200.png
category_relation:
  - 'y'
tag_relation:
  - 'y'
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
  - 17
pvc_views:
  - 143
keni_post_fb_time:
  - 1567578613
categories:
  - 雑学・日記

---
<img class="alignnone size-medium wp-image-720" src="https://okanemochi.tk/wp-content/uploads/2018/08/celeron420-169x300.png" alt="" width="169" height="300" srcset="https://okanemochi.tk/wp-content/uploads/2018/08/celeron420-169x300.png 169w, https://okanemochi.tk/wp-content/uploads/2018/08/celeron420.png 576w" sizes="(max-width: 169px) 100vw, 169px" />

VAIO TYPE L VGC-LB50のCPUは上記の様にCeleronモバイル420です。

上の赤枠の円の中心をマイナスドライバーで左に回すと、上の青枠のCPUが解除されて外せます。

この、CPUを、Intel Core2 Duo プロセッサー E8400 LGA775 SLB9J 3.00GHzに換装する予定です。

もうすぐ届くので正に蓋を開けて待っている状態です。

ただ、見込みで購入したCPUなので本当に正常に動作するかどうかはわかりません。ソケットは一致しているし、希望的観測で動作すると考えてヤフオクで350円で購入です。

結果は後に追記で書きますね。

**追記：**

よく確認せずにソケットの異なるCPUを購入してしまいました。対応する正式なソケットはPPGA478でした。E8400はソケット775なので型が合いません。自業自得とはまさにこの事！残念！！

**再追記：**

メーカー品にCPUの換装とは予想以上に神経を使う必要があるようです。

Celeronモバイル420は、

仕様番号＝ SL8VZ 、
  
ステッピング＝ C0 、
  
CPU ID＝ 06E8、
  
Socket Type =Socket M、
  
Bus speed= 533 MHz、
  
64-bit Support?= No
  
命令セット拡張＝MMX ,SSE ,SSE2 ,SSE3

など複数の項目の値を見た上で換装前のCPUとできるだけ同じ構造のものを選択する必要がある様です。また、対象のパソコンのUEFI(BIOS)の最新版の更新日よりも後に発売されたCPUは換装の対象にはなりませんので、パソコンや換装したいCPUの発売日も考慮しなければなりません。

よって、CeleronM420の換装が成功する可能性が高く、最も効果を得られる可能性が高いCPUは「Intel Core Duo T2600 (Socket M) CPU」ではないかと考えております。

仕様番号＝ SL8VZ 、SL9JN
  
ステッピング＝ C0 、Do
  
CPU ID＝ 06E8、06EC
  
Socket Type =Socket M、
  
Bus speed= 667 MHz、
  
64-bit Support?= No
  
命令セット拡張＝MMX ,SSE ,SSE2 ,SSE3

この様に基本的な構造はほぼ同じでバススピードは少し速いのと、仕様番号が複数あるのが不一致点ですね。これで適合率が70％程度なのでおそらく換装可能なのではないかと考えております。

もし、換装が成功した場合の性能としてはおよそ263％向上という指標になっています。早く結果をみたいこの頃です。

## 結果

画面真っ暗でBIOSすら立ち上がりません。念の為CMOSのクリアも試しましたが状況は変化せず。残念、断念。

やっぱりメーカー製のパソコンのCPU換装は難しいですね、ThinkPadはすんなりうまく出来たのにVAIOは散々でした。