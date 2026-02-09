# ニコニコ大百科の外部リンク案
ニコニコ大百科の外部リンクに掲出する外部リンクアイコンの実装案
![すくしょ](https://github.com/gimmickgang/external-link-sample/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-02-04%20024933.png)


負荷軽減のため、記事の過去リビジョンでの自動リンク付与の停止に伴い、過去リビジョンでの外部リンクアイコンの掲出が不可能になっている件について、ニコニコ大百科側の負担をなくした形での外部リンクアイコンの付与に関する提言


- 外部リンクアイコンの掲出を現状のリンクに関するプログラム部分より完全にマージして、CSSによる掲出に切り替える
- PC版、スマホ版の以下のCSS内にこのCSS　[external link.css](https://github.com/gimmickgang/external-link-sample/blob/main/external%20link.css)を追加
  - nicopedia_style.css
  - nicopedia_style_sp.css

![すくしょ](https://github.com/gimmickgang/external-link-sample/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-02-04%20024958.png)

## CSSでのアイコン掲出について
CSSファイル　[external link.css](https://github.com/gimmickgang/external-link-sample/blob/main/external%20link.css)　にあるように`<a>`タグの属性セレクター`[attr^=value]`を利用して外部リンクとなる項目のみに`::after`疑似要素のcontentを用いてリンクアイコンを掲出する。    
デフォルト指定の`http`から始まるリンク以外の場合は、静画への指定箇所のように`[attr*=value]`での『文字列中に value を1つ以上含む要素』の指定でもよい。

### 各アイコンの掲出ルールについて
現状の外部アイコンの掲出ルールに準じる。
- ![ext.webp](https://github.com/gimmickgang/external-link-sample/blob/main/img/ext.webp)　デフォルト外部リンクアイコン　下記ニコニコ内サービス以外の全ての外部リンクに掲出　`http`から始まるリンクに掲出
  - `http`からの指定により、自動リンクなどの相対パスでの指定されたリンクを除外する。
- ![ext_nico.webp](https://github.com/gimmickgang/external-link-sample/blob/main/img/ext_nico.webp)　ニコニコ動画リンクアイコン　動画視聴ページなど、`www.nicovideo.jp`から始まるリンクに掲出
- ![ext_list.webp](https://github.com/gimmickgang/external-link-sample/blob/main/img/ext_list.webp)　マイリストリンクアイコン　`www.nicovideo.jp/mylist/`から始まるリンクに掲出
- ![ext_nl.webp](https://github.com/gimmickgang/external-link-sample/blob/main/img/ext_nl.webp)　ニコニコ生放送リンクアイコン　`live.nicovideo.jp`から始まるリンクに掲出
- ![ext_ch.webp](https://github.com/gimmickgang/external-link-sample/blob/main/img/ext_ch.webp)　ニコニコチャンネルリンクアイコン　`ch.nicovideo.jp`から始まるリンクに掲出
- ![ext_commons.webp](https://github.com/gimmickgang/external-link-sample/blob/main/img/ext_commons.webp)　ニコニコモンズリンクアイコン　`commons.nicovideo.jp`から始まるリンクに掲出
- ![ext_news.webp](https://github.com/gimmickgang/external-link-sample/blob/main/img/ext_news.webp)　ニコニコチャンネルリンクアイコン　`news.nicovideo.jp`から始まるリンクに掲出
- ~~![ext_sg.png](https://github.com/gimmickgang/external-link-sample/blob/main/img/ext_sg.png)　ニコニコ静画リンクアイコン　`seiga.nicovideo.jp`から始まるリンクに掲出~~静画リンクアイコンについては後述
- （記事本文内）記事編集者ユーザーによる`<a>`タグへの外部アイコン非表示の指定`style="background-image: none;"`が存在する場合は、現状でも外部リンクアイコンの掲出を行わない仕様なので、それに準じて非表示とする。
- `dic.nicovideo.jp`から始まるリンクを除外することにより、ユーザーの編集での絶対パスによるリンク指定、および掲示板での`http`から始まる文字列に対するリンク付与時のニコニコ大百科内へのリンク時に外部リンクアイコンが生成されるのを除外する。

#### ニコニコ静画への外部アイコン掲出について
- 2019年6月11日付けの改修において、『ニコニコ静画引用時のアイコンを
表示しないように仕様を変更』（[リンク](https://ch.nicovideo.jp/nico-nico-pedia/blomaga/ar1774296)）しているが、この際に静画の引用時だけではなく静画へのリンク自体へのリンクアイコンの掲出がなくなっているため
  - 静画へのリンク単独の場合は掲出する（※単語記事『ニコニコ静画』の静画へのリンク箇所など）
  - 静画引用時は掲出しない（※各記事で静画引用を行っている箇所）

のルールにてリンクアイコンを掲出する（対応するwebp画像、png画像がないためサンプルでは、アイコンお絵カキコ画像にて代用）

## 表示サンプルページ
- [サンプルページ(https://gimmickgang.github.io/external-link-sample/)](https://gimmickgang.github.io/external-link-sample/)
  - 当サンプルページは、exclude階下の`displaynone.css`と同様に`<img>`タグでの外部リンクアイコンの掲出を`display: none;`にて非表示化したものに    
  `::after`疑似要素にてアイコン掲出を行っている。
  - 追加スタイルシートは、外部CSSではなく`<style>`タグで追加している。


## 問題点
スマホ版では記事が`span class="article"`内、掲示板レスが`ul class="sw-Article_List"`内、PC版では`div class="st-bbs-contents"`内のdlに内包されているため、記事本文・掲示板レスのそれぞれ当該部分に限った運用が行えるが、<br>PC版本文の領域は`div class="article" id="article"`内にて、記事下方の【スポンサーリンク】や`div class="a-list_articleInfo"`の初版作成日などの領域と同居している兄弟要素となるため、現状では単体での指定が困難であり、指定せずに適用しようとするとタグ検索リンク部分などにアイコンが表示される。<br>これを回避するには本文領域をdivなどで内包しその領域に限った指定をするのが良いと思われる。
![すくしょ](https://github.com/gimmickgang/external-link-sample/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202026-02-04%20030038.png)

- 詳細については[exclude](https://github.com/gimmickgang/external-link-sample/tree/main/exclude)階下のREADME.mdにて解説。サンプルのCSSも同階層に格納。
