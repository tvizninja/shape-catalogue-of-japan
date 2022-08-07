# Shape catalogue of Japan

## What is This

* データ可視化の分野で日本列島を表現する場合、単純化された地図を示す場合がある。
* そうした表現には様々な型があり、それぞれに長所短所がある。それらをまとめることで、適切な型を選択できるようにしたい。
* 有用そうなやつは、HTMLやSVGのテンプレートを用意するなどしていきたい。
* 用例採集情報の提供や、プルリクエストは大歓迎です。

## テクニックetc

* 沖縄は九州と近づけるか隣り合わせ。北海道は石川県沖や秋田県沖に配置し、全体をコンパクトに。
* 面積比を保つと、東京が小さすぎて選びづらい
* 海に面さない内陸県は次の8県
  * 奈良、滋賀、岐阜、長野、山梨、埼玉、群馬、栃木
* Gridに詰め込む場合海がある県を内陸に配置せざるを得ない。京都、富山、東京などは海への接続が相対的に小さい点、考慮可能か。
* [JIS X 0401](https://nlftp.mlit.go.jp/ksj/gml/codelist/PrefCd.html)の並びを意識すると良い場合も

## Catalogue

### Grid Type

* 1県1マスとすると、ぱっと見日本列島であるという認識がしづらいため、北海道を2マスで表現するケースも
* 九州、四国、本州、北海道の間の海を表現するために、グリッド間隔が調整されているケースもある
* [グリッド座標からSVGを生成するSnnipetsを書いた](https://codepen.io/tvizninja/pen/rNdVjGG) -> csv2grid.html

#### Grid 4x12

* とにかくコンパクトにする目的で 4 x 12 のグリッドで表現してみた。
* 北海道を下に詰め、空いたマスに「総数」や「BackHomeボタン」を表現することも可能
* 東日本が(普段よく見る地図に比べ)斜めになったり配置が歪むため、探しづらいか

<img src="https://raw.githubusercontent.com/tvizninja/shape-catalogue-of-japan/main/svg/grid-4x12.svg" width="400" height="200">

#### Grid 7x7

* 左上2マスに全国(総数)を割り当てetc
  * <https://www.stopcovid19.jp/>

<img src="https://raw.githubusercontent.com/tvizninja/shape-catalogue-of-japan/main/svg/grid-7x7.svg" width="400" height="400">

#### Grid 8x10

* case
  * <https://www.yomiuri.co.jp/election/sangiin/2022/kouho/>

<img src="https://raw.githubusercontent.com/tvizninja/shape-catalogue-of-japan/main/svg/grid-8x10.svg" width="400" height="400">

#### Grid 8x12

* case
  * <https://sangiin.go2senkyo.com/2022/>

<img src="https://raw.githubusercontent.com/tvizninja/shape-catalogue-of-japan/main/svg/grid-8x12.svg" width="400" height="400">

#### Grid 9x10

* case
  * <https://townnote.net/000_5.html>

<img src="https://raw.githubusercontent.com/tvizninja/shape-catalogue-of-japan/main/svg/grid-9x10.svg" width="400" height="400">

#### Grid 10x13

* case
  * <https://loom.jp/kmap/price.html>

<img src="https://raw.githubusercontent.com/tvizninja/shape-catalogue-of-japan/main/svg/grid-10x13.svg" width="400" height="400">

<img src="https://raw.githubusercontent.com/tvizninja/shape-catalogue-of-japan/main/svg/grid-10x13c.svg" width="400" height="400">

#### Grid 17x13

<img src="https://raw.githubusercontent.com/tvizninja/shape-catalogue-of-japan/main/svg/grid-17x13.svg" width="400" height="400">

* <https://twitter.com/Yokohama_Geo/status/1547159498074501121>を参考にした
* 縦は半グリッドあると表現力が増す気がする。横は半グリッドなくてもなんとかなりそう。

### Rectangle Type

#### 地図に寄せたタイプ

* 地図によせつつ、人口密度が高いエリアは大きめに
  * <https://vdata.nikkei.com/election/2022/sanin/kaihyo/>
  * <https://www.data.go.jp/list-of-database/local-government>
  * <https://www.nhk.or.jp/senkyo/database/sangiin/#ancSenkyokuSeatsMap>
  * <https://www3.nhk.or.jp/news/special/coronavirus/data/>

### Hex Type

* 日本の地図でHexはあまり見たことないかも？
* アメリカの場合、かなりいい感じのがあり、参考にしたい。
  * <https://blog.apps.npr.org/2015/05/11/hex-tile-maps.html>

* FlatTopとPointyTopの2種類で、1マス/都道府県で作ってみた。

<img src="https://raw.githubusercontent.com/tvizninja/shape-catalogue-of-japan/main/svg/hex-flattop.svg" width="400" height="400">

<img src="https://raw.githubusercontent.com/tvizninja/shape-catalogue-of-japan/main/svg/hex-pointytop.svg" width="400" height="400">

* 多マス/都道府県として、実際の地図形状のシンプル化として使う方がよさそうか。

* Hex Gridの考え方について参考になる記事
  * <https://www.redblobgames.com/grids/hexagons/>

### List Type

* 表現する情報に西高東低などの地理的な関連があれば簡略化された地図を使うのも良いが、そうでなければ単純なリスト形式が一番視認性と選択性が高いのかもしれない
* case
  * <https://www.asahi.com/senkyo/saninsen/2022/koho/>

```
北海道・東北: 北海道 青森 岩手 宮城 秋田 山形 福島
関東　　　　: 茨城 栃木 群馬 埼玉 千葉 東京 神奈川
北陸・甲信越: 新潟 富山 石川 福井 山梨 長野
東海　　　　: 岐阜 静岡 愛知 三重
近畿　　　　: 滋賀 京都 大阪 兵庫 奈良 和歌山
中国・四国　: 島根 岡山 鳥取 広島 山口 徳島 香川 高知 愛媛
九州・沖縄　: 福岡 佐賀 長崎 熊本 大分 宮崎 鹿児島 沖縄
```