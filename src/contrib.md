# 貢献

<!-- toc -->

## デッキを公開で共有する

デッキを一般公開で共有するには、AnkiWebと同期 ([synchronize](syncing.md))し、AnkiWebにログインして、共有したいデッキの横にあるメニューから「共有」をクリックします。

以前にデッキを共有した場合（Ankiの以前のバージョンを含む）、上記のように「共有」をクリックして更新できます。共有デッキを更新しても、ダウンロード数や評価はリセットされません。アップロードした共有デッキは、共有デッキのページにある削除ボタンを使用して削除できます。

デッキを更新する際、AnkiWebはデッキが以前と同じ場所にあることを期待します。例えば、デッキを「Korean Verbs」として共有し、その後「Korean::Korean Verbs」に名前を変更した場合、再共有しても既存のコピーを更新することはできません。元の名前を忘れた場合は、AnkiWebでデッキをダウンロードして新しいプロファイル（ファイル > プロファイルの切り替え > 追加）にインポート（ファイル > インポート）することで推測できます。その後、最初に共有したときの正確な名前をコピーできます。これでもうまくいかない場合は、サポートに連絡してください。

共有デッキを更新すると、以前にデッキをダウンロードしたユーザーは自動的に更新を受け取りません。再度デッキをダウンロードして再インポートすると、新しく追加された素材は既存の学習進捗を変更することなくインポートされます。ただし、最初のインポート以降にあなたやユーザーがノートタイプを変更していない場合に限ります。

## デッキをプライベートに共有する

デッキを一般公開ではなく、限られたグループの人々（例えば、勉強会やクラス）と共有したい場合は、AnkiWebの外で共有することができます。

デッキをプライベートに共有するには、ファイルメニューに移動してエクスポートを選択します。単一のデッキ（「すべてのデッキ」ではなく）を選択し、「スケジュール情報を含む」をオフにします。これにより、他の人と共有できる.apkgファイルが生成されます。

.apkgファイルは、メールで送信したり、ウェブサイトや共有フォルダに置いたり、DropboxやGoogle Driveなどの無料のファイル共有サービスを使用してリンクを送信することで共有できます。

コンピュータ版とモバイルクライアントの両方で、.apkgファイルをクリックまたはタップするだけで簡単にインポートできます。ただし、AnkiWebは.apkgファイルをインポートする機能がないため、デッキの受信者はコンピュータ版またはモバイルデバイス上のAnkiを持っている必要があります。

ユーザーが.apkgファイルをインポートすると、そのコレクションに既に存在するカードは無視され、新しいカードが追加されます。同じノートタイプを使用している限り、変更されたカードも更新されます。データの損失を防ぐために、新しい.apkgファイルで削除されたカードはユーザーのコレクションから削除されません。したがって、何らかの理由でユーザーのデッキからカードを削除する必要がある場合は、ユーザーに連絡する必要があります。

## アドオンの共有

<https://addon-docs.ankiweb.net/sharing.html>をご覧ください。

## Ankiの翻訳

<https://translating.ankiweb.net>をご覧ください。

## コードの貢献

Ankiのソースコードは<https://github.com/ankitects/anki>で利用できます。

貢献する前に、[contributing.md](https://github.com/ankitects/anki/blob/main/docs/contributing.md)をご覧ください。





<!-- # Contributing -->

<!-- toc -->
<!-- 
## Sharing Decks Publicly

To share decks with the general public, [synchronize](syncing.md) them
with AnkiWeb, then log into AnkiWeb and click on "Share" from the menu
next to the deck you wish to share.

If you shared a deck previously (including with previous versions of
Anki), you can update it by clicking "Share" as above. Updating a shared
deck will not reset the download counts or ratings. You can delete a
shared deck that you have uploaded using the Delete button on the shared
deck's page.

When updating a deck, AnkiWeb expects the deck to be at the same
location as before. If you shared a deck when it was called "Korean
Verbs" for example, and then renamed it to "Korean::Korean Verbs",
resharing will not be able to update the existing copy. If you have
forgotten the original name, you can guess it by downloading the
deck on AnkiWeb and importing it (File > Import) in a new profile
(File > Switch profile > Add). Then you can copy the exact name of the
deck when it was first shared. If this doesn't work, please contact
support.

When you update a shared deck, users who downloaded the deck previously
will not automatically receive updates. If they download the deck again
and re-import it, newly added material will be imported without altering
their existing study progress, provided neither you nor the user has
altered the note type since the first import.

## Sharing Decks Privately

If you’d like to share decks with a limited group of people (such as a
study group or class) rather than the general public, you can do so by
sharing them outside of AnkiWeb.

To share a deck privately, go to the File menu and choose Export. Select
a single deck (not "All Decks"), and turn off "include scheduling
information". This will produce an .apkg file which you can share with
others.

You can share the .apkg file by emailing it to people, placing it on a
website or shared folder, or using a free file sharing service like
Dropbox or Google Drive and sending people a link.

Both the computer version and mobile clients make it easy to import from
an apkg file simply by clicking or tapping on it. AnkiWeb does not have
the ability to import apkg files however, so the recipients of your deck
will need to have the computer version or Anki on their mobile device.

When a user imports an .apkg file, cards that already exist in their
collection will be ignored and any new cards will be added. As long as
they use the same note type, modified cards will also be updated. To
prevent data loss, cards that have been deleted in the new apkg file
will not be deleted in the user’s collection, so if you need to delete
cards from users' decks for whatever reason, you will need to contact
them about it.

## Sharing Add-ons

Please see <https://addon-docs.ankiweb.net/sharing.html>

## Translating Anki

Please see <https://translating.ankiweb.net>

## Contributing Code

Anki's source code is available at <https://github.com/ankitects/anki>

Before contributing, please see [contributing.md](https://github.com/ankitects/anki/blob/main/docs/contributing.md).
 -->
