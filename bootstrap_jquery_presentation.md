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



##参考資料
###[DITプログラミング勉強会資料](https://gist.github.com/Tamrin007/4e68fc175c3041a4eff2)
Tamrinさんのご好意より一部参照させていただきました！あざす！

# 以上、ありがとうございました
