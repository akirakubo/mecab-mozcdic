# mecab-mozcdic

## 概要
open source mozc dictionaryをMeCab辞書のフォーマットに変換したものです。

## 使用方法
matrix.def.gzを展開後、

```
$ mecab-dict-index -d . -o . -f UTF-8 -t UTF-8
```

を実行して解析用バイナリ辞書を作成し、MeCabから使用します。

### 解析例
```
$ mecab -d .
さくらのはながさきました。
さくらのはな 名詞,一般,*,*,*,*,NULL,桜の花,NULL
が           助詞,格助詞,一般,*,*,*,NULL,が,NULL
さき         動詞,自立,*,*,五段・カ行イ音便,連用形,NULL,咲き,NULL
まし         助動詞,*,*,*,特殊・マス,連用形,NULL,まし,NULL
た           助動詞,*,*,*,特殊・タ,基本形,NULL,た,NULL
。           記号,句点,*,*,*,*,NULL,。,NULL
EOS
```

## エントリのフォーマットについて
* mecab-ipadicと同じです。
* 元の辞書が仮名漢字変換用なので、通常の形態素解析用辞書と異なり、「表層形」と「読み」が逆です。
* 「原形」と「発音」については、一律「NULL」としています。

## 注意事項
* Mozcは、単に辞書を使うだけでなく、誤変換を防ぐために色々な工夫を行っているため、mecab-mozcdicで「変換」した結果とは一致しない場合があります。
* 生成過程のミス等により、結果として変なファイルが生成されているおそれがあります。

## ライセンス
* dictionary*.csv、left-id.def、right-id.def、matrix.defは、Open source mozc dictionaryから生成されています。
* dicrc、unk.def、rewrite.defは、mecab-ipadic-2.7.0-20070801から生成されています。

詳細については、LICENSE.txtを参照してください。
