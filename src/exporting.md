
# エクスポート

<!-- toc -->

エクスポートを使用すると、コレクションの一部をテキストファイルまたはパッケージ化されたAnkiデッキとして保存できます。エクスポートするには、ファイルメニューをクリックし、「エクスポート」を選択します。

## テキストファイル

「プレーンテキストのノート」を選択すると、Ankiはノートの内容をテキストファイルに書き込みます。各フィールドはタブで区切られています。結果として得られたファイルを編集し、最初のフィールドを変更しない場合、同じノートタイプにインポートすることで、Ankiは編集に基づいてノートを更新します。

最初のフィールドも編集する必要がある場合は、ノートタイプの形式を変更して、最初のフィールドが実際のテキストではなくID番号になるようにする必要があります。（これを簡単にするために、[Add note id](https://ankiweb.net/shared/info/1672832404)アドオンをインストールできます。）

テキストをインポートする際にフォーマットが保持されるように、テキストはすべてのHTMLフォーマットが埋め込まれた状態でエクスポートされます。

## パッケージ化されたデッキ

「パッケージ化されたデッキ」は、カード、ノート、ノートタイプ、および.apkgまたは.colpkgで終わるファイルにバンドルされたサウンドや画像で構成されています。パッケージ化されたデッキを使用して、カードを他の人と共有したり、コレクションの一部をバックアップしたりできます。

パッケージ化されたデッキには2種類あります。

### コレクション (.colpkg)

すべてのデッキをスケジューリング情報と共にエクスポートする場合、これを「コレクションパッケージ」と呼びます。Ankiはコレクション全体を.colpkgで終わるファイルにコピーし、デスクトップに配置します。コレクションパッケージは、コレクションをバックアップするか、別のデバイスにコピーするために使用されます。

以前のバージョンのAnkiで作成されたコレクションパッケージは、collection.apkgと呼ばれていました。

このファイルを後でインポートすると、Ankiはコレクション内の現在のすべてのカードを削除し、ファイル内のアイテムでコレクションを置き換えます。これは、デバイス間でコレクションをやり取りするのに便利です。

コレクションパッケージをインポートしても、コレクション内の既存のメディアは削除されません。未使用のメディアを削除するには、ツール>メディアのチェックを使用します。

Anki 2.1.50+コレクションパッケージ形式を選択すると、インポートとエクスポートが高速になり、メディアファイルが圧縮されますが、結果として得られる.colpkgファイルは古いAnkiクライアントでは読み取れません。

### デッキ (.apkg)

デッキパッケージには、単一のデッキ（およびその子デッキ）が含まれています。ファイル名は.apkgで終わりますが、collection.apkg以外のファイル名です。デッキパッケージをインポートすると、Ankiはコレクションを上書きするのではなく、内容をコレクションに追加します。

デッキパッケージ内の一部のノートが以前にインポートされている場合、Ankiは最も最近の変更時間を持つバージョンを保持します。したがって、更新されたデッキをダウンロードすると、更新バージョンで行われた編集がコレクションにも反映されますが、コレクションで編集を行った後に変更されていないデッキを再インポートすると、コレクション内の変更が保持されます。

スケジューリング情報を含めないことを選択した場合、Ankiはデッキを他の人と共有していると見なし、マークされたタグやリークタグを削除して、クリーンなコピーを提供します。






<!-- # Exporting -->

<!-- toc -->
<!-- 
Exporting allows you to save part of your collection as a text file or
packaged Anki deck. To export, click the File menu and choose 'Export'.

## Text Files

If you choose "Notes in Plain Text", Anki will write the contents of the
notes into a text file. Each field is separated by a tab. If you edit
the resulting file and don't modify the first field, you can later
import that file back into Anki and Anki will update your notes based on
your edits, provided you import back into the same note type.

If you find yourself needing to edit the first field as well, you'll
need to change the format of your note type so that the first field is
an ID number rather than actual text. (You can install
the [Add note id](https://ankiweb.net/shared/info/1672832404)
add-on to make this easier.)

In order for formatting to be preserved when you import text back in,
the text is exported with all the HTML formatting embedded in it.

## Packaged Decks

A 'packaged deck' consists of cards, notes, note types, and any sounds or
images bundled up into a file ending with .apkg or .colpkg. You can use
packaged decks to transfer cards between people, or for backing up parts
of your collection.

There are two different kinds of packaged decks.

### Collection (.colpkg)

When you export all decks with scheduling included, this is called a
'collection package'. Anki will copy your entire collection into a file
ending in .colpkg, and place it on your desktop. A collection package is
used to back up your collection, or copy it to another device.

Collection packages created with previous versions of Anki were called
collection.apkg.

When this file is later imported, Anki will delete all the current cards
in the collection, and replace the collection with the items in the
file. This is useful for copying your collection back and forth between
devices.

Existing media in your collection is not deleted when you import a
collection package. To delete unused media, use Tools&gt;Check Media.

If you choose Anki 2.1.50+ Collection Package format, imports and exports
will be faster, and media files will be compressed, but the resulting
.colpkg file will not be readable by older Anki clients.

### Deck (.apkg)

Deck packages contain a single deck (and any child decks it may have).
They have a filename ending with .apkg, but a filename other than
collection.apkg. When you import a deck package, Anki will add the
contents into your collection, rather than overwriting your collection.

If some notes in the deck package have previously been imported, Anki
will keep the version with the most recent modification time. So if you
download an updated deck, the edits that have been made in the updated
version will be made in your collection as well, but if you re-import an
unchanged deck after making edits in your collection, the changes in
your collection will be kept.

If you choose not to include scheduling information, Anki will assume
that you are sharing the deck with other people, and will remove marked
and leech tags so that they will have a clean copy of it. -->
