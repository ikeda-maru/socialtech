# jQueryを導入して動きのあるWebサイトを作る

## ボタンにアニメーションを付ける

- `a`タグで囲った`img`タグにクラス名をつける
- クラス名を付けた`img`タグを対象に`js`ファイルで動きを設定する
- 

`mouseover`したときの動きを設定する書き方
```
$(function() {
  $('対象のクラス名').on('mouseover', function() {
    $(this).animate({
      cssの内容を設定
      例
      opacity: 0.5,
      marginLeft: 20, // 左にmarginが入るので、右に動く
    }, 変化にかける時間);
  });
  // 続けてマウスアウトしたときの動きも指定する(これがないと、一度動いて元に戻らないので)
  $('対象のクラス名').on('mouseout', function() {
    $(this).animate({
      $(this).animate({
        例
        opacity: 1.0,
        marginLeft: 0, //上記で左に挿入したmarginを解除して元の位置に戻す
      }, 変化にかける時間);
    });
  });
```

## カルーセルの設定

以下、プラグイン(slick)を使って実装する方法。
slickとは、jQueryのプラグインの1つ。

### slickの読み込み

slickを使用する際は、jQuery本体と同様、CDNで読み込みをする。
CDNで読み込む際はslickの[公式サイト](https://kenwheeler.github.io/slick/)または[slickのGitHubページ](https://github.com/kenwheeler/slick/#cdn)に記載されているURLを記述する。

### slickでカルーセルを作成

1. CSSのセレクタを使ってどのHTML要素をカルーセル化するか設定
2. `slick({...})`の中にカルーセルの設定内容を記述する

書き方
```
$('セレクタ').slick({
  設定項目: 設定値,
  設定項目: 設定値,
  ...
});
```

代表的な設定項目
- `autoplay`: 画像を自動的に切り替えるかどうか
- `autoplaySpeed`: 次の画像に切り替えるまでの待ち時間
- `arrows`: 画像を手動で切り替えるための矢印ボタンを表示するかどうか
- `dots`: 「現在何枚目の画像を表示しているか」を示すUI(ドット)を表示するかどうか
- `fade`: 画像の切替時にフェード(徐々に透明/不透明になるアニメーション)させるかどうか
- `infinite`: 画像をループさせるかどうか
- `speed`: 画像の切替時のアニメーション速度
- `swipe`: スワイプ操作による画像の切り替えを有効にするかどうか

