# LinuxへのAnkiのインストールとアップグレード

<!-- toc -->

## 必要条件

パッケージ版は、最近の64ビットIntel/AMD Linuxでglibcやlibwayland-client、systemdなどの一般的なライブラリを必要とします。異なるアーキテクチャ（例：ARM/AArch64）や最小限のLinuxディストリビューションを使用している場合、パッケージ版を使用することはできませんが、代わりに[Pythonホイール](https://betas.ankiweb.net/#via-pypipip)を使用できるかもしれません。

Debianおよびその派生ディストリビューション（Ubuntuや[Linuxが有効になっているChromebook](https://support.google.com/chromebook/answer/9145439?)など）を使用している場合、インストール前に以下を実行してください：

```shell
sudo apt install libxcb-xinerama0 libxcb-cursor0 libnss3
```

Ankiのインストール後に起動しない場合、[他のライブラリが不足している](./missing-libraries.md)可能性があります。

Ubuntu 24.04を使用している場合は、[このスレッド](https://forums.ankiweb.net/t/issues-running-on-ubuntu-24-04/40974)を参照してください。

Ankiのビルドシステムはglibcのみをサポートしているため、muslベースのディストリビューションは現在サポートされていません。

## インストール

Ankiをインストールするには：

1. <https://apps.ankiweb.net> からAnkiをダウンロードして、ダウンロードフォルダに保存します。-qt5と-qt6のどちらを選ぶかについては次のセクションを参照してください。
2. システムにzstdがインストールされていない場合は、インストールする必要があります（例：`sudo apt install zstd`）。
3. ターミナルを開き、適切なファイル名に置き換えて次のコマンドを実行します。

```shell
tar xaf Downloads/anki-2XXX-linux-qt6.tar.zst
cd anki-2XXX-linux-qt6
sudo ./install.sh
```

一部のLinuxシステムでは、`tar xaf --use-compress-program=unzstd`を使用する必要があるかもしれません。

4. その後、'anki'と入力してEnterキーを押すことでAnkiを起動できます。問題が発生した場合は、左側のリンクを参照してください。

## Qt5 vs. Qt6

最近のAnkiバージョンは、Qt5とQt6の別々のバリアントで提供されています。ほとんどのユーザーにはQt6バージョンが推奨されます。

Qt6バージョンの利点：

- 最近のglibcバージョンとの互換性（最近のディストリビューションでの[空白画面の修正](./blank-window.md)）。
- より良いHiDPIサポート。
- より良いWaylandサポート。
- 様々なバグ修正、例えば、あまり一般的でない言語のサポートの向上。
- セキュリティアップデート。Qt5ライブラリのサポートは2020年11月に終了しており、それ以降に発見されたセキュリティの欠陥は修正されません。

Qt6バージョンの欠点：

- 一部のアドオンは現在Qt5バージョンでのみ動作します。

## アップグレード

以前に.deb/.rpmなどからAnkiを実行していた場合は、ここで提供されているパッケージをインストールする前にシステムバージョンを削除してください。

以前のパッケージからアップグレードする場合は、インストール手順を繰り返して最新バージョンにアップグレードするだけです。ユーザーデータは保持されます。

以前のバージョンにダウングレードしたい場合は、まず[ダウングレード](http://changes.ankiweb.net)を行ってください。

## アドオンの互換性

一部のアドオンは最新のAnkiリリースで常に動作するとは限りません。最新のAnkiバージョンにアップグレードして、どうしても必要なアドオンが動作しなくなった場合は、[リリースページ](https://github.com/ankitects/anki/releases)から古いAnkiバージョンをダウンロードできます。

## 問題

Ankiのインストールや起動時に問題が発生した場合は、以下のページを参照してください：
- [不足しているライブラリ](https://docs.ankiweb.net/platform/linux/missing-libraries.html)
- [表示の問題](https://docs.ankiweb.net/platform/linux/display-issues.html)
- [空白のメインウィンドウ](https://docs.ankiweb.net/platform/linux/blank-window.html)
- [Linuxディストリビューションのパッケージ](https://docs.ankiweb.net/platform/linux/distro-packages.html)
- [不正なGTKテーマ](https://docs.ankiweb.net/platform/linux/gtk-theme.html)
- [Wayland](https://docs.ankiweb.net/platform/linux/wayland.html)
- [入力方法](https://docs.ankiweb.net/platform/linux/input-methods.html)

