# Chapter 8: フォントの作り方 - Sketch 編

Glyphsはフォント制作の延長から、Illustratorは既存のアイコン制作の延長からのアプリ選定でした。どちらも非常に良いソフトなのですが、シンボルフォントに限って言えば、帯に短しタスキに長しな部分もあります。この章で紹介するSketchは、Illustrator/Fireworksなどの代替アプリケーションとして注目されています。ベクター画像の編集に特化していること、画像の切り出し機能が非常に優れていることが特徴です。シンボルフォント作成に必要充分な機能を備えているだけでなく、価格・操作性の点でも多くの人に「ちょうどいい」選択肢になるでしょう。

Sketchには、幸いPNGだけでなくSVGで画像を出力する機能が備わっています。そこで基本的な手順としては次のように作業を進めます。

- テンプレートファイルのダウンロード
- Sketchでグリフの作成
- SketchからSVS出力
- FontCustomで変換

制作にあたって便利なテンプレートファイルを、14px用と、16px用の2種用意しました。本章の説明は14px (FontAwesome互換) で進めますが、用途に合わせてどちらかを選んでください。

![テンプレート](../images/sketch-symbol-template.png)

ダウンロードは、GitHubのプロジェクトページから可能です。

(TODO: GitHubのリンク先を掲載)


## グリッドの設定

作業の前に、Chapter 5の「グリッドの設計」を確認しておいてください。ここでは、Font Awesomeに合わせて、独自のグリフを作る想定で説明を進めます。フォントの基準のサイズを14pxとすると、4倍までの4パターンを想定して56px、座標の精度を確保するためにその10倍として、キャンバスサイズを560pxとしました。なお、Sketchではキャンバスのことを「Artboard」と呼びます。

- 14px (x1)
- 28px (x2)
- 42px (x3)
- 56px (x4)

Sketchでテンプレートファイルを開いて、`View > Grid Settings...`メニューを開くと、下記のように設定されているはずです。

- Grid block size: 20px
- Thick lines every: 2 blocks.

つまり、40pxごとにグリッド、その半分で補助グリッドが引かれます。Sketchでは

- 矢印キーによる入力: 1px移動
- Shift + 矢印キーによる入力: 10px移動

となるので、微調整はマウスだけでなくキー入力も併用して、グリッドに揃えていきましょう。

![グリッドの設定](../images/sketch-grid-setting.png)

※注: この章の後半でフォントに変換する際、FontCustom(あるいはgrunt-webfont)を使うと、キャンバスサイズが512pxに縮小されてから処理されます。そのため望ましくはありませんが、14pxグリッドから若干ずれる可能性があります。(基準サイズを16pxとした場合は、512の約数なので問題ありません)


## グリフの作成

テンプレートには、glyph01からglyph32まで32個のアートボードが配置されています。32個あれば、たいていのプロジェクトでは事足りますが、必要に応じて2つ目のファイルを作成してください。Sketchはオブジェクト数が増えると、動作が遅くなりがちです。もし32個でも動作が遅く感じる場合は、アートボードの数を減らすと良いでしょう。

### グリッドにスナップ


### 黒一色で作成


### パスの合成


## SVG出力

### Artboardにグリフ名を付ける

Sketchでは出力されるファイル名は、Artboard名がデフォルトです。もちろん、複数のスライスを設定する場合は、スライスごと個別に設定可能です。


### すべてエクスポート


## Font Custom によるフォント変換

ここでは、コマンドラインのツールとして、[Font Custom]()を紹介します。Font Customは[Font Forge](http://fontforge.org/)

Chapter 11で登場する自動化ツール「Grunt」のプラグインに「grunt-webfont」がありますが、これも内部的にはFont Customを使っています。業務で制作する場合はGruntとの併用するのが望ましいので、この節を飛ばして、Gruntの説明に進むのもOKです。その場合、パラメータなど分からない点があれば、この節にまた戻って来てください。

### Font Custom のインストール


### 変換の設定と実行


### SVGファイルの自動監視

