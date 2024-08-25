# ブラウジング

<!-- toc -->

ブラウザウィンドウでは、カードやノートを検索して編集することができます。
メインウィンドウで「ブラウザ」をクリックするか、<kbd>B</kbd>を押すことで開くことができます。
ブラウザウィンドウは、左側の「サイドバー」、右上の「カード/ノートテーブル」、右下の「編集エリア」の3つのセクションで構成されています。
セクションの間にマウスを置き、クリックしてドラッグすることで、セクションのサイズを変更することができます。



## テーブルモード

![テーブルモード](media/browser_table_modes.png)

Anki 2.1.45+では、カードまたはノートがデータテーブルに表示される2つのモードが提供されています。
現在のモードは、上部のスイッチをクリックするか、<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>または<kbd>Cmd</kbd>+<kbd>Opt</kbd>+<kbd>T</kbd>を押すことで変更することができます。
スイッチは、現在 **C**（カード）または **N**（ノート）が表示されているかどうかも示しています。

**注意**: 説明をシンプルにするため、このマニュアルでは通常、カードモードを現在有効なモードとして扱っています。
「カード」の選択/検索などについて言及したい場合、読者は現在有効なモードに応じて「カードまたはノート」に置き換えることができます。

## サイドバー

左側の「サイドバー」では、一般的な検索用語へのクイックアクセスが可能です。
Anki 2.1.45+では、検索バー、タグとデッキの編集機能、および2つの異なるツールの選択肢も提供されています。
ツールは、サイドバーの上部にあるツールバーまたはショートカット<kbd>Alt</kbd>+<kbd>1</kbd>/<kbd>2</kbd>を使用して切り替えることができます。

### 検索ツール

![検索ツール](media/browser_search_tool.png)

このツールでは、サイドバーは以前のバージョンと同様に動作します。
アイテムをクリックすると、それに対して検索が実行されます。

<kbd>Ctrl</kbd>（Macでは<kbd>Command</kbd>）を押しながらクリックすると、クリックしたアイテムを現在の検索にAND条件で追加することができます。
たとえば、ドイツのデッキにある「学習」カードを表示したい場合、"学習"をクリックし、その後<kbd>Ctrl</kbd>を押しながら"ドイツ"をクリックします。

<kbd>Shift</kbd>を押しながらクリックすると、AND条件ではなくOR条件の検索が作成されます。
たとえば、1つのデッキをクリックし、その後<kbd>Shift</kbd>を押しながら別のデッキをクリックすると、両方のデッキからのカードが同じビューに表示されます。

<kbd>Alt</kbd>（Macでは<kbd>Option</kbd>）を押すと、検索を逆にすることができます（先頭に`-`を追加）。
たとえば、特定のタグを持たない現在のデッキのすべてのカードを表示したい場合、<kbd>Alt</kbd>を押しながらクリックすることで実行できます。
<kbd>Alt</kbd>/<kbd>Option</kbd>は、<kbd>Ctrl</kbd>または<kbd>Shift</kbd>と組み合わせることもできます（たとえば、<kbd>Ctrl</kbd>+<kbd>Alt</kbd>でクリックすると、反転した検索条件が新しく追加されます）。

Anki 2.1.39+では、同種の検索のすべての出現箇所を新しい検索で置き換えるために、<kbd>Ctrl</kbd>と<kbd>Shift</kbd>を同時に押しながら検索用語をクリックすることもできます。
たとえば、以前に`deck:英語 (is:due or tag:必須単語)`という複雑な検索式を入力したあと、スペイン語デッキで同じ検索を実行したい場合、スペイン語デッキをサイドバーでクリックしながら<kbd>Ctrl</kbd>+<kbd>Shift</kbd>を押すと、次の検索式が得られます: `deck:スペイン語 (is:due or tag:必須単語)`.


### 選択ツール

![選択ツール](media/browser_selection_tool2.png)

選択ツールは、<kbd>Ctrl</kbd>キーまたは<kbd>Shift</kbd>キーを押しながらクリックすることで、複数のアイテムを同時に選択することができます。また、デッキやタグの順序をドラッグアンドドロップで変更することも可能です。

例えば、`数学`、`微積分`、`代数学`というタグがあるとします。`微積分`タグをクリックし、次に<kbd>Ctrl</kbd>キーを押しながら`代数学`タグをクリックします。これで両方のタグが選択され、どちらかを`数学`タグにドラッグアンドドロップすると、両方のタグがこのタグの子になります。プログラムの裏側では、Ankiが2つのタグをそれぞれ`数学::微積分`と`数学::代数学`に変更し、ノートを更新しています。

