## エンジニアと働きたい「非エンジニア」勉強会

# jQuery勉強会

### Presented by Kazuki Higashiguchi



## 自己紹介

- @kazukun_gutikun
- 同志社大学経済学部 4回
- テッド2が面白かったことが最近の人生のハイライト
- デルタクロス京都エンジニアなう
- その他、ウェブアプリ製作のプロジェクト参加や母親のウェブサイトヘッダー編集・ハッカソン参加など



## 今日のスケジュール

1. 非エンジニア勉強会って？
1. 今日の最終目標
2. 開発において「プログラマー」っぽくなるツールのインストール
3. ウェブ開発概要講義
1. jQueryの基本知識講義・実践
1. jQuery実践
1. 今後のインフォメーション



##非エンジニア勉強会って？

[冒頭スライド](http://kazuki1994.github.io/non-programmerstudy/#/8)

##今日の最終目標

メンバーのスライドショーをjQueryで作成する<br>
[完成イメージ](http://entos.sakura.ne.jp/home/)
![スライド](https://dl.dropboxusercontent.com/u/79953334/slide_20150903.png)
デルタクロス京都のウェブサイトβ版のスライドショー

##ツールの紹介
###テキストエディタ「sublimeText3」
![sublimeText](https://raw.githubusercontent.com/wiki/oubiwann/vim-blackboard-sublime-theme/images/Sublime-VimBlackboard.png)
[公式サイト](http://www.sublimetext.com/3)<br>
テキストエディタとは、「プログラマー用のメモ帳」
普通のメモ帳と違って、色がついて見やすくなったりコードが見やすいようにレイアウトしやすくしてくれます。<br>
<small>もうすでにテキストエディタをインストール済みの方はスキップしていただいて結構です。</small>

###ブラウザ
今回はgoogle chromeで表示いたします。

##ウェブサイト・サービス開発概要講義

###ウェブサービスやサイトをつくる上で知っとくべき二つの単語
- フロントエンド
- サーバーサイド

###フロントエンド
主に<br>

- HTML
- CSS
- JavaScript

を使って開発する部分のこと<br>
- HTMLとは、ウェブサイト・アプリ内の文章や文章構造を定義する言語
- CSSとは、デザインをする言語（色や形や大きさなど）
- Javascriptとは、動きをつける言語

ウェブサイトを作ろうと思ったら大体これらで事足りることが多い。フロントエンドを作ってサーバーにアップすれば世の中に公開される。

###バックエンド

- サーバサイドプログラミング（サーバーからのデータのやりとりなど）
- サービスのロジック部分
- Java, Perl, PHP, Python, Ruby, 等々

ウェブアプリをつくろうと思ったらバックエンドが不可欠。簡単な例では、掲示板のようなアプリケーションなど。




## 今回学ぶのは

フロントエンド > javascript > jQuery


## jQuery


jQuery とは

- JavaScript を簡潔に書くためのライブラリ
- John Resig 氏が2006年にリリース
- オープンソース（MIT, GPL License）
- "write less, do more."
- 複数のブラウザに対応


#### write less, do more.

例えば red クラスの要素の色を一括で赤にしたいとき

```js
// JavaScript の場合
var redElements = document.getElementsByClassName("red");
for (var i = 0; i < redElements.length; i++) {
  redElements[i].style.color = "red";
}

// jQuery の場合
$(".red").css("color", "red");
```

4行書くのは面倒くさい！それが1行で完結。

#### 複数のブラウザに対応

例えば要素の透明度を設定する場合

```js
// JavaScript の場合 IE 用の記述が必要
document.getElementById('translucent').style.opacity = 0.5;
document.getElementById('translucent').filter = "alpha(opacity = 50)";

// jQuery の場合
$("#translucent").fadeTo(0, 0.5);
```
javascriptでは、IE用とわけないといけないところを一発解決！

### 準備

1. どこにでもいいので index.html, script.js を作成
1. http://learn.jquery.com/about-jquery/how-jquery-works/ にアクセス
1. jQuery: The Basics を貼り付け
1. jQuery のソースを Google CDN から読み込み
 - https://developers.google.com/speed/libraries/#jquery
1. body 終了直前に script.js を読み込み


### 書き方その1. 操作対象を指定する

jQuery(セレクタ)

jQuery は $ と書くことも出来る

$(セレクタ)

```js
$(".red")

$("#translucent")
```


セレクタとは

**「CSS でスタイルを適用する対象を指定する仕組み」**

具体的にはタグ名や ID 名、クラス名など

```js
$("tag")      // タグ
$("#id")      // ID
$(".class")   //クラス
$("a img")    // 子要素
```


### 書き方その2. オブジェクトを操作する

$(セレクタ).メソッド(引数)

```js
$(".red").css("color", "red");

$("#translucent").fadeTo(0, 0.5);
```


メソッド以外にプロパティというものも少数ながらある

$(セレクタ).プロパティ

```js
// div 要素の個数を取得して変数 num に格納する処理
var num = $("div").length;
```


### イベント

- インタラクティブなコンテンツ作りに必要な仕組み
- ユーザの操作や状態の変化など


#### 構文

```js
$(セレクタ).イベント(function (){
  // 処理
});
```


### ready イベント

HTML をロードする前に JavaScript が実行されると

**もちろん JavaScript は正しく動作しません**


そこで、 ready イベントを用いて HTML が読み込まれるのを待ちます

ready イベントの中には必ず関数を記述します

```js
jQuery(document).ready(function hoge() {
  // html 読み込み後にこの部分が実行されます
});

// 省略記法
$(function hoge() {
  // html 読み込み後にこの部分が実行されます
});
```


いちいち関数名を付けるのは面倒な上に管理も大変なので、無名関数を用います

```js
$(function() {
  // html 読み込み後にこの部分が実行されます
});
```


主なイベントは以下のようなものがあります

- .ready()
- .click()
- .hover()
- .keydown()
- .select()
- .scroll()


### 例. クリックイベント

```js
var clicked_props = {
  "color" : "#fff",
  "background" : "#D2527F"
};

$(function() {
  $("button").click(function() {
    $("div").css(clicked_props);
    $("div").text("buttonがクリックされました");
  });
});
```


### メソッドチェイン

- jQuery オブジェクトの生成には負荷がかかる
- 1回の生成で複数の処理ができるようにする

$("セレクタ").メソッド().メソッド().メソッド()...

```js
$(function() {
  $("button").click(function() {
    $("div").css(clicked_props).text("buttonがクリックされました");
  });
});
```

##jQuery実践
####（参考）実際のスライドショー部分のHTML, CSS, Javascriptファイル一覧
実際は、最初からゴリゴリ作成するのではなく、[OWL Carousel](http://owlgraphic.com/owlcarousel/#demo)というjQueryプラグインを使用してスライドショーを実装しています。
![owl](https://dl.dropboxusercontent.com/u/79953334/owl_img.png)
index.html

```
<div id="tf-team" class="text-center">
        <div class="overlay">
            <div class="container">
                <div class="section-title center">
                    <h2>Meet <strong>our team</strong></h2>
                    <div class="line">
                        <hr>
                    </div>
                </div>

                <div id="team" class="owl-carousel owl-theme row">
                    <div class="item">
                        <div class="thumbnail">
                            <img src="img/team/01.jpg" alt="..." class="img-circle team-img">
                            <div class="caption">
                                <h3>Naoto Ando</h3>
                                <p>Executive / Founder</p>
                                <p>立命館大学 好きな動物は猫</p>
                            </div>
                        </div>
                    </div>

                    <div class="item">
                        <div class="thumbnail">
                            <img src="img/team/02.jpg" alt="..." class="img-circle team-img">
                            <div class="caption">
                                <h3>Daimu Nakamura</h3>
                                <p>Financial / Founder</p>
                                <p>京都府立医科大学大学院　学会の日々</p>
                            </div>
                        </div>
                    </div>

                    <div class="item">
                        <div class="thumbnail">
                            <img src="img/team/03.jpg" alt="..." class="img-circle team-img">
                            <div class="caption">
                                <h3>Kazuki Higashiguchi</h3>
                                <p>Technological / Founder</p>
                                <p>同志社大学　AngularJSが最近のはやり</p>
                            </div>
                        </div>
                    </div>

                    <div class="item">
                        <div class="thumbnail">
                            <img src="img/team/04.jpg" alt="..." class="img-circle team-img">
                            <div class="caption">
                                <h3>Kakeru Maruo</h3>
                                <p>Operation</p>
                                <p>大阪府立大学　「関西で一番の一回生になる」</p>
                            </div>
                        </div>
                    </div>

                    <div class="item">
                        <div class="thumbnail">
                            <img src="img/team/05.jpg" alt="..." class="img-circle team-img">
                            <div class="caption">
                                <h3>Kaori Nishikawa</h3>
                                <p>Design</p>
                                <p>京都精華大学　あだ名はジュデイ</p>
             		    </div>
                   </div>
            </div>
      </div>       
    </div>
</div>
```

style.css

```
/* Team Section */
#tf-team{
	background: url(../img/03.jpg);
	background-size: cover;
	background-position: center;
	background-attachment: fixed;
	background-repeat: no-repeat;
	color: #ffffff;
}
#tf-team .overlay{
	background: -moz-linear-gradient(top,  rgba(0,0,0,0.8) 0%, rgba(0,0,0,0.73) 17%, rgba(0,0,0,0.66) 35%, rgba(0,0,0,0.55) 62%, rgba(0,0,0,0.4) 100%); /* FF3.6+ */
	background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,rgba(0,0,0,0.8)), color-stop(17%,rgba(0,0,0,0.73)), color-stop(35%,rgba(0,0,0,0.66)), color-stop(62%,rgba(0,0,0,0.55)), color-stop(100%,rgba(0,0,0,0.4))); /* Chrome,Safari4+ */
	background: -webkit-linear-gradient(top,  rgba(0,0,0,0.8) 0%,rgba(0,0,0,0.73) 17%,rgba(0,0,0,0.66) 35%,rgba(0,0,0,0.55) 62%,rgba(0,0,0,0.4) 100%); /* Chrome10+,Safari5.1+ */
	background: -o-linear-gradient(top,  rgba(0,0,0,0.8) 0%,rgba(0,0,0,0.73) 17%,rgba(0,0,0,0.66) 35%,rgba(0,0,0,0.55) 62%,rgba(0,0,0,0.4) 100%); /* Opera 11.10+ */
	background: -ms-linear-gradient(top,  rgba(0,0,0,0.8) 0%,rgba(0,0,0,0.73) 17%,rgba(0,0,0,0.66) 35%,rgba(0,0,0,0.55) 62%,rgba(0,0,0,0.4) 100%); /* IE10+ */
	background: linear-gradient(to bottom,  rgba(0,0,0,0.8) 0%,rgba(0,0,0,0.73) 17%,rgba(0,0,0,0.66) 35%,rgba(0,0,0,0.55) 62%,rgba(0,0,0,0.4) 100%); /* W3C */
	filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#cc000000', endColorstr='#66000000',GradientType=0 ); /* IE6-9 */
	height: auto;
	background-attachment: fixed;
	padding: 80px 0;
}
.section-title.center{
	padding: 30px 0;
}
.section-title h2,
.section-title.center h2{
	font-weight: 300;
}
.section-title.center .line{
	border-top: 4px solid #fcac45;
	height: 10px;
	width: 60px;
	text-align: center;
	margin: 0 auto;
	margin-top: 20px;
}

.section-title.center hr {
	border-top: 4px solid rgba(252, 172, 69, 0.34);
	width: 40px;
	text-align: center;
	margin-top: 10px;
	position: relative;
	left: 17%;
}
#team{ margin: 0 auto}
#team .item{
    padding: 0;
    margin: 15px;
    color: #FFF;
    text-align: center;
}

img.img-circle.team-img {
	width: 120px;
	height: 120px;
	border: 4px solid transparent;
	transition: all 0.5s;
}
#tf-team .item .thumbnail:hover>img.img-circle.team-img{
	border: 4px solid #FCAC45;
}
#tf-team .thumbnail {
	background: transparent;
	border: 0;
}

#tf-team .thumbnail .caption {
	padding: 9px;
	color: #F2F2F2;
}

.owl-theme .owl-controls .owl-page span {
	display: block;
	width: 10px;
	height: 10px;
	margin: 5px 7px;
	filter: Alpha(Opacity=1);
	opacity: 1;
	-webkit-border-radius: 0;
	-moz-border-radius: 20px;
	border-radius: 0;
	background: #FFFFFF;
	transition: all 0.5s;
}

.owl-theme .owl-controls .owl-page.active span, 
.owl-theme .owl-controls.clickable .owl-page:hover span {
	filter: Alpha(Opacity=100);
	opacity: 1;
	background: #FCAC45;
}
.owl-theme .owl-controls .owl-page.active span{
	background: #FCAC45;
}

/* Services Section */
#tf-services{
	padding: 80px 0;
}

.space{
	margin-top: 40px;
}

#tf-services i.fa {
	font-size: 40px;
	border: 4px solid #FCAC45;
	width: 100px;
	height: 100px;
	padding: 27px 25px;
	margin-bottom: 10px;
	border-radius: 50%;
	transition: all 0.5s;
}

#tf-services i.fa.fa-mobile{
	font-size: 50px;
	padding: 20px 25px;
}

#tf-services .service:hover>i.fa{
	background: #FCAC45;
	color: #ffffff;
}
```
main.js

```
$(document).ready(function() {
  	  $("#team").owlCarousel({
  	 
  	      navigation : false, // Show next and prev buttons
  	      slideSpeed : 300,
  	      paginationSpeed : 400,
  	      autoHeight : true,
  	      itemsCustom : [
				        [0, 1],
				        [450, 2],
				        [600, 2],
				        [700, 2],
				        [1000, 4],
				        [1200, 4],
				        [1400, 4],
				        [1600, 4]
				      ],
  	  });
```


##参考資料
###[DITプログラミング勉強会資料](https://gist.github.com/Tamrin007/4e68fc175c3041a4eff2)
Tamrinさんのご好意より一部参照させていただきました。

###[文系でも知ってもおきたいプログラミングとプログラマーのこと　清水亮](http://www.amazon.co.jp/%E6%96%87%E7%B3%BB%E3%81%A7%E3%82%82%E7%9F%A5%E3%81%A3%E3%81%A6%E3%81%8A%E3%81%8D%E3%81%9F%E3%81%84%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%9F%E3%83%B3%E3%82%B0%E3%81%A8%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%9E%E3%83%BC%E3%81%AE%E3%81%93%E3%81%A8-%E6%B8%85%E6%B0%B4-%E4%BA%AE/dp/4478063141)

###[ドットインストール「jQuery入門」](http://dotinstall.com/lessons/basic_jquery_v2)
# 以上、ありがとうございました
