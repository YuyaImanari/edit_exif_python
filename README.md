# EXIF情報をPythonで編集するコードまとめ

## 1. 仕組みなど

`piexif` と `pillow` を使った2通りの方法があります。

### piexif

piexif は簡単にEXIF情報を削除できます。実質1行です。  
ただし、削除できない画像もあるという噂があります。また、JPEGもしくはTIFFファイルのみ扱えます。  
また、`piexif.remove()` は破壊的であり、元画像が上書きされます。

### pillow

pillow は割と有名な画像編集ライブラリで、自由度高く画像を編集できます。  
JPEGファイルもPNGファイルも実行できます。

### EXIF情報と画像の回転

カメラで撮影されたJPEG画像は、基本的に横長のデータとして保存されています。それをEXIFの `orientation` というタグに回転反転情報として持たせ、自然に表示しています。  
したがって、EXIF情報をすべて消すと、縦画像が90度回転されます。  
今回は、`orientation` を取得した上で、pillowを使って画像を回転させて保存することで解決します。

## 2. 使い方

1. 画像を好きなところにおき、各コードの `filename_input` に画像パスを指定してください。
2. 実行したいコードブロックを実行します。ただし、piexifは破壊的であり、元画像データが上書きされるので気をつけてください。

## 3. 参考記事

[Python で JPG ファイルから Exif 情報を削除する｜Junf / Jade｜note](https://note.com/junf/n/n553d4a9a99c3)  
[【Pillow】画像ファイルからExif情報を削除する - よちよちpython](https://chayarokurokuro.hatenablog.com/entry/2019/09/19/230924)  
[PILでEXIF Orientationタグを考慮して処理 - Qiita](https://qiita.com/Klein/items/a04cf1a6c94d6f03846e)