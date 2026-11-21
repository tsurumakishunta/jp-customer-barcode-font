# カスタマバーコードフォント

日本郵便の仕様に基づくカスタマバーコード用TrueTypeフォントです。郵便番号と町域名以降の住所を入力すると、印字用文字列とバーコードをブラウザで確認できます。

## ファイル

| ファイル | 内容 |
| --- | --- |
| [JPCustomerBarcode.ttf](JPCustomerBarcode.ttf) | バーコード印字用フォント |
| [index.html](index.html) | 印字用文字列の生成とバーコードのプレビュー |
| [BarcodeGlyphs.html](BarcodeGlyphs.html) | 入力文字とバーの対応表 |

## ブラウザで試す

1. リポジトリの **Code → Download ZIP** からダウンロードして展開します。
2. `index.html` をブラウザで開き、郵便番号と、町域名以降の住所を入力します。
3. **生成**を押すと、印字用文字列とバーコードが表示されます。**コピー**で印字用文字列を取得できます。

例として、郵便番号 `100-0013` と、町域名以降の住所 `1丁目3番2号 郵便プラザ503室` を入力すると、`<10000131-3-2-503dddd9>` が表示されます。入力した住所はブラウザ内で処理します。

## 帳票で使う

`JPCustomerBarcode.ttf` をインストールし、生成された文字列に **JP Customer Barcode Regular** を指定します。基準サイズは **10 pt** です。印刷時は倍率を100%にし、上下左右に2 mm以上の余白を確保してください。実際の帳票とプリンターで読み取りをご確認ください。

| フォントに渡す文字 | 印字される内容 |
| --- | --- |
| 半角 `<` または `(` | スタートコード |
| 半角 `>` または `)` | ストップコード |
| 半角小文字 `a`〜`h` | 制御コード CC1〜CC8 |
| 半角大文字 `A`〜`Z` | 住所の英字に対応する2コード分 |

小文字の `d` は住所表示番号の不足分を埋めるCC4として使います。大文字の `D` は住所の英字に対応し、`a3` と同じバーを印字します。バーの形は [文字とバーの対応表](BarcodeGlyphs.html) を参照してください。

## 参考資料

- [日本郵便「カスタマバーコードの体系について」](https://www.post.japanpost.jp/service/search/zipcode/zipmanual/p11.html)
- [日本郵便「カスタマバーコードのフォーマットおよびけた数」](https://www.post.japanpost.jp/service/search/zipcode/zipmanual/p12.html)
- [日本郵便「印字位置」](https://www.post.japanpost.jp/service/search/zipcode/zipmanual/p13.html)
