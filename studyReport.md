# 実践！ウェブサイトを作ろう
ドットインストール「[実践！ウェブサイトを作ろう](https://dotinstall.com/lessons/website_html_v3)」の学習記録

## 進め方
サイトの制作を一通りこなし、学習する。  
一度学習したことが多くなるかと思うので、新出のテクニックだけまとめ、  
以下で完成したものが見られるようにする。  
https://oratake.github.io/dotinstall_making_website/  

以下は記述したhtmlとcss  
https://github.com/oratake/dotinstall_making_website/blob/master/index.html  
https://github.com/oratake/dotinstall_making_website/blob/master/css/styles.css  

また、なるべく弊社での書き方で書くようにした。  

## 曖昧だったところまとめ
### 模擬要素・模擬クラス
とりあえずCSSの後につくもので同じもの、程度の認識だったものの、  
ちゃんと違いがあった。  
- 模擬要素  
  **要素内の一部** に対してスタイルを適用する。  
  CSS3では以下がある  
  `::before`,`::after`,`::first-letter`,`::first-line`  
  コロンが二重になっているのは、CSS3になったときに模擬要素、模擬クラスを明確に区別するためとのこと。
- 模擬クラス
  **要素内全体** に対してスタイルを適用する。  
  かなり数は多い。`:hover`,`:nth-child()`などもそう。

参考：[【CSS】擬似要素と擬似クラスの違いの覚書 | niwaka-web](https://niwaka-web.com/css_pseudo_different/)

## 使われていたテクニックなど
### favicon
`<link rel="icon" href="./favicon.ico">`  
htmlにはfaviconを指定する事ができる。  
faviconはタブやウィンドウにtitleとともに載ったり、ブックマーク時に一緒に保存されたりする。  

iOSとAndroid(chormeのみ)で使われるapple-touch-icon.pngというものもある。  
これは、ブックマークをホーム画面に配置した際にアイコンになる。  

### 画像の絶対配置(position:)
親要素に対して`position: relative;`をあて、  
絶対配置したい画像に`position: absolute;`をあてつつ、  
`top:`,`right:`,`bottom:`,`left:`などで位置を調整。  
```html
<div class="container">
  <img src="./path/of/image.png" alt="なにかしらの画像">
</div><!-- /container -->
```
```css
.container { position: relative; }
.container img {
  position: absolute;
  top: 0;
  right: 0;
}
```

### Font Awesome
web上でfreeで使えるアイコン群がある。(ex. [Font Awesome](https://fontawesome.com/))  
1. 公式からhead内に入れるlinkをもらってくる
ex) `<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.5.0/css/all.css" integrity="省略" crossorigin="anonymous">`
2. 使いたいアイコンを探して、ページ内から`<i>`から始まるタグをコピーしてくる。  
ex) `<i class="fas fa-external-link-alt"></i>`
3. 貼り付けて使う。  

### cssの整理
コメントで`/* header */`などと入れておき、場所が限定されるスタイルは何がどこにあるかわかりやすいようにする。

### 模擬要素でサブタイトルをつくる
模擬要素を用いて付帯するデザインをつくる方法  
```html
<h1 data-subtitle="- Features -">Dotinstall Paneの特徴</h1>
```
```css
h1 { /* ヘッダ内に適用 */ }
h1::after { /* h1の直後に */
  content: attr(data-subtitle); /* attrで属性の値を読み込む */
  display: block; /* ブロック要素にしておく */
  /* その他、サブタイトルのデザイン */
}
```

### 模擬クラスを使ったスタイリング
**○ 画像を並べるとき、左右交互に振りたい**
`div.img*3>img`のとき  
```css
.img:nth-of-type(odd) { float: left; }
.img:nth-of-type(even) { float: right; }
```
odd(奇数)は左、even(偶数)は右などできる。  
`:nth-of-type()`の()内には(an+b)の形で数式を当てはめることも可能。  

### flexboxでの位置合わせ
3枚のカードを横並べにする場合  
`div.flex>div.card*3`のとき  
```css
.flex {
  display: flex; /* flex要素として指定 */
  justify-content: space-between;
}
```

---
以下作成したページ  
https://oratake.github.io/dotinstall_making_website/

記述したhtml, css  
https://github.com/oratake/dotinstall_making_website/blob/master/index.html  
https://github.com/oratake/dotinstall_making_website/blob/master/css/styles.css
