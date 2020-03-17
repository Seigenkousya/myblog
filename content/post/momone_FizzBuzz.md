---
title: "世界一かわいいプログラムを書こう"
date: 2019-12-06T23:07:49+09:00
tags: ["技術活動","どうして私が美術科に"]
categories: "技術活動"
draft: false
---

この記事は「[まんがタイムきらら Advent Calendar 2019](https://adventar.org/calendars/4098)」の13日目の記事です。


### 注意
この記事の元となるプログラムは今年の2月のMAXの発売日の直後という僕史上最もメンタルがイカれていた時期に書かれたものです。  
狂気的な内容ではございますがお付き合いください。  

# はじめに
みなさんプログラム書きます？  
まぁ書いたこと無い人もいれば自作言語をガンガン開発している人もいるでしょう（多分）   
プログラムっていうのはこんな奴です。（~~ねねっちが3Tab派の変態プログラマーって本当何ですか？~~）  
![programming.png](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcS4bRXdaaKDbNLBM1s_1bsOTKJ7V86_9Ccy1dyKhQlX5MCkNkRA)  
プログラムには美しいプログラムとそうでないプログラムがあります。  
美しいプログラムというのは要は誰が見ても内容を理解しやすく見やすいプログラムです。これが書ける人はちやほやされます。  
逆に読みづらいプログラムは内容が理解しづらかったり、後で修正するのが面倒だったりもうそれは大変です。  
  
あるとき僕は考えました。この世に美しいプログラムやカッコいいプログラムがあっても、見ていて癒されるかわいいプログラムは無いなぁと。  
プログラムを書いているときに思うように動かなければ心が荒みます。  
しかし、そのプログラム自体が美少女だったらどうでしょう。自然と笑顔を取り戻すことができるはずです。  
そして、当時の僕にはもう一つこのかわいいプログラムを書かねばならない理由がありました。  
それがこちらです。  
<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">【おしらせ】本日2月19日発売のまんがタイムきららMAXに「どうして私が美術科に!?」38話目載せてもらっています。<br>そして次号、最終話です。 <a href="https://t.co/Ars5radT6o">pic.twitter.com/Ars5radT6o</a></p>&mdash; 相崎うたう@きららMAXゲスト (@py_py_ai) <a href="https://twitter.com/py_py_ai/status/1097828975823413249?ref_src=twsrc%5Etfw">February 19, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 
僕の[Qiitaの記事](https://qiita.com/Seigenkousya)を読んだことのある人ならお分かりでしょうが、僕はこの出来事に大きなショックを受け1月半以上家に引きこもっていました。  
不眠と嘔吐に耐えながら僕はプログラムに打ち込むことで気を紛らわせていました。  
当時の僕には癒されるプログラムが、心の支えが必要だったのです。  
そんなこんなで非常に不純な理由で僕はこのプログラムを書き始めたのです。[^2]  

## 用意するもの
- かわいいsomething
- 技術力
- 精神力
- 半ば狂気ともいえる執念

世界一かわいいプログラムを書くには世界一かわいい美少女が必要です。  
僕にとっては「どうして私が美術科に！？」[^1]の酒井桃音ちゃんだったので（ももきなをすこれ）桃音ちゃんの力を借りてプログラムを書こうと思います。  
モデルにするイラストは以下。  
<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">【おしらせ】11月19日発売のまんがタイムきららMAXに「どうして私が美術科に!?」11話目載せてもらっています。初めての合同制作、ということでグループ名からどんな作品を作るのかまで悩みっぱなしな回です。そしてセンターカラーを頂いた来月号にお話は続きます。よろしくお願いします！ <a href="https://t.co/4GxWCpKfDh">pic.twitter.com/4GxWCpKfDh</a></p>&mdash; 相崎うたう@きららMAXゲスト (@py_py_ai) <a href="https://twitter.com/py_py_ai/status/799947825924554752?ref_src=twsrc%5Etfw">November 19, 2016</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 
~~か゛わ゛い゛い゛な゛ぁ゛桃゛音゛ち゛ゃ゛ん゛~~  

ちなみにこの号の予告絵（桃音）と次号の予告絵（黄奈子）がつながっていてヤバみがヤバい（僕はこれで1000回死んだ）  
どうびじゅについて語ると世界中のリソースを使い尽くしても語りきれないので省略しますが、賢明な読者諸氏なら既にご存知でしょう。  

### 環境  
一応技術記事らしく。

```terminal
$ uname -a
Linux kali 4.18.0-kali2-amd64 #1 SMP Debian 4.18.10-2kali1 (2018-10-09) x86_64 GNU/Linux
$ perl --version
This is perl 5, version 28, subversion 1 (v5.28.1) built for x86_64-linux-gnu-thread-multi
```
何でPerlなの？ねぇねぇ何で？的なツッコミはなしで。[^3]  


## 対象とするプログラム
プログラマの技能の基本とも言えるFizzBuzzにしましょう。  
FizzBuzzというのは数字を順に羅列していって、もし3で割りきれるなら数字の代わりにFizzもし5で割りきれるなら数字の代わりにBizzそれ以外ならそのまま数字を表示する簡単なプログラムです。  
表示例はこんな感じ。  
```
1
2
Fizz　（3は3の倍数）
4
Buzz　（5は5の倍数）
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz　（15は3と5の倍数）
16
17
Fizz
19
Buzz
```
これらの処理を愚直に書くとこうなります。~~めちゃくちゃ愚直だなぁ~~  

```perl
#!/bin/perl

use strict;
use warnings;

my $i=0;
my $max=10000;
my $digit=$max=~tr/0-9/0-9/;

for($i=1;$i<=$max;$i++){
	if(($i%3)==0 && ($i%5)==0){
		printf"%${digit}d | FizzBuzz\n",$i;
	}elsif(($i%3)==0){
		printf"%${digit}d | Fizz\n",$i;
	}elsif(($i%5)==0){
		printf"%${digit}d | Buzz\n",$i;
	}else{
		printf"%${digit}d |\n",$i;
	}
}
```

これらを限界まで短くしていきます。  

```perl
for(1..100){
	if(!($_%3)){
		print("Fizz");
	}elsif(!($_%5)){
		print("Buzz");
	}else{
		print($_);
	}
	print("\n");
}
```
とりあえず余計な宣言とか処理をすべて排除します。  

そして後置forや三項演算子を使って限界までコードを切り詰めます。  
```perl
print(($_%3?"":Fizz).($_%5?"":Buzz)or$_)for 1..100
```
だいぶ小さくなりました。  
これらをコンパイルの通る最小単位に分割します。
最小単位に分割することでAAに混ぜても違和感が無いようにします。  

```perl
print
(
	(
		$_
		%
		3
		?
		""
		:
		Fizz
	)
	.
	(
		$_
		%
		5
		?
		""
		:
		Buzz
	)
		or
	$_
)
for
1
..
100
```

準備ができたらターミナルに桃音ちゃんを降臨させます。  
画像をアスキーアートに変換するのが楽でしょう。自分で変換プログラムを書くなり[ここ](https://tool-taro.com/image_to_ascii/)を使うなりしましょう。  
ターミナルの背景は黒が多いので黒の人はあらかじめ画像の白黒を反転させると上手くいきます。（pythonのスクリプト書いた）  
そうしたら後はさっき作ったプログラムと合成させるだけです。  
今回は最も愚直で簡単な方法を書きます。（これ以外にも方法はたくさんあるがこれが一番簡単）  
行頭にPerlのコメントアウトである#を付けてさっきの細分化されたコードを頭につける方法です。（固定ツイに載せているのはこの方式）  
これにより生成したアスキーアートがすべて行頭の#によってコメントアウトされプログラム的な意味を持たなくなります。  
そして#の前にある細分化されたプログラムだけが意味を持つ命令として解釈されるので綺麗に動くという算段です。（~~ぶっちゃけコメントアウトを使うのはずるいと思う~~）  
  
つけてみるとこんな感じ。  
![momone_FizzBuzz](/images/1_momone_FizzBuzz.png)
か゛わ゛い゛い゛な゛ぁ゛桃゛音゛ち゛ゃ゛ん゛  
プログラムとして実行すると実行結果は無論こうなりちゃんと動いていることが確認できます。  
```
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
16
17
Fizz
19
Buzz
...（以下100まで）
```
これにより世界で一番かわいいFizzBuzzを書くことに成功しました。  
ありがとう桃音ちゃん。ありがとう相崎先生。  
ソースコードはこちら。  
[https://github.com/Seigenkousya/momone_fizzbuzz](https://github.com/Seigenkousya/momone_fizzbuzz)
  
Twitterに載せたやつ  
<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">精神が限界に達した時に書いた世界一かわいいFizzBuzzです<a href="https://twitter.com/hashtag/doubiju?src=hash&amp;ref_src=twsrc%5Etfw">#doubiju</a> <a href="https://twitter.com/hashtag/FizzBuzz?src=hash&amp;ref_src=twsrc%5Etfw">#FizzBuzz</a> <a href="https://t.co/xhWfHXqFqw">https://t.co/xhWfHXqFqw</a> <a href="https://t.co/8Cx3dUAE4q">pic.twitter.com/8Cx3dUAE4q</a></p>&mdash; 正弦工社 (@Seigenkousya) <a href="https://twitter.com/Seigenkousya/status/1131209142880784384?ref_src=twsrc%5Etfw">May 22, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 


# 終わりに
一応、「まんがタイムきらら Advent Calendar 2019」ってことでプログラム分からん人にも熱意だけは伝えられるようにしたんですがどうですかね？  
このAdvent calendarの為にこのブログを構築したんですがgithub pages+hugoを使ってmarkdownで簡単に記事が書けるようになったので満足です。  
暇を見つけて非技術系の純然たるきららの記事も追加で何個か頑張って書きたいなぁ。（あわよくばAdvent calendarもせっかくなのでもっと埋めたい） 
いつかこのネタは記事にしてまとめたいと思っていたネタをまとめられてスッキリ。  
技術的にはまだまだ頑張りようがあるので精進したいです。  
  
どうして私が美術科に！？を買おう！（ダイマ）  
[1巻：https://www.amazon.co.jp/gp/product/B06XFYK4PN?ref_=dbs_p_pwh_rwt_anx_cl_0&storeType=ebooks](https://www.amazon.co.jp/gp/product/B06XFYK4PN?ref_=dbs_p_pwh_rwt_anx_cl_0&storeType=ebooks)  
[2巻：https://www.amazon.co.jp/gp/product/B07BRMN6S7?ref_=dbs_p_pwh_rwt_anx_cl_1&storeType=ebooks](https://www.amazon.co.jp/gp/product/B07BRMN6S7?ref_=dbs_p_pwh_rwt_anx_cl_1&storeType=ebooks)  
[3巻：https://www.amazon.co.jp/gp/product/B07QCBKKZB?ref_=dbs_p_pwh_rwt_anx_cl_1&storeType=ebooks](https://www.amazon.co.jp/gp/product/B07QCBKKZB?ref_=dbs_p_pwh_rwt_anx_cl_1&storeType=ebooks)  

## これから
実はこれのQuineバージョンもあるのでそれも記事にしてAdvent calendarに加えたいなぁと思っています。  
任意のCのコードと画像からASCIIプログラムを生成するツールを作るのが当面の目標なので頑張りたいです。  

[^1]:どうびじゅは僕の人生です。[Amazonのリンク](https://www.amazon.co.jp/dp/B06XFYK4PN/ref=dp-kindle-redirect?_encoding=UTF8&btkr=1)
[^2]:今は相崎先生の新作である「月が綺麗だから盗んで」の読み切りが載ったので比較的精神が安定してます。
[^3]:単純に個人レベルで書き捨てるなら自由度が高く書きやすいからかなぁ


