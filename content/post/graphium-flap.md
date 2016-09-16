+++
categories = ["diary"]
date = "2016-09-16T12:24:15+09:00"
description = "ベクタグラフィックスのアオスジアゲハを羽ばたかせてみる"
tags = ["junk", "アオスジアゲハ", "svg", "javascript"]
title = "やがて竜巻を引き起こす"

+++

<object type="image/svg+xml" data="/works/graphium-flap.svg"></object>

**この記事はスマートフォンでの閲覧を推奨しています**

アオスジアゲハの構造色(目の覚めるような水色)の部分の光の反射をせっかくなので動かせないかと提案がありました。

動かせるよ、それ。

仕組みは[SVGでプログラマブルな書体を作る話](http://creator.dwango.co.jp/8741.html)の加速度センサで書体を変化させるものにならいますが、

* idを用いて画像中の要素を掴む
* センサに反応があればsetAttribute()関数を用いて属性値を直接書きかえる

という手順になっています。

書いているうちに、よーしついでに羽ばたかせてしまおう、となったのでtransform属性の値も書き換えます。

```
var grad = document.getElementById('radialGradient5666'),
  p = document.getElementById('g5651');
window.addEventListener('deviceorientation', function(e) {
  var r = 100 + (Math.abs(e.gamma)+Math.abs(e.beta))/90 * 600,
    xoff = e.beta * 10;
  grad.setAttribute('r', r);
  grad.setAttribute('cx', xoff);
  grad.setAttribute('fx', xoff);
  p.setAttribute('transform', 'translate(225.21687,-14.655479)' +
    'scale(' + (1 - Math.abs(e.beta/90)) + ', 1)');
});
```
