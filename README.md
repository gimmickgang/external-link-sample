# ニコニコ大百科の外部リンク案
ニコニコ大百科の外部リンクに掲出する外部リンクアイコンの実装案
![すくしょ](https://github.com/gimmickgang/external-link-sample/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-02-04%20024933.png)


負荷軽減のため、記事の過去リビジョンでの自動リンク付与の停止に伴い、過去リビジョンでの外部リンクアイコンの掲出が不可能になっている件について、ニコニコ大百科側の負担をなくした形での外部リンクアイコンの付与に関する提言


- 外部リンクアイコンの掲出を現状のリンクに関するプログラム部分より完全にマージして、CSSによる掲出に切り替える
- PC版、スマホ版の以下のCSS内にこのCSSを追加
  - nicopedia_style.css
  - nicopedia_style_sp.css

![すくしょ](https://github.com/gimmickgang/external-link-sample/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-02-04%20024958.png)

## 問題点
スマホ版では記事がspan class="article"内、掲示板レスがul class="sw-Article_List"内、PC版ではdiv class="st-bbs-contents"内のdlに内包されているため、記事本文・掲示板レスのそれぞれ当該部分に限った運用が行えるが、<br>PC版本文の領域はdiv class="article" id="article"内にて、記事下方の【スポンサーリンク】やdiv class="a-list_articleInfo"の初版作成日などの領域と同居している兄弟要素となるため、現状では単体での指定が困難であり、指定せずに適用しようとするとタグ検索リンク部分などにアイコンが表示される。<br>これを回避するには本文領域をdivなどで内包しその領域に限った指定をするのが良いと思われる。
![すくしょ](https://github.com/gimmickgang/external-link-sample/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-02-04%20030038.png)