複数のアイテムを選択するもう一つの使用例は検索です｡ アイテムを選択して右クリックすると、**｢検索｣ ➔ ｢選択条件すべてを含む/選択条件のいずれかを含む｣** を選択できます。これは[検索ツール](#検索ツール)で説明されているキーボード修飾子と組み合わせて、検索結果を現在の検索に追加できます。

* サイドバー ➔ タグをシフトキーで複数選択 ➔ 右クリック ➔ 検索 ➔ ｢選択条件すべてを含む/選択条件のいずれかを含む｣


### 保存した検索条件

同じことを定期的に検索する場合、サイドバーの一番上のアイテム(♡保存した検索条件)を右クリックし、「現在の検索条件を保存」を選択し、名前を入力すると、現在の検索条件を保存できます。また、サイドバーの任意のアイテムをこのエリアにドラッグアンドドロップすると、同じ保存検索を追加して上部に固定できます。


### アイテムの編集

タグ、デッキ、保存した検索条件は、サイドバーから、右クリックメニューから、またはショートカットキー（Windowsでは<kbd>Del</kbd>と<kbd>F2</kbd>）を使用して直接削除または名前変更できます。削除は複数のアイテムを一度に行うことも可能です（[選択ツール](#選択ツール)を参照）。


### アイテムの検索

サイドバーのツリー内の特定のアイテムを見つけるには、
名前を検索バーに入力して、検索に一致しないすべてのアイテムを一時的に非表示にします。


## 検索ボックス

カードリストの上には検索ボックスがあります。
ここに様々なことを入力してカードを検索できます。
検索構文については、[検索](searching.md)を参照してください。


## カード ノートテーブル

テーブルの行は、現在の検索に一致するカードまたはノートを表します。
行をクリックすると、対応するノートが下部セクションに表示されます。


### 行

マウスをドラッグするか、<kbd>Ctrl</kbd>キーまたは<kbd>Command</kbd>キーを押しながら複数の行を選択すると、エディタが一時的に非表示になります。
デッキの変更など、さまざまな操作は、アクティブなモードに依存せず、一度に複数のカードまたはノートに対して行うことができます。
したがって、カードモードでは、ノートのいずれかのカードが選択されている場合、そのノートは選択されたと見なされます。
ノートモードでは、カードが選択されている場合、そのカードのノートが選択されたと見なされます。

その他の操作（カード情報の表示など）は、単一のカードまたはノートにのみ適用されます。
これは「現在の」カードまたはノートと呼ばれ、通常は最後に選択またはクリックされたものです。
カードモードでは、再び、現在のノートは現在のカードのノートであり、ノートモードでは、現在のカードは現在のノートの最初のカードです。

背景色はカードとノートに応じて変化します。カードモードでは、最初に一致したものが使用されます:

1. カードが**フラグ付き**の場合、フラグの色が使用されます。
2. カードが**中断されている**場合、黄色が使用されます。
3. カードのノートが**マークされている**場合、紫が使用されます。

ノートモードでは、色はマークされたノートにのみ適用されます。
マークされたノートと中断されたカードについての詳細は、[編集とその他](studying.md#編集とその他)を参照してください。

### カラム

カラムは設定可能です: 右クリック（またはMacでは<kbd>Ctrl</kbd>をクリック）して表示するカラムを選択できます。
カラムをドラッグして並べ替えることもできます。カラムをクリックすると、そのカラムでソートされます。
再度クリックすると、ソート順が逆になります。ただし、QuestionとAnswerのカラムでのソートはできません。

すべてのカラムは、[カードモードとノートモード](#テーブルモード)の両方で利用できますが、
名前やデータが若干異なる場合があります。以下の表は、両モードの動作をリストしています。

<!-- prettier-ignore -->

| Column          | カード モード                                                                                                                                                                                                                             | ノート モード                                                                                                                                                                                                     |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 回答         | カードの裏面は、質問が剥がされた1行で表示されます。カードタイプエディターで[カスタムフォーマット](templates/styling.md#ブラウザの外観)を選択することもできます。代わりに｡                                                      | カード モードと同じですが、メモの最初のカードのみが対象です。                                                                                                                                                |
| カード(s)         | カードのテンプレートの名前。                                                                                                                                                                                                       | ノートが持つカードの数。                                                                                                                                                                              |
| カードの変更日時   | カードに変更が行われた最後の日時（例：カードを復習し、復習履歴と間隔が更新された場合）。                                                                                                        | ノートのカードの中で変更が行われた最後の日時。                                                                                                                                                    |
| 作成日時         | カードのノートと同じ。                                                                                                                                                                                         | ノートが作成された日付。                                                                                                                                                                                 |
| デッキ            | カードが所属するデッキの名前。                                                                                                                                                                                                   | ノートのカードが所属する異なるデッキの数、またはすべてのカードが同じデッキに所属する場合はデッキの名前。                                                                                                     |
| 期限             | 復習や（再）習得中のカードの期限、および新しいカードのキュー内の位置。カードが中断されたり埋められた場合は角括弧で囲まれます。タイプによるソートが行われ、その後に日付または位置によるソートが行われます。 | ノートの次の復習や（再）学習カードの期限で、中断されていない、埋められていない、フィルターデッキに含まれていないカードの期限。                                                                                          |
| (平均) イーズ     | カードが新しい場合を除くイーズの値。                                                                                                                                                                                                      | 新しいカードではないノートのカードの平均イーズ。                                                                                                                                                        |
| (平均) インターバル | カードが復習または再習得中の場合のインターバルの値。                                                                                                                                                                            | 復習または再習得中のノートのカードの平均インターバル。                                                                                                                                    |
| ラプス          | カードが「もう一度」と評価された回数。                                                                                                                                                                                                  | ノートのすべてのカードの合計ラプス。                                                                                                                                                                    |
| ノート            | カードのノートと同じ。                                                                                                                                                                                         | ノートのノートタイプの名前。                                                                                                                                                                               |
| ノートの変更日時   | カードのノートと同じ。                                                                                                                                                                                         | ノート（フィールドの内容など）が編集された最後の日時。                                                                                                                                               |
| 質問        | カードの表面を1行で表示します。カードタイプエディタで[カスタムフォーマット](templates/styling.md#ブラウザの外観)を選択することもできます。                                                                                | カードモードと同じですが、ノートの最初のカードに対してのみです。                                                                                                                                                |
| 復習         | カードが復習された回数。                                                                                                                                                                                                  | ノートのすべてのカードの合計復習カウント。                                                                                                                                                              |
| ソートフィールド      | カードのノートと同じ。                                                                                                                                                                                         | ノートタイプのソートフィールドとして定義されたノートのフィールドの内容。このフィールドのみが表示およびソートされます。編集エリアで**フィールド...**をクリックしてソートフィールドを変更できます。 |
| タグ            | カードのノートと同じ。                                                                                                                                                                                         | ノートのタグ。                                                                                                                                                                                               |

## 編集エリア

右下のエリアには現在選択されている行のノートが表示されます。詳細については、[はじめに](getting-started.md)を参照してください。
フォーマットボタンについての詳細は、[編集](editing.md)を参照してください。

現在選択されているカードのプレビューを確認するには、編集エリアの上部にある**プレビュー**ボタンをクリックします。
これにより、カードのタイプアンサーフィールドが表示されないため、カードを素早くプレビューすることができます。
ノートモードでは、プレビューは選択したノートの最初のカードに対して表示されます。

## メニューとアクション

ブラウザウィンドウの上部には、さまざまなメニューがあるツールバーがあり、それぞれのメニューにはブラウザで実行できるさまざまなアクションが用意されています。

### 編集

<!-- prettier-ignore -->

| 名前                 | アクション                                                                                                                                                                                                                        |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 元に戻す                 | 直前に実行された操作を元に戻します。                                                                                                                                                                                 |
| すべて選択           | 表示されているすべての行を選択します。                                                                                                                                                                                                    |
| ノートを選択         | 現在選択されているノートのみを表示し、すべての行を選択します。                                                                                                                                                                   |
| 選択を反転     | 選択されていない行を選択し、現在選択されている行を選択解除します。                                                                                                                                                     |
| フィルターデッキを作成 | [フィルターデッキ](filtered-decks.md#手動での作成)ダイアログを表示し、現在のブラウザ検索をフィルターとして設定します。代わりに2番目のフィルターを設定するには<kbd>Alt</kbd> / <kbd>Option</kbd>を使用します（スケジューラバージョン2以上が必要です）。 |

### ノート

以下のアクションのほとんどは、選択されたノートに対して操作を行います。これらのアクションは、ノートモードでは選択された行を右クリックしたときのコンテキストメニューでも利用できます。カードモードでは、コンテキストメニューのサブメニューにあります。

<!-- prettier-ignore -->

| 名前              | アクション                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ノートを追加         | [追加](editing.md#カードとノートの追加)ダイアログを開きます。                                                                                                                                                                                                                                                                                                  |
| コピーを作成       | 現在のノートの[エディタ](editing.md#カードとノートの追加)での[重複](browsing.md#重複の検索)を開き、カードのバリエーションを簡単に取得するためにわずかに変更できます。デフォルトでは、重複したカードは元のデッキと同じデッキに作成されます。                                                                      |
| ノートをエクスポート      | [エクスポート](exporting.md)ダイアログを開きます。                                                                                                                                                                                                                                                                                                                    |
| タグを追加          | 選択したすべてのノートに指定されたタグを追加します。                                                                                                                                                                                                                                                                                                                   |
| タグを削除       | タグを入力し、選択したすべてのノートからタグを削除します。                                                                                                                                                                                                                                                                                                        |
| 未使用のタグをクリア | サイドバーから、ノートで使用されていないすべてのタグを削除します。                                                                                                                                                                                                                                                                                           |
| マークを切り替え       | 現在のノートがマークされている場合（つまり、_マークされた_タグを持っている場合）、選択したすべてのノートのマークを解除します。現在のノートがマークされていない場合、選択したすべてのノートをマークします。                                                                                                                                                                                                              |
| ノートタイプを変更   | 選択したノートを別のタイプに変換します。たとえば、_Russian_ノートタイプと_Computer_ノートタイプがあるとしましょう。_Russian_ノートにコンピュータ関連のテキストを誤って追加した場合、このオプションを使用してその間違いを修正できます。カードのスケジュールは影響を受けません。ノートのタイプを変更するには、ワンウェイ同期が必要です。 |
| 重複を検索   | [重複](#重複の検索)ダイアログを開きます。                                                                                                                                                                                                                                                                                                         |
| 検索して置換  | [検索して置換](#検索と置換)ダイアログを開きます。                                                                                                                                                                                                                                                                                                     |
| ノートタイプを管理  | [ノートタイプ](editing.md#ノートタイプの追加)ダイアログを開きます。                                                                                                                                                                                                                                                                                                |
| 削除            | 選択したすべてのノートとそのカードを削除します。個々のカードを削除することはできません。個々のカードは[テンプレート](templates/intro.md)によって制御されます。                                                                                                                                                                                       |

### カード

以下のアクションは、現在選択されているカードに対して操作を行います。カードモードでは、選択した行を右クリックしたときのコンテキストメニューでも利用できます。ノートモードでは、コンテキストメニューのサブメニューにあります。

<!-- prettier-ignore -->

| 名前           | アクション                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| デッキ変更    | 現在選択されているカードを別のデッキに移動します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| 期限設定   | カードを復習カードに変更し、特定の日付に期限を設定します。学習スケジュールが中断された場合に、数日前後にカードを移動するのに便利です。 `60-90` のような範囲を入力すると、選択したカードは現在から60日から90日後に期限が設定されます。新しいカードは同じ遅延時間で間隔が設定されますが、復習は現在の間隔を変更せずに再スケジュールされます（範囲の末尾に '!' を含めると例外です）。 （手動でカードをスケジュールする場合、回答時間は記録されません。スケジュールは復習の外でも実行できるため、Ankiはその時点でどのカードが表示されるかを認識していません。）                                                                                                                                                                                                                                                                                                                                                                                                                              |
| 忘却         | 現在選択されているカードを新しいキューの末尾に移動します。既存の復習履歴は保持されます。バージョン2.1.50以降では、元のカード位置を復元するオプションと、カードの遅延と繰り返しカウンターをリセットするオプションがあります。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| 位置変更     | 新しいカードが表示される順序を変更します。[table](#カード ノートテーブル) セクションで説明されているように、_due_ 列を有効にすることで既存の位置を確認できます。複数のカードが選択されている場合、位置変更コマンドは順番に各カードに増加する番号を適用します。デフォルトでは、各カードごとに番号が1ずつ増加しますが、"step" 設定を変更することで調整できます。 **既存のカードの位置をシフトする** オプションを選択すると、現在存在するカードの間にカードを挿入し、現在存在するカードを分離します。たとえば、5つのカードがあり、1と2の間に3、4、5を移動したい場合、この設定を選択すると、カードの順序は1、3、4、5、2になります。一方、このオプションをオフにすると、1と2は同じ位置番号を取得します（したがって、同じ番号のカードのうちどのカードが最初に表示されるかは予測できません）。有効にすると、より高い位置のカードは変更され、変更されたカードは次回同期時に送信する必要があります。 |
| 一時停止の切り替え | 選択したすべてのカードの一時停止を切り替えます。現在のカードが一時停止されているかどうかによって、選択したカードの一時停止が解除されるかどうかが決まります。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| フラグ           | 選択したすべてのカードのフラグを切り替えます。現在のカードに選択したフラグが追加されるか削除されるかは、フラグの状態によります。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 情報           | 現在のカードに関するさまざまな情報を表示します。復習履歴を含む。詳細については、[Card Info](stats.md#カード情報) を参照してください。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

### 移動

このメニューは、ブラウザのさまざまな部分にキーボードショートカットを提供し、カードリストを上下に移動するためのものです。

## 検索と置換

このダイアログでは、ノートのテキストを置換することができます。上記の説明にあるように、ツールバーやテーブルのコンテキストメニューから利用できます。

最初の入力フィールドは、置換されるテキストです。2番目のフィールドは、置換後のテキストです。次に、Ankiがテキストを置換する場所を指定するドロップダウンメニューがあります：ノートのタグ（Anki 2.1.45+が必要）、すべてのフィールド、または特定のフィールドのみ（選択したノートに属するフィールドのみがリストされます）。

デフォルトでは、選択したノートのみが影響を受けます。この制限を解除したい場合は、「選択したノートのみ」のチェックボックスを外すことができます（Anki 2.1.45+が必要）。

正規表現オプションを使用すると、複雑な置換を行うことができます。例えば、次のようなテキストがフィールドにあるとします：

    <img src="pic.jpg" />

次の設定を使用します：

![検索と置換ダイアログ](media/find_and_replace.png)

（Anki 2.1.28以前のバージョンでは、`${1}` を `\1` に置き換える必要があります。）

すると、フィールドの内容は次のように変わります：

    pic.jpg

正規表現についての詳しい説明は、このドキュメントの範囲外です。ウェブ上にはいくつかの構文ガイドがあります：

- Anki 2.1.28+の場合、<https://docs.rs/regex/latest/regex/index.html#syntax>を参照してください。
- 古いAnkiバージョンの場合、<http://docs.python.org/library/re.html>を参照してください。

## 重複の検索

**ノート > 重複を検索** オプションを使用して、同じ内容のノートを検索することができます。ウィンドウを開くと、Ankiはすべてのノートタイプを調べ、すべての可能なフィールドのリストを表示します。_Back_ フィールドで重複を検索したい場合は、リストから選択して **検索** をクリックします。

デフォルトでは、指定したフィールドを持つすべてのノートタイプで検索されます。これは、手動でカードを追加するときの重複チェックとは異なり、単一のノートタイプに限定されません。

**オプションフィルター**テキストボックスを使用すると、Ankiが重複を検索する範囲を絞り込むことができます。例えば、「French Vocab」と「French Verbs」のノートタイプでのみ重複を検索したい場合は、次のように入力します：

    "note:french vocab" または "note:french verbs"

または特定のデッキでのみ重複を検索したい場合は、次のように入力します：

    "deck:myDeck"

検索の構文は、ブラウザで検索するときと同じです。詳細については、[検索](searching.md)を参照してください。

検索結果リストのリンクをクリックすると、そのセット内の重複したノートが表示されます。検索結果が多数の重複を示す場合は、代わりに **重複をタグ付け** ボタンをクリックすることをお勧めします。これにより、すべての一致するノートに _duplicate_ タグが付けられます。その後、ブラウザでこのタグを検索し、同じ画面からすべてを処理することができます。



<!--

# Browsing



The Browse window allows you to search through your cards and notes, and edit
them. It is opened by clicking **Browse** in the main window, or by pressing
<kbd>B</kbd>. It is comprised of three sections: the _sidebar_ on the
left, the _card/note table_ on the top right, and the _editing area_ on the bottom
right. By positioning the mouse between two sections, it is possible to click
and drag to expand one section and shrink the other.

## Table Modes

![Table Modes](media/browser_table_modes.png)

Anki 2.1.45+ offers two modes: either cards or notes are shown in the data table.
You can change the current mode by clicking the switch at the top, to the left
of the search area, or pressing <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd> or
<kbd>Cmd</kbd>+<kbd>Opt</kbd>+<kbd>T</kbd>. The switch also indicates if **C**ards
or **N**otes are currently shown.

**Note**: For the sake of simplicity, this manual generally assumes the Cards
mode to be the active one. Whenever selecting/finding/etc. "cards" is mentioned,
the reader may substitute it for "cards or notes depending on the active mode".

## Sidebar

The _sidebar_ on the left allows quick access to common search terms. On Anki
2.1.45+, it also provides a searchbar, facilities to edit tags and decks, and a
choice of two different tools, which are discussed in the following sections.
You can switch tools using the toolbar at the top of the sidebar or the shortcuts
<kbd>Alt</kbd>+<kbd>1</kbd>/<kbd>2</kbd>.

### Search Tool

![Search Tool](media/browser_search_tool.png)

With this tool, the sidebar behaves as in previous versions: Clicking on an item
will search for it.

You can hold down <kbd>Ctrl</kbd> (<kbd>Command</kbd> on Mac) while clicking in
order to append the clicked item to the current search with an AND condition,
instead of starting a new search. If you wanted to show _learning_ cards that were
also in the German deck for instance, you could click on "Learning",
then <kbd>Ctrl</kbd>-click on "German".

You can hold down <kbd>Shift</kbd> to create an OR search instead of an AND. For
example, you could click one deck, then <kbd>Shift</kbd>-click another to show
cards from either of the decks in the same view.

You can hold down <kbd>Alt</kbd> (<kbd>Option</kbd> on Mac) in order to reverse the
search (prepend a `-`): for example, to show all cards in a current deck that
do _not_ have a certain tag. <kbd>Alt</kbd>/<kbd>Option</kbd> can be combined with
either <kbd>Ctrl</kbd> or <kbd>Shift</kbd> (e.g. clicking with <kbd>Ctrl</kbd>+<kbd>Alt</kbd>
will result in adding a new search term that is negated).

On Anki 2.1.39+, you can also hold down both <kbd>Ctrl</kbd> and
<kbd>Shift</kbd> together when clicking a search term to replace all occurrences of the
same kind of search with the new one.
Let's say you had previously typed in a complicated search expression like
`deck:Swahili (is:due or tag:important)`
and now want to perform the same search for your Urdu deck. You can hold down
<kbd>Ctrl</kbd>+<kbd>Shift</kbd> while clicking the Urdu deck in the sidebar to obtain the
following search expression:
`deck:Urdu (is:due or tag:important)`.

### Selection Tool

![Selection Tool](media/browser_selection_tool2.png)

The Selection tool allows for selecting multiple items at the same time by holding down <kbd>Ctrl</kbd>
or <kbd>Shift</kbd> while clicking. It also enables drag-and-drop to reorder decks and
tags.

Here is an example: Say you have the tags `Math`, `Calculus`, and `Algebra`.
Click on the `Calculus` tag, then <kbd>Ctrl</kbd>-click on the `Algebra` tag. Now both
tags are selected, click and drag any of the two onto the `Math` tag to make them
both children of this tag. Behind the scene, Anki has renamed the two tags to
`Math::Calculus` and `Math::Algebra` respectively and updated your notes accordingly.

Another use case for selecting multiple items is searching: If you right-click on
a selection of items, you can choose **Search &gt; All/Any Selected**. This
can be combined with keyboard modifiers as described in [Search Tool](#search-tool)
to append the resulting search to the current search.

### Saved Searches

If you regularly search for the same thing,
you can save the current search by right-clicking the topmost item in the sidebar,
choosing “Save Current Search” and typing in a name.
You can also drag and drop any sidebar item onto this area to add an equivalent
saved search, effectively pinning it at the top.

### Editing Items

You can delete or rename tags, decks, and saved searches directly from the sidebar,
from the right-click menu, or by using a shortcut key (<kbd>Del</kbd> and
<kbd>F2</kbd> on Windows). Deletion even works for multiple items at once
(see [Selection Tool](#selection-tool)).

### Finding Items

To find a certain item in the sidebar tree, type part of its name into the searchbar
at the top to temporarily hide all items not matching the search.

## Search Box

Above the card list is a search box. You can type in various things
there to search for cards. For information on the search syntax,
see [Searching](searching.md).

## Card/Note Table

The table's rows represent cards or notes that match the current search.
When you click on a row, the corresponding note will be shown in the bottom section.

### Rows

If you drag the mouse or hold <kbd>Ctrl</kbd> or <kbd>Command</kbd> to select multiple
rows, the editor will be temporarily hidden. Various operations (such as
changing the deck) can operate on multiple cards or notes at once, independent
of the active mode. Therefore in Cards mode, a note is considered to be selected
if any of its cards is selected, and in Notes mode, a card is considered to be selected
if its note is selected.

Other operations (like showing card information) only operate on a single card
or note. This is called the _current_ card or note, which is usually the one that
was last selected or clicked.
In Cards Mode, again, the current note is the note of the current card and in Notes
mode, the current card is the first card of the current note.

The background colour will change depending on the card and note. In Cards mode,
the first match will be used:

1. if the card is **flagged**, use the flag colour,
2. if the card is **suspended**, yellow,
3. if the card's note is **marked**, purple.

In Notes mode, colour is only applied to marked notes.\
For more information about marked notes and suspended cards, see [Editing and More](studying.md#editing-and-more).

### Columns

The columns are configurable: right click on one (or <kbd>Ctrl</kbd>-click on a
Mac) to choose which columns you'd like to see.
You can drag columns to reorder them. Clicking on a column will sort by that column;
click again to reverse the sort order. Note that you cannot sort by the Question
and Answer columns.

All columns are available for both [Cards and Notes mode](#table-modes)
but sometimes with slightly different names and data. The following table lists
the behaviours for both modes.



| Column          | Cards mode                                                                                                                                                                                                                             | Notes mode                                                                                                                                                                                                     |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Answer          | The back side of the card in one line with the question stripped. You can also choose a [custom format](templates/styling.md#browser-appearance) in the card type editor instead.                                                      | The same as in Cards mode, only for the first card of the note.                                                                                                                                                |
| Card(s)         | The name of the card's template.                                                                                                                                                                                                       | The number of cards the note has.                                                                                                                                                                              |
| Card Modified   | The last time changes were made to the card (e.g. when you reviewed the card and the review history and interval were updated).                                                                                                        | The last time changes were made to one of the note's cards.                                                                                                                                                    |
| Created         | The same as in Notes mode for the card's note.                                                                                                                                                                                         | The date the note was created.                                                                                                                                                                                 |
| Deck            | The name of the deck the card is in.                                                                                                                                                                                                   | The number of different decks the note's cards are in, or the deck name if all cards are in the same deck.                                                                                                     |
| Due             | The due date for cards in review or (re)learning, and the position in the new card queue for new cards. The line is wrapped in brackets if the card is suspended or buried. Sorting is done by type and only then by date or position. | The due date for the note's next due review or (re)learning card that is not suspended, buried or in a filtered deck.                                                                                          |
| (Avg.) Ease     | The card's ease if it is not new.                                                                                                                                                                                                      | The average ease for the note's cards that are not new.                                                                                                                                                        |
| (Avg.) Interval | The card's interval if the card is in review or relearning.                                                                                                                                                                            | The average interval for the note's cards that are in review or relearning.                                                                                                                                    |
| Lapses          | How often the card was rated “Again”.                                                                                                                                                                                                  | The total lapses for all cards of the note.                                                                                                                                                                    |
| Note            | The same as in Notes mode for the card's note.                                                                                                                                                                                         | The name of the note's notetype.                                                                                                                                                                               |
| Note Modified   | The same as in Notes mode for the card's note.                                                                                                                                                                                         | The last time the note (e.g. the content of a field) was edited.                                                                                                                                               |
| Question        | The front side of the card in one line. You can also choose a [custom format](templates/styling.md#browser-appearance) in the card type editor instead.                                                                                | The same as in Cards mode, only for the first card of the note.                                                                                                                                                |
| Reviews         | How often the card has been reviewed.                                                                                                                                                                                                  | The total review count for all cards of the note.                                                                                                                                                              |
| Sort Field      | The same as in Notes mode for the card's note.                                                                                                                                                                                         | The content of the note's field that is defined as the notetype's sort field. Only this one field can be displayed and sorted by. You can change the sort field by clicking **Fields...** in the editing area. |
| Tags            | The same as in Notes mode for the card's note.                                                                                                                                                                                         | The note's tags.                                                                                                                                                                                               |

## Editing Area

The bottom right area displays the note of the currently selected row. For
more information about cards and notes, see [Getting Started](getting-started.md).
For more information on formatting buttons, see [Editing](editing.md).

You can see a preview of what the currently selected card would look
like when reviewing by clicking the **Preview** button at the top of the editing area.
Note that this will not display any type-the-answer fields on your
cards, which makes it easier to preview the cards quickly.
In Notes mode, the preview is shown for the first card of the selected note.

## Menus and Actions

At the top of the browser window, you find a toolbar with various menus which in
turn offer various actions that can be performed in the browser.

### Edit


| Name                 | Action                                                                                                                                                                                                                        |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Undo                 | Revert the most recently performed operation.                                                                                                                                                                                 |
| Select All           | Select all rows displayed.                                                                                                                                                                                                    |
| Select Notes         | Show only the currently selected notes and select all rows.                                                                                                                                                                   |
| Invert Selection     | Select those rows not selected, and deselect the currently selected rows.                                                                                                                                                     |
| Create Filtered Deck | Show the [filtered deck](filtered-decks.md#creating-manually) dialog and set the current browser search as a filter. Use <kbd>Alt</kbd> / <kbd>Option</kbd> to set the second filter instead (requires scheduler version 2+). |

### Notes

Most of the following actions operate on the selected notes. They are also available through
a context menu when a selected row is right-clicked in Notes mode. In Cards mode,
they can be found in a submenu of the context menu.


| Name              | Action                                                                                                                                                                                                                                                                                                                                                     |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Add Notes         | Open the [Add](editing.md#adding-cards-and-notes) dialog.                                                                                                                                                                                                                                                                                                  |
| Create Copy       | Open a [duplicate](browsing.md#finding-duplicates) of the current note in the [editor](editing.md#adding-cards-and-notes), which can be slightly modified to easily obtain variations of your cards. By default, the duplicate card will be created in the same deck as the original.                                                                      |
| Export Notes      | Open the [Export](exporting.md) dialog.                                                                                                                                                                                                                                                                                                                    |
| Add Tags          | Add provided tags to all selected notes.                                                                                                                                                                                                                                                                                                                   |
| Remove Tags       | Enter tags and remove them from all selected notes.                                                                                                                                                                                                                                                                                                        |
| Clear Unused Tags | Remove all tags from the sidebar that are not used by any notes.                                                                                                                                                                                                                                                                                           |
| Toggle Mark       | If the current note is marked (i.e., has the _Marked_ tag), unmark all selected notes. If the current is not marked, mark all selected notes.                                                                                                                                                                                                              |
| Change Note Type   | Convert the selected notes from one type to another. For example, imagine you have a _Russian_ notetype and a _Computer_ notetype, and you accidentally added some computer-related text into a _Russian_ note. You can use this option to fix that mistake. The scheduling of cards is not affected. Changing the type of a note requires a one-way sync. |
| Find Duplicates   | Open the [Duplicates](#finding-duplicates) dialog.                                                                                                                                                                                                                                                                                                         |
| Find and Replace  | Open the [Find and Replace](#find-and-replace) dialog.                                                                                                                                                                                                                                                                                                     |
| Manage Note Types  | Open the [Notetypes](editing.md#adding-a-note-type) dialog.                                                                                                                                                                                                                                                                                                |
| Delete            | Delete all selected notes and their cards. It is not possible to remove individual cards, as individual cards are controlled by the [templates](templates/intro.md).                                                                                                                                                                                       |

### Cards

The following actions operate on the currently selected cards. They are also available through
a context menu when a selected row is rightclicked in Cards mode. In Notes mode,
they can be found in a submenu of the context menu.



| Name           | Action                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Change Deck    | Move currently selected cards to a different deck.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Set Due Date   | Turn cards into review cards, and make them due on a certain date. This can be useful for moving cards forward or back a few days when your study schedule is interrupted. Entering a range like `60-90` will make the selected cards due between 60 and 90 days from now. New cards will have their interval set to the same delay, but reviews will be rescheduled without changing their current interval, unless '!' is included at the end of the range. (Note that answer time is not recorded when manually scheduling cards, since the action can be performed even outside of review, and Anki isn’t aware of which card may or may not be shown at the time.)                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Forget         | Move currently selected cards to the end of the new queue. The existing review history is preserved. In 2.1.50+, there are options to restore the original card position, and to reset the card's lapse and repetition counters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Reposition     | Change the order new cards will appear in. You can find out the existing positions by enabling the _due_ column, as described in the [table](#cardnote-table) section above. If you run the reposition command when multiple cards are selected, it will apply increasing numbers to each card in turn. By default the number increases by one for each card, but this can be adjusted by changing the "step" setting. The **Shift position of existing cards** option allows you to insert cards between currently existing ones, pushing the currently existing ones apart. For instance, if you have five cards and you want to move 3, 4, and 5 between 1 and 2, selecting this setting would cause the cards to end up in the order 1, 3, 4, 5, 2. By contrast, if you turn this option off, 1 and 2 will get the same position number (and it will thus be unpredictable which of the cards with the same number comes up first). Please note that when enabled, any card with a higher position will be modified, and all of those changed cards will need to be sent the next time you sync. |
| Toggle Suspend | [Suspend](studying.md#editing-and-more) or unsuspend all selected cards, depending on whether the current card is suspended or not.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Flag           | Toggle the flags of all selected cards. Whether a flag is added or removed depends on whether the current card has the chosen flag.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Info           | Show various information about the current card, including its review history. For more information, see [Card Info](stats.md#card-info).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

### Go

This menu exists to provide keyboard shortcuts to jump to various
parts of the browser, and to go up and down the card list.

## Find and Replace

This dialog allows for replacing text on notes. As described above, it is available
from the toolbar and the table's context menu.

The first input field is for the text that is going to be replaced, the second
one for the replacement. Next, there is a dropdown menu that allows you to specify
where Anki should look for text to replace: in a note's tags (requires Anki 2.1.45+),
in all fields, or just in a specific field (only fields belonging to a selected
note will be listed).

By default, only selected notes will be affected. If you want to lift that
restriction, you can untick the "selected notes only" checkbox (requires Anki 2.1.45+).

The regular expression option allows you to perform complex replacements.
For example, assume there is the following text in a field:

    <img src="pic.jpg" />

We use these settings:

![Find and Replace dialog](media/find_and_replace.png)

(Note that on Anki versions prior to 2.1.28, you would need to replace `${1}`
with `\1`.)

Then the assumed field content will change to:

    pic.jpg

A full discussion on regular expressions is outside the scope of this document.
There are a number of syntax guides available on the web:

- For Anki 2.1.28+, see <https://docs.rs/regex/latest/regex/index.html#syntax>.
- For older Anki versions, see <http://docs.python.org/library/re.html>.

## Finding Duplicates

You can use the **Notes > Find Duplicates** option to search for notes that
have the same content. When you open the window, Anki will look at all
of your note types and present a list of all possible fields. If you
want to look for duplicates in the _Back_ field, you’d select it from
the list and then click **Search**.

By default, it will search in all note types that have the field you provided.
This differs from the duplicate check when you add cards manually, which
is limited to a single note type.

The **Optional filter** text box allows you to narrow down where Anki will
look for duplicates. If you only want to search for duplicates in the
"French Vocab" and "French Verbs" note types, you would enter:

    "note:french vocab" or "note:french verbs"

Or you might want to look only for duplicates in a particular deck, so
you could use:

    "deck:myDeck"

The search syntax is the same as used when searching in the browser.
For more information, see [Searching](searching.md).

You can click one of the links in the search results list to display the
duplicate notes in that set. If the search brings up a large number of
duplicates, you may wish to instead click the **Tag Duplicates** button,
which will tag all matching notes with _duplicate_. You can then search
for this tag in the browser and handle them all from the same screen.

-->