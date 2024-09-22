# メディア

Ankiは、ノートで使用される音声や画像をコレクションの隣にあるフォルダに保存します。フォルダの場所については、[ファイルの場所](files.md#ファイルの場所)セクションを参照してください。Anki内でメディアを追加する場合、クリップアイコンを使用するか、フィールドに貼り付けることで、元の場所からメディアフォルダにコピーされます。これにより、コレクションのメディアをバックアップしたり、別のコンピュータに移動したりすることが簡単になります。

メディアのファイル名にスペースやパーセント記号などの特殊文字が含まれている場合、HTMLエディタでのファイル名の表示方法は、ディスク上のファイル名の表示方法とは異なります。例えば、`hello 100%.jpg`というファイルは、HTMLエディタでは`hello%20100%25.jpg`として表示されます。内部的には、Ankiは元のファイル名を使用しているため、ファイルを[検索](searching.md)したり、ファイル名を[検索と置換](browsing.md#検索と置換)で変更したりする場合は、HTMLエディタに表示される名前ではなく、ディスク上の名前を使用する必要があります。テキストファイルにエクスポートすることで、基礎となる表現を見ることもできます。

## メディアの確認

ツール > メディアの確認メニューオプションを使用して、ノートとメディアフォルダをスキャンできます。これにより、メディアフォルダ内のノートで使用されていないファイルや、ノートで参照されているがメディアフォルダに存在しないメディアのレポートが生成されます。また、以下のことが可能です：

- 未使用のメディアファイルを削除する。
- メディアファイルが欠けているノートにタグを付ける。
- ゴミ箱フォルダを空にする。
- 削除されたファイルをメディアフォルダに復元する。

このツールは質問や回答のテンプレートをスキャンしないため、テンプレートにフィールドへのメディア参照を配置することはできません。すべてのカードに静的な画像や音声が必要な場合は、先頭にアンダースコア（例：`\_dog.jpg`）を付けて名前を付け、メディアの確認時にAnkiが無視するようにします。未使用のメディアチェックを使用してメディアを削除すると、Ankiはそれをオペレーティングシステムのゴミ箱フォルダに移動するため、誤って削除したメディアを回復することができます。

## メディアの手動追加

Ankiのインターフェースを介してメディアを追加する場合、Ankiはファイル名が異なるデバイス間で動作するようにエンコードされることを保証し、特定のオペレーティングシステムで動作しない文字を削除し、非常に長いファイル名を切り詰めます。

[メディアフォルダ](files.md#ファイルの場所)に手動でファイルを追加する場合は、後でツール > メディアの確認を使用して、ファイル名が正しくエンコードされていることを確認する必要があります。この手順をスキップすると、互換性のないファイル名が同期時にスキップされます。

## サポートされている形式

Ankiは、mpv（およびフォールバックとしてmplayer）というプログラムを使用して、音声や動画をサポートしています。さまざまなファイル形式がサポートされていますが、これらの形式すべてがAnkiWebおよびモバイルクライアントで動作するわけではありません。MP3音声およびMP4動画が最も広くサポートされているようです。