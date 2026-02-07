## PC版本文領域の下部メニュー部分を除外する

- PC版下部のメニューや『記事と一緒に動画もおすすめ！』などの部分を現在の構造のままで除外するには  
:not()擬似クラスを用いて個別に当該箇所の除外指定をするしかなく
  > .article a:not(.a-banner_space-bottom a, .a-nicoad_supporter a, .a-bottomMenu a, .a-list_articleInfo a, .st-box_contents a, .a-relatedContents a, .a-infoArea_buttons a)[href^="http"]::after    

  と…それぞれの要素の階下のaタグを除外指定しなければならない。
  - メンテナンス性が著しく劣るため、また以降の機能追加や表示項目の追加などの際に、逐一除外指定を追加しなければならなくなるため    
現在の構造のままで除外指定しておく　というのは妥当ではないと思われる。

- このフォルダ階下の[eternal.css](https://github.com/gimmickgang/external-link-sample/blob/main/exclude/eternal.css)
  - :not()を用いて下部メニュー部分の除外
  - PC版/スマホ版掲示板レス部分・スマホ版本文領域部分をそれぞれ指定したサンプル
- このフォルダ階下の[displaynone.css](https://github.com/gimmickgang/external-link-sample/blob/main/exclude/displaynone.css)
  - 上記に加えて現行のimgタグ追加での外部リンクアイコンの掲出をCSSのdisplay noneにて非表示にしたサンプル
