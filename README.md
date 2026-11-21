# カスタマバーコードフォント

日本郵便の仕様に基づくカスタマバーコード用TrueTypeフォントです。郵便番号と町域名以降の住所を入力すると、印字用文字列とバーコードをブラウザで確認できます。

**[カスタマバーコード検証デモを開く](https://tsurumakishunta.github.io/jp-customer-barcode-font/)**

## ファイル

| ファイル | 内容 |
| --- | --- |
| [JPCustomerBarcode.ttf](JPCustomerBarcode.ttf) | バーコード印字用フォント |
| [index.html](index.html) | 印字用文字列の生成とバーコードのプレビュー |
| [BarcodeGlyphs.html](BarcodeGlyphs.html) | 入力文字とバーの対応表 |

## ブラウザで試す

[公開デモ](https://tsurumakishunta.github.io/jp-customer-barcode-font/) を開くと、その場で印字用文字列の生成とフォントによるバーコード表示を試せます。

ファイルを手元で開く場合は、以下の手順でお試しください。

1. リポジトリの **Code → Download ZIP** からダウンロードして展開します。
2. `index.html` をブラウザで開き、郵便番号と、町域名以降の住所を入力します。
3. **生成**を押すと、印字用文字列とバーコードが表示されます。**コピー**で印字用文字列を取得できます。

例として、郵便番号 `100-0013` と、町域名以降の住所 `1丁目3番2号 郵便プラザ503室` を入力すると、`<10000131-3-2-503dddd9>` が表示されます。入力した住所はブラウザ内で処理します。

## 帳票で使う

`JPCustomerBarcode.ttf` をインストールし、生成された文字列に **JP Customer Barcode Regular** を指定します。基準サイズは **10 pt** です。印刷時は倍率を100%にし、上下左右に2 mm以上の余白を確保してください。実際の帳票とプリンターで読み取りをご確認ください。

## カスタマバーコードの体系について

このフォントは、印字用文字列を、上下の伸び方が異なる4種類のバーで描画します。数字・ハイフン・制御コードは各3本、スタートとストップは各2本です。

表の「フォントに渡す半角文字」には、このフォント固有の割り当てを示しています。たとえば日本郵便の仕様でいうCC1は半角小文字の a、CC4は半角小文字の d を指定します。下の見本は、同梱のTrueTypeフォントを実際に描画した画像です。

### 数字・制御コード・開始・終了

| キャラクタ | フォントに渡す半角文字 | バーの形 | チェックデジット計算値 |
| --- | --- | --- | ---: |
| 0 | `0` | <img src="barcode-glyphs/digit-0.png" height="38" alt="digit-0"> | 0 |
| 1 | `1` | <img src="barcode-glyphs/digit-1.png" height="38" alt="digit-1"> | 1 |
| 2 | `2` | <img src="barcode-glyphs/digit-2.png" height="38" alt="digit-2"> | 2 |
| 3 | `3` | <img src="barcode-glyphs/digit-3.png" height="38" alt="digit-3"> | 3 |
| 4 | `4` | <img src="barcode-glyphs/digit-4.png" height="38" alt="digit-4"> | 4 |
| 5 | `5` | <img src="barcode-glyphs/digit-5.png" height="38" alt="digit-5"> | 5 |
| 6 | `6` | <img src="barcode-glyphs/digit-6.png" height="38" alt="digit-6"> | 6 |
| 7 | `7` | <img src="barcode-glyphs/digit-7.png" height="38" alt="digit-7"> | 7 |
| 8 | `8` | <img src="barcode-glyphs/digit-8.png" height="38" alt="digit-8"> | 8 |
| 9 | `9` | <img src="barcode-glyphs/digit-9.png" height="38" alt="digit-9"> | 9 |
| ハイフン | `-` | <img src="barcode-glyphs/hyphen.png" height="38" alt="hyphen"> | 10 |
| CC1 | `a` | <img src="barcode-glyphs/cc1.png" height="38" alt="cc1"> | 11 |
| CC2 | `b` | <img src="barcode-glyphs/cc2.png" height="38" alt="cc2"> | 12 |
| CC3 | `c` | <img src="barcode-glyphs/cc3.png" height="38" alt="cc3"> | 13 |
| CC4 | `d` | <img src="barcode-glyphs/cc4.png" height="38" alt="cc4"> | 14 |
| CC5 | `e` | <img src="barcode-glyphs/cc5.png" height="38" alt="cc5"> | 15 |
| CC6 | `f` | <img src="barcode-glyphs/cc6.png" height="38" alt="cc6"> | 16 |
| CC7 | `g` | <img src="barcode-glyphs/cc7.png" height="38" alt="cc7"> | 17 |
| CC8 | `h` | <img src="barcode-glyphs/cc8.png" height="38" alt="cc8"> | 18 |
| スタート | `<` | <img src="barcode-glyphs/start.png" height="38" alt="start"> | — |
| ストップ | `>` | <img src="barcode-glyphs/stop.png" height="38" alt="stop"> | — |
| スタート（別入力） | `(` | <img src="barcode-glyphs/start-parenthesis.png" height="38" alt="start-parenthesis"> | — |
| ストップ（別入力） | `)` | <img src="barcode-glyphs/stop-parenthesis.png" height="38" alt="stop-parenthesis"> | — |

### 住所に含まれる英字

大文字1文字は、制御コードと数字の2コード分を描画します。たとえば大文字の D は a3、小文字の d はCC4です。

| 英字 | 同じ形になる入力 | バーの形 |
| --- | --- | --- |
| A | a0 | <img src="barcode-glyphs/letter-A.png" height="38" alt="letter-A"> |
| B | a1 | <img src="barcode-glyphs/letter-B.png" height="38" alt="letter-B"> |
| C | a2 | <img src="barcode-glyphs/letter-C.png" height="38" alt="letter-C"> |
| D | a3 | <img src="barcode-glyphs/letter-D.png" height="38" alt="letter-D"> |
| E | a4 | <img src="barcode-glyphs/letter-E.png" height="38" alt="letter-E"> |
| F | a5 | <img src="barcode-glyphs/letter-F.png" height="38" alt="letter-F"> |
| G | a6 | <img src="barcode-glyphs/letter-G.png" height="38" alt="letter-G"> |
| H | a7 | <img src="barcode-glyphs/letter-H.png" height="38" alt="letter-H"> |
| I | a8 | <img src="barcode-glyphs/letter-I.png" height="38" alt="letter-I"> |
| J | a9 | <img src="barcode-glyphs/letter-J.png" height="38" alt="letter-J"> |
| K | b0 | <img src="barcode-glyphs/letter-K.png" height="38" alt="letter-K"> |
| L | b1 | <img src="barcode-glyphs/letter-L.png" height="38" alt="letter-L"> |
| M | b2 | <img src="barcode-glyphs/letter-M.png" height="38" alt="letter-M"> |
| N | b3 | <img src="barcode-glyphs/letter-N.png" height="38" alt="letter-N"> |
| O | b4 | <img src="barcode-glyphs/letter-O.png" height="38" alt="letter-O"> |
| P | b5 | <img src="barcode-glyphs/letter-P.png" height="38" alt="letter-P"> |
| Q | b6 | <img src="barcode-glyphs/letter-Q.png" height="38" alt="letter-Q"> |
| R | b7 | <img src="barcode-glyphs/letter-R.png" height="38" alt="letter-R"> |
| S | b8 | <img src="barcode-glyphs/letter-S.png" height="38" alt="letter-S"> |
| T | b9 | <img src="barcode-glyphs/letter-T.png" height="38" alt="letter-T"> |
| U | c0 | <img src="barcode-glyphs/letter-U.png" height="38" alt="letter-U"> |
| V | c1 | <img src="barcode-glyphs/letter-V.png" height="38" alt="letter-V"> |
| W | c2 | <img src="barcode-glyphs/letter-W.png" height="38" alt="letter-W"> |
| X | c3 | <img src="barcode-glyphs/letter-X.png" height="38" alt="letter-X"> |
| Y | c4 | <img src="barcode-glyphs/letter-Y.png" height="38" alt="letter-Y"> |
| Z | c5 | <img src="barcode-glyphs/letter-Z.png" height="38" alt="letter-Z"> |

### バーコード全体の見本

入力文字列 `<10000131-3-2-503dddd9>`

<img src="barcode-glyphs/sample.png" width="700" alt="スタートからストップまでのカスタマバーコード（67本）">

## 参考資料

- [日本郵便「カスタマバーコードの体系について」](https://www.post.japanpost.jp/service/search/zipcode/zipmanual/p11.html)
- [日本郵便「カスタマバーコードのフォーマットおよびけた数」](https://www.post.japanpost.jp/service/search/zipcode/zipmanual/p12.html)
- [日本郵便「印字位置」](https://www.post.japanpost.jp/service/search/zipcode/zipmanual/p13.html)
