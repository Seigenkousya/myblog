---
title: "桃音ちゃんのAAの形をした桃音ちゃんのAAの形をした桃音ちゃんのAAの形をした...桃音ちゃんのAAを出力するプログラム"
date: 2019-12-21T23:40:35+09:00
draft: false
---
この記事は「[まんがタイムきらら Advent Calendar 2019](https://adventar.org/calendars/4098)」の23日目の記事にして[13日目](https://seigenkousya.github.io/post/momone_fizzbuzz/)のオマケ記事です。  
プログラムの見た目自体は変わってないので伝わり辛いでしょうがお付き合いください。  

# 前回のあらすじ
精神を病んで桃音ちゃん型のプログラムを書いた。  
![momone_FizzBuzz](/images/1_momone_FizzBuzz.png)
しかし、プログラムの内容はFizzBuzzという相崎先生に申し訳ないレベルの簡単なプログラム。  
もっと、見た人がおぉってなるようなプログラムにしたい。（~~あと、しょうもないコメントを使った手法から脱却したい~~）

# 今回のあらすじ
出力自体も桃音ちゃんだったらめっちゃエモく無いですか？（唐突な思いつき）  
いっそのこと自己参照型のプログラムにしたら良さそう（これをQuine[^1]と言います）。  
そんなこんな今回も気合で書いていきます。  

## 環境  
前回に引き続きPerlで。

```terminal
$ uname -a
Linux kali 4.18.0-kali2-amd64 #1 SMP Debian 4.18.10-2kali1 (2018-10-09) x86_64 GNU/Linux
$ perl --version
This is perl 5, version 28, subversion 1 (v5.28.1) built for x86_64-linux-gnu-thread-multi
```

## Quineとは？
wikiの説明を借りると、

> クワイン（英: Quine）は、コンピュータプログラムの一種で、自身のソースコードと完全に同じ文字列を出力するプログラムである。

要はプログラムと出力がまったく等しいプログラムのことです。  
perlでいうとこう。
```perl
$_=q{print"\$_=q{$_};eval"};eval
```

実際に確かめてみると、

```terminal
$ perl -E '$_=q{print"\$_=q{$_};eval"};eval'
$_=q{print"\$_=q{$_};eval"};eval
```

たしかに入力と出力が一致する。  
これは、  

1. 暗黙変数$\_に```q{print"\$\_=q{$_};eval"}```を代入する
+ evalが実行される
+ evalは暗黙的に```$_```を参照するので```q{print"\$_=q{$_};eval"}```がevalに渡される
+ q演算子```q//```より、文字列```print"\$_=q{$_};eval"```が渡されることになる
+ evalに渡される```print"\$_=q{$_};eval"```のうち、エスケープされていない```q{$_}```の部分の```$_```は最初に代入した```q{print"\$\_=q{$_};eval"}```になるので
+ 標準出力に```$_=q{print"\$_=q{$_};eval"};eval```が出力される

という流れで実行されるからです。  

これらの実行の流れを見ているとあることに気がつきます。  
それは、```print```命令の前に何を置いてもQuineとして成立するということです。  
何を書こうが暗黙変数で参照されてQuineになります。ただし、標準出力に関係ない処理である必要があります。  
例えば、変数helloを置いてもQuineは成立します。
```perl
$_=q{$hello;print"\$_=q{$_};eval"};eval
```
試してみると、

```terminal
$ perl -E '$_=q{$hello;print"\$_=q{$_};eval"};eval'
$_=q{$hello;print"\$_=q{$_};eval"};eval
```

大丈夫。  
ならばこれを応用すればAAにも適用できるのでは？と考えました。  

# 実際にやってみた
実際の構造はこんな感じ。

```perl
$_=q|q* Ascii art *;print"\$_=q{$_};eval";q* Ascii art *;|;eval;
```
できるだけAscii artの部分を最大化してコード部分を短くしました。  
q演算子の区切りにはAAで使用率の低かった```|```と```*```を採用しました。  

できたコードがこちら。（前回の上の画像と変わらないじゃないかだって？動かせば分かりますよ）  

![momone_quine](/images/momone_quine.png)

このプログラムは桃音ちゃんのAAであると同時に桃音ちゃんのAAを表示するプログラムでもあります。  
そして、この表示プログラムはQuineの要件を満たしているため自己参照プログラムでもあります。  
つまり、このプログラムは桃音ちゃんのAAを表示するプログラムであると同時に桃音ちゃんのAAを表示するプログラムを表示するプログラムでもあるのです。  
これらのことをまとめるとこのプログラムは桃音ちゃんのAAの外見をした桃音ちゃんのAAを表示するプログラムを表示するプログラムを表示するプログラムを表示するプログラム...ということになります。  

<font size="36">\~𝑯𝒂𝒑𝒑𝒚 𝑬𝒏𝒅\~</font>

# 終わりに
前回から少し成長してコメントを使ったせこい技を使わずに済んだのは大きいかなと思います。  
桃音ちゃんから桃音ちゃんが生成されるなんて素晴らしいですね。  
まだまだ可能性はいっぱいあると思うのでこれからも精進したいなぁと思いました。  

まぁこれを読んでいる読者諸氏なら当然持っているだろうが、一応言っておく。  
どうして私が美術科に！？を買おう！（ダイマ）  
[1巻：https://www.amazon.co.jp/gp/product/B06XFYK4PN?ref_=dbs_p_pwh_rwt_anx_cl_0&storeType=ebooks](https://www.amazon.co.jp/gp/product/B06XFYK4PN?ref_=dbs_p_pwh_rwt_anx_cl_0&storeType=ebooks)  
[2巻：https://www.amazon.co.jp/gp/product/B07BRMN6S7?ref_=dbs_p_pwh_rwt_anx_cl_1&storeType=ebooks](https://www.amazon.co.jp/gp/product/B07BRMN6S7?ref_=dbs_p_pwh_rwt_anx_cl_1&storeType=ebooks)  
[3巻：https://www.amazon.co.jp/gp/product/B07QCBKKZB?ref_=dbs_p_pwh_rwt_anx_cl_1&storeType=ebooks](https://www.amazon.co.jp/gp/product/B07QCBKKZB?ref_=dbs_p_pwh_rwt_anx_cl_1&storeType=ebooks)  


[^1]:[Quineのwikipedia](https://ja.wikipedia.org/wiki/%E3%82%AF%E3%83%AF%E3%82%A4%E3%83%B3_(%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%9F%E3%83%B3%E3%82%B0))
