# Windowsでの表示の問題

<!-- toc -->

Windowsでは、画面にコンテンツを表示する方法が3つあります。デフォルトはソフトウェアで、これは遅いですが最も互換性があります。他に2つのオプションがあり、それらはより高速です：OpenGLとANGLE。これらは高速ですが、動作しない場合や、メニューバーが表示されない、ウィンドウが空白になるなどの表示問題を引き起こすことがあります。どれが最適かはコンピュータによります。

この表示方法を変更できるかどうか、およびその方法は、使用しているAnkiのバージョン、正確には使用されているQtツールキットのバージョンによります。

## Qt5

このツールキットは、2.1.50以前のすべてのAnkiバージョンで使用されています。
ここでは、表示ドライバはツール > 設定メニューから調整できます。調整後、Ankiを再起動してください。

Ankiの設定画面にアクセスできない場合や、Ankiを数回再起動しても問題が解決しない場合は、グラフィックドライバを手動で調整する必要があるかもしれません。これを行うには、cmd.exeを起動し、次のように入力します：

```bat
echo auto > %APPDATA%\Anki2\gldriver
```
何も表示されません。その後、再度Ankiを起動できます。

デフォルトは `software` です。他に試せるドライバは `angle` と `auto` です。

## Qt6

Anki 2.1.50+ は、より新しいQt6ツールキットを使用しています。新しいツールキットでは、グラフィックアクセラレーションがデフォルトで有効になっています。表示の問題が発生した場合は、cmdを使用してソフトウェアモードに切り替えてみてください：

```bat
echo software > %APPDATA%\Anki2\gldriver6
```

または、PowerShellを使用して行うこともできます：

```powershell
echo software > $env:APPDATA\Anki2\gldriver6
```

何も表示されません。その後、再度Ankiを起動できます。

デフォルトの動作に戻すには、「software」を「auto」に変更するか、そのファイルを削除してください。

Anki 23.10+ では、設定画面からグラフィックドライバを変更することもできます。

## フルスクリーン

Anki 2.1.50+ にはフルスクリーンモードが搭載されていますが、さまざまな問題により、`OpenGL` を使用している場合は無効にする必要がありました。上記のようにソフトウェアレンダリングをオンにすると、フルスクリーンオプションを使用できるようになりますが、レンダリングパフォーマンスが低下する可能性があることに注意してください。

Anki 23.10+ では、デフォルトの Direct3D ドライバでフルスクリーンモードがサポートされています。