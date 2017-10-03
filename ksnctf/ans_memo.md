### q1
テスト、入れるだけ

### q2
シーザー暗号、試しにpythonのrot13で複合したらあっさり

### q3
ソースをみるとscriptの中にニャル子さんが。
エラー吐いてないのでjsとして動作するっぽい、まじ？
とりあえずコピペして手元に保存、
```javascript
> node unya.js

$(function () {
  $("form").submit(function () {
    var t = $('input[type="text"]').val();
    var p = Array(70, 152, 195, 284, 475, 612, 791, 896, 810, 850, 737, 1332, 1469, 1120, 1470, 832, 1785, 2196, 1520, 1480, 1449);
    var f = false;
    if (p.length == t.length) {
      f = true;
      for (var i = 0; i < p.length; i++)
        if (t.charCodeAt(i) * (i + 1) != p[i]) f = false;
      if (f) alert("(」・ω・)」うー!(/・ω・)/にゃー!");
    }
    if (!f) alert("No");
    return false;
  });
}); 
``` 
おお、でた。うーにゃーの実態。
あとは`Array(70, 152,...`に対して逆の変換をしてやれば良さそう

### q5
とりあえずbase64エンコード、
```
echo q4 | nkf -d --base64
```
まだ暗号化されてるっぽい、というかタイトルがonionなるほどと思い数回デコード、５、６回？
```python

>>> dec = dec.decode('base64')
>>> dec
'begin 666 <data>\n51DQ!1U]&94QG4#-3:4%797I74$AU\n \nend\n'
```
uuencodeっぽい文字列が出現。ビンゴ

```python
>>> print dec.decode('uu')
FLAG_FeLgP3SiAWezWPHu
```

### q8
リンクがあるので脳死してクリック、表示がやばい
URLみたらpcapって書いてあったのでlocalに落としてwiresharkで表示した

basic is secure?なんでBasic認証してる通信がありそう→http 401発見
200の直前の通信をみると`Ausentication: XXXXX`
wiresharkが勝手にdecodeしてくれているのでタブを開くとフラグ出現




