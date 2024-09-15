# トラブルシューティング

Ankiで問題が発生した場合、以下の手順を順番に試してください：

**1. Ankiを再起動する**

Ankiを閉じてから、再度起動してください。

エラーメッセージのためにAnkiを閉じることができない場合は、タスクマネージャーを使用してAnkiを終了するか、コンピュータを再起動してください。Ankiは定期的に保存するため、ほとんどの場合、数分以上の作業が失われることはありません。

問題が再発しない場合は、以下の手順をスキップできます。

**2. アドオンを確認する**

Ankiを閉じて、Shiftキーを押しながら再起動してください。問題が解消される場合、アドオンが原因であることを示しています。不要なアドオンを削除し、残りのアドオンの半分を無効にしてください。問題が続く場合は、もう半分を試してください。このプロセスを繰り返して、どのアドオンが問題を引き起こしているかを特定します。その後、デバッグ情報をコピーするボタンを使用して、その情報をレポートに貼り付け、アドオンの作者に問題を報告してください。

**3. Ankiのバージョンを確認する**

使用しているバージョンは、ヘルプ>バージョン情報またはAnki>バージョン情報メニューで確認できます。使用しているバージョンが<https://apps.ankiweb.net>に公開されている最新バージョンでない場合は、Ankiを閉じて最新バージョンをインストールし、再度Ankiを起動して問題が解消されたか確認してください。

Linuxを使用している場合は、Ankiのウェブサイトで提供されているパッケージ版でエラーを再現できることを確認してください。ディストリビューションによっては[壊れたバージョン](https://anki.tenderapp.com/kb/anki-ecosystem/third-party-linux-packages-and-source-builds-are-not-supported)を配布していることがあります。

**4. データベースを確認する**

Ankiを再起動した後、ツール>データベースの確認メニュー項目を試して、コレクションに問題がないか確認してください。

**5. コンピュータを再起動する**

コンピュータを再起動すると問題が解決する場合があります。

**6. ビデオドライバを変更する**

クラッシュや表示の問題はビデオドライバが原因であることがあります。設定画面やgldriverファイルを使用して、別のビデオドライバに変更すると役立つ場合があります。すべてのオプションを試してください。

- [Windows](https://docs.ankiweb.net/platform/windows/display-issues.html)
- [Mac](https://docs.ankiweb.net/platform/mac/display-issues.html)
- [Linux](https://docs.ankiweb.net/platform/linux/display-issues.html)

**7. ウィンドウサイズをリセットする**

Ankiを起動した直後に設定画面で「ウィンドウサイズをリセット」ボタンを押すと、問題が解決する場合があります。

**8. 問題が解決しない場合**

最新のAnkiバージョンを使用していることを確認し、Shiftキーを押しながらAnkiを起動してもエラーが発生する場合は、[問題を報告](./getting-help.md)してください。次に受け取るエラーメッセージを投稿に含めてください。