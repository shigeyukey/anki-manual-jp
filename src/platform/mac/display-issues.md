# macOSでの表示の問題

<!-- toc -->

## Qt6ビデオドライバ

Anki 23.10+で表示の問題やクラッシュが発生している場合は、設定画面でビデオドライバを変更し、Ankiを再起動してみてください。

以前のAnkiバージョンでは設定画面にオプションがありませんでしたが、Terminal.appを開き、以下を貼り付けてEnterキーを押すことでドライバを調整できました：

```
echo software > ~/Library/Application\ Support/Anki2/gldriver6
```

何も表示されません。その後、再度Ankiを起動できます。

デフォルトに戻したい場合は、「software」を「auto」に変更するか、そのファイルを削除してください。

## eGPU

Macで外部グラフィックスカードを使用しているときに画面が空白になる場合は、Ankiアプリをcontrolキーを押しながらクリックし、「情報を見る」をクリックして、「eGPUを優先する」オプションを有効にします。

## 異なる解像度のモニター

[このフォーラムの投稿](https://forums.ankiweb.net/t/mac-known-issues-wording-suggestion/7331)を参照してください。