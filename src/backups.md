# バックアップ

<!-- toc -->

## 自動バックアップ

Ankiは、カードデータの自動バックアップを作成します。これには、カードのテキストとスケジュール情報が含まれますが、音声や画像ファイルは含まれません。

自動バックアップは、ミスからの回復に役立つ場合がありますが、それだけに頼るべきではありません。デバイスが壊れたり盗まれたりした場合には保護されません。[手動バックアップ](#手動colpkgバックアップ)と組み合わせることをおすすめします。

### 復元

自動バックアップから復元するには：

- Ankiを開き、ファイルメニューから「プロファイルを切り替る」を選択します。
- 「バックアップを開く」ボタンをクリックします。
- 復元したいバックアップを選択します。

バックアップから復元すると、バックアップが作成された時点からの変更は失われます。

バックアップから復元すると、Ankiは自動同期とバックアップを無効にします。正しいバックアップを復元したことを確認したら、通常の状態に戻すためにAnkiを閉じて再度開いてください。

### Anki 2.1.50+

バックアップは定期的に作成されます。バックアップ間の時間を[設定](preferences.md)で調整することができます。デフォルトは30分です。

特定の操作をすると、設定された時間が経過していなくてもバックアップを作成します：

- 一方向に強制同期でダウンロードしたとき
- .colpkgファイルのインポート（ファイル➔インポートを使用）
- ツール➔データベースのチェック

バックアップが2日以上経過すると、Ankiは古いバックアップの一部を削除し始めます。毎日、週ごと、月ごとに保持するバックアップの数を制御することができます。

2.1.50で作成されたバックアップは、古いAnkiバージョンにインポートすることはできません。

### 古いAnkiバージョン

コレクションが閉じられるたびに（Ankiを閉じる、プロファイルを切り替える、フル同期のダウンロードを行うなど）、Ankiはバックアップを作成します。デフォルトでは最大30個のバックアップを保存します。これは[設定](preferences.md)で調整することができます。

## 手動colpkgバックアップ

### 復元

手動バックアップから復元するには、ファイルメニューの「インポート」を使用します。

### 作成

Anki 2.1.50以降では、ファイルメニューの「バックアップの作成」を使用すると､すぐにバックアップを作成することができます。これは通常の自動バックアップと同じで、メディアファイルは含まれません。

サウンドや画像を含むバックアップを作成するには：

- ファイルメニューからエクスポートを選択します。
- 「Ankiコレクションパッケージ（.colpkg）」が選択されていることを確認します。
- 「メディアを含める」オプションを有効にします。

これにより、カードとそれに使用されるサウンド/画像が含まれる.colpkgファイルが作成されます。ファイルを別のデバイスやDropboxやGoogle Driveなどのクラウドベースのファイルストレージサービスに安全に保存することをおすすめします。

## AnkiWeb

AnkiWebとのコレクションの同期により、デバイスの紛失や盗難に対する一定の保護が提供されます。AnkiWebからコレクションを復元する必要がある場合は、設定画面で一方向の強制同期を強制するか、新しいデバイスから同期してから「ダウンロード」を選択します。
* \[ 強制同期 \] ツール ➔ 設定 ➔ ネットワーク ➔ 次回の同期は一方向に変更を強制実行する


## 削除ログ

Ankiは、削除されたノートをdeleted.txtというテキストファイルにログを保存します。これらのノートは｢ファイル ➔ インポート｣で読み込むことができますが、インポート機能は一度に1つのノートタイプしかサポートしていないため、異なるノートタイプから削除されたノートがある場合は、ファイルを別々のファイルに分割する必要があります。




<!--

## Automatic backups

Anki will create automatic backups of your card data. These include the text
on your cards and your scheduling information, but do not include sounds or
image files.

Automatic backups can be useful to recover from mistakes, but you should not
rely solely on them. Because they are stored on your local device, they will not
protect you if your device breaks or is stolen. We recommend you combine them with
[manual backups](#manual-colpkg-backups).

### Restoring

To restore from an automatic backup:

- Open Anki, and choose Switch Profile from the File menu.
- Click on the "Open Backup" button.
- Select the backup you wish to restore from.

When restoring from a backup, any changes made since the backup was created will be lost.

Anki disables automatic syncing and backups when you restore from a backup. Once you're
happy that you've restored the correct backup, close and re-open Anki to return to normal.

### Anki 2.1.50+

Backups are created periodically. You can configure the time between backups
in the [preferences](preferences.md) screen. The default is 30 minutes.

Certain operations will trigger a backup, even if the configured time has not
elapsed yet:

- A one-way sync download
- Importing a .colpkg file using File>Import
- Tools>Check Database

After backups are two days old, Anki will start removing some of the older ones.
You can control how many daily, weekly and monthly backups you'd like to keep.

Backups created with 2.1.50 will not be importable into older Anki versions.

### Older Anki versions

Each time your collection is closed (when closing Anki, switching
profiles, or doing a full sync download), Anki creates a backup. By default
it will store up to 30 backups; you can adjust this in the [preferences](preferences.md).

## Manual colpkg backups

### Restoring

You can restore from a manual backup by using File>Import.

### Creating

In Anki 2.1.50+, you can use File>Create Backup to trigger an immediate backup. This
functions like regular automatic backups, and does not include media files.

To create a backup that includes your sounds and images:

- Select Export from the File menu.
- Ensure "Anki collection package (.colpkg)" is selected.
- Enable the "include media" option.

This will create a .colpkg file that contains all of your cards and any sounds/images they
use. We recommend you store the file somewhere safe, like a different device, or a cloud-based
file storage service like Dropbox or Google Drive.

## AnkiWeb

[Synchronising](./syncing.md) your collection with AnkiWeb provides some level of protection
against your device being lost or stolen. If you need to restore your collection from AnkiWeb,
you can force a one-way sync in the preferences screen, or sync from a new device, and then choose
"Download".

## Deletion log

Anki logs deleted notes to a text file called deleted.txt in your
profile folder. These notes are in a text format that can be read by
File&gt;Import, though please note the import feature only supports a
single note type at one time, so if you have deleted notes from
different note types, you'll need to split the file into separate files
for each note type first.
-->