# デッキオプション

<!-- toc -->

デッキオプションは主にAnkiがカードをスケジュールする方法を制御します。Ankiの使い方に慣れるために、最初の数週間はデフォルト設定のままにしておくことをお勧めします。オプションを変更する前に、オプションの内容を理解していることを確認してください。間違った設定をすると、Ankiの効果が減少する可能性があります。

デッキオプションにアクセスするには、次の方法があります：

- `デッキ`画面で歯車アイコンをクリックします。
- `デッキ`画面でデッキを選択し、画面下部の`オプション`をクリックします。
- 復習モード中に`その他` > `オプション`をクリックします。
- 復習モード中に`o`キーを押します。

このページでは、v2またはv3スケジューラが有効になっているAnki 2.1.45+で表示されるオプションについて説明します。古いバージョンでは、一部のオプションが利用できないか、別のセクションに表示されることがあります。Anki 2.1.50+ではv1スケジューラはサポートされていないことに注意してください。まだv2またはv3に更新していない場合、2.1.50+でカードを復習しようとすると更新を促されます。

デッキオプションの詳細については、以下を参照してください：

- [デッキオプションの説明](https://forums.ankiweb.net/t/deck-options-explained/213)
- [メンタルマップでのデッキオプション](https://forums.ankiweb.net/t/deck-options-in-a-mental-map/15757)

## プリセット

Ankiでは、異なるデッキ間でオプションを共有することができ、多くのデッキのオプションを一度に更新するのが簡単になります。このために、オプションは_プリセット_にグループ化されています。デフォルトでは、新しく作成されたデッキはすべて同じプリセットを使用します。

1つのデッキの設定を変更したいが、他のデッキの設定は変更したくない場合は、デッキオプションウィンドウの右上にある矢印アイコンをクリックします。オプションは次のとおりです：

- **保存**: デッキオプション画面を開いてから行ったすべての変更を保存します。
- **追加**: デフォルトのオプションで新しいプリセットを追加します。
- **クローン**: 現在のプリセットをクローンします。これは、特定のオプションだけを変更し、他のオプションはそのままにしておきたい場合に便利です。
- **名前変更**: 現在のプリセットの名前を変更します。
- **削除**: 現在のプリセットを削除します。次の同期が一方向同期になることが必要です。
- **すべてのサブデッキに保存**: _保存_と同様ですが、選択したプリセットを現在選択されているデッキのすべてのサブデッキにも割り当てます。

デッキオプションは遡及的ではありません。例えば、カードを失敗した後の遅延を制御するオプションを変更した場合、そのオプションを変更する前に失敗したカードは古い遅延を持ち、新しい遅延にはなりません。

## サブデッキ

デッキにサブデッキがある場合、それぞれのデッキに異なるプリセットを割り当てることができます。Ankiがカードを表示する際、カードがどのサブデッキにあるかを確認し、そのデッキのオプションを使用します。ただし、いくつかの例外があります：

- 新しいカード/日および復習/日の[制限](#日次制限)は、選択したスケジューラのバージョンによって異なります。
- v3スケジューラの[表示順序](#表示順序)オプションは、現在のカードのデッキではなく、学習するために選択したデッキから取得されます。

例えば、次のようなコレクションがあるとします：

    - デッキA（プリセット1）
      - デッキA::サブデッキB（プリセット2）
        - カードB1
        - カードB2

プリセット1と2は、次の2つの例外を除いて同一です：

- プリセット1：
  - 新しいカード - 学習ステップ：1分 10分
  - 表示順序 - 新しいカード/復習の優先順位：復習と混合
- プリセット2：
  - 新しいカード - 学習ステップ：20分 2時間
  - 表示順序 - 新しいカード/復習の優先順位：復習の後に表示

デッキAを学習することを選択した場合：

- すべての新しいカードの学習ステップは1分 10分になります（プリセット1が適用されます）
- すべての新しいカードは復習と混合されます（プリセット1が適用されます）

サブデッキBを学習することを選択した場合：

- すべての新しいカードの学習ステップは20分 2時間になります（プリセット2が適用されます）
- すべての新しいカードは復習の後に表示されます（プリセット2が適用されます）

## 日次制限

### 新しいカード/日

毎日プログラムを開くたびに導入される新しいカードの数を制御します。制限より少ないカードを学習したり、1日を逃したりしても、翌日にはカウントがリセットされ、制限に戻ります。カウントは累積しません。

デッキがネストされている場合（例：親、親::子、親::子::孫）、制限の適用方法はスケジューラのバージョンによって異なります。

- v1は、どのデッキをクリックしても親の制限を子に適用します。
- v2は、新しいカードに関してはv1と同様に動作します。復習に関しては、クリックしたデッキの制限のみが適用されます。
- v3は、クリックしたデッキとその内部のデッキの制限を尊重します。クリックしたデッキの上位の親デッキの制限は無視されます。

詳細については、[v3スケジューラ](https://shigeyukey.github.io/Anki-faqs-jp/the-2021-scheduler.html#日時制限)のページをご覧ください。

新しいカードを学習すると、一時的に1日に必要な復習の数が増加します。新しく学習した素材は、繰り返しの間隔が大幅に増加する前に何度も繰り返す必要があるためです。毎日20枚の新しいカードを一貫して学習している場合、1日の復習数は約200枚になると予想されます。毎日導入する新しいカードの数を減らすか、新しいカードの表示をオフにして復習の負担が減るまで待つことで、必要な復習数を減らすことができます。多くのAnkiユーザーは、プログラムを使い始めた最初の数日間で何百枚もの新しいカードを興奮して学習し、その後必要な復習に圧倒されることがあります。

### 1日の最大復習数

毎日表示する復習の上限を設定できます。この制限に達すると、Ankiはその日の復習カードをこれ以上表示しません。たとえ待機中のカードがあってもです。一貫して学習する場合、この設定は時折発生する復習カードのピークを平準化し、1週間の休暇後にAnkiに戻ったときに心臓発作を防ぐのに役立ちます。このオプションによって復習が隠された場合、祝福画面にメッセージが表示され、時間があれば制限を増やすことを検討するよう提案されます。

[v3スケジューラ](https://shigeyukey.github.io/Anki-faqs-jp/the-2021-scheduler.html#日次制限)およびv1スケジューラでは、新しいカードと同様に、親/選択されたデッキによってカウントが影響を受けます。

v2スケジューラでは、制限は選択したデッキからのみ取得され、親デッキや子デッキの制限は無視されます。

v3スケジューラには、1日以上の遅延がある学習カードも復習カウントに含まれるため、これらの学習カードも日次制限の対象となります。

### 新しいカードが復習制限を無視

[v3スケジューラ](https://shigeyukey.github.io/Anki-faqs-jp/the-2021-scheduler.html##日次制限)を使用している場合、新しいカードのカウントはデフォルトで復習カウントによって制限されることに注意してください。復習制限が200に設定されていて、190の復習が待機している場合、最大で10枚の新しいカードが導入されます。復習制限に達した場合、新しいカードは表示されません。復習のバックログがあり、それでも新しいカードを導入したい場合は、復習を一時停止するか、復習制限を増やすことで可能です。しかし、遅れを取り戻すまで新しいカードの導入を控えることをお勧めします。遅れているときに新しいカードを導入すると、バックログがさらに悪化するだけです。

Anki 2.1.61以降、この機能はオプションであり、デッキオプション画面からグローバルに無効化できます。

### デッキごとの日次制限

バージョン2.1.55から、異なるデッキやサブデッキに対して同じプリセットを使用し、それぞれにカスタマイズされた制限を設定することが可能になりました。これにより、その目的のためだけにクローンプリセットを作成する必要がなくなり、多くのネストされたデッキがある場合にサブデッキにカスタム制限を設定するのが容易になります。

オプションは次のとおりです：

- プリセット: このプリセットを使用するすべてのデッキで制限が共有されます。
- このデッキ: 制限はこのデッキに固有のものです。
- 今日のみ: このデッキの制限を一時的に変更します。

## 新しいカード

このセクションの設定は、新しいカードと初期の[学習](studying.md#学習-再学習カード)モードのカードにのみ影響します。カードが卒業（つまり、このカードに対する学習ステップがなくなる）すると、[復習カード](studying.md#復習カード)になり、このセクションの設定は適用されなくなります。

### 学習ステップ

学習の繰り返し回数とその間の遅延を制御します。1つ以上の遅延をスペースで区切って入力する必要があります。復習中に`良い`を押すたびに、カードは次のステップに進みます。

例えば、学習ステップが**1分 10分 1日**であるとします。

- `再度`を押すと、カードは最初のステップに戻り、約1分後に再度表示されます。
- 新しいカードや`再度`と答えたカードに`良い`を押すと、カードは次のステップに進み、約10分後に再度表示されます。
- 10分のステップの後にカードに`良い`を押すと、翌日まで遅延されます。
- 翌日にカードに`良い`を押すと、学習を終了し（つまり、卒業し）、復習カードになります。_卒業間隔_で設定された遅延後に再度表示されます。

他に学習するものがない場合、Ankiはデフォルトで最大20分前にカードを表示します。先読みする時間の量は[設定](preferences.md)で構成可能です。

ステップの動作についての詳細は、[学習](studying.md#学習-再学習カード)セクションをご覧ください。

#### 日付の境界

Ankiは、小さなステップと[日付の境界を越える](./preferences.md#復習)ステップを異なる方法で処理します。小さなステップの場合、遅延が経過するとすぐにカードが表示され、復習のような他の待機カードよりも優先されます。これは、要求された遅延にできるだけ近いタイミングでカードに回答できるようにするためです。対照的に、間隔が日付の境界を越える場合、それは自動的に日単位に変換されます。

### 卒業間隔

学習カードで「良い」と回答してステップがなくなった後、カードを再び復習カードとして見るまでの日数の遅延を指します。これは、学習カードが復習カードになった後の最初の間隔を意味します。前のセクションの例を参照してください。

### 簡単間隔

学習カードで「簡単」と回答してから、初めて復習モードでカードを見るまでの遅延を指します。

「簡単」ボタンは、学習カードを即座に復習カードに変え、設定した遅延を割り当てます。これは常に_卒業間隔_と同じかそれ以上であるべきで、通常は数日長く設定されます。

### 挿入順序

Ankiが新しいカードをデッキにランダムに追加するか、順序通りに追加するかを制御します。このオプションを変更すると、Ankiは現在のオプショングループを使用してデッキを再ソートします。デフォルトでは、学習時に期限が早いカードが最初に表示されます。このオプションを変更すると、新しいカードの既存の位置が自動的に更新されます。

ランダム順序モードの注意点：多くの新しいカードを復習し、その後さらに新しいカードを追加すると、新しく追加された素材が、既にデッキにあった新しいカードよりも統計的に早く表示される可能性が高くなります。例えば、ランダム順序で100枚のカードがあり、最初の50枚を復習した場合、新しく追加されたカードは依然として1-100の位置に割り当てられますが、最初の50枚を既に復習しているため、新しく追加されたカードが早く表示される可能性が高くなります。これを修正するには、順序モードに変更してから再度ランダムモードに戻して再ソートを強制します。

ランダム順序を選択すると、Ankiはノートをランダム化し、特定のノートのカードを近くに保ちます。特定のノートのカードは、そのカードタイプが表示される順序で表示されるため、兄弟カードが一貫して導入されます。そうしないと、あるノートはすべてのカードが導入され、他のノートは1枚か2枚しか導入されない状態になる可能性があります。詳細については、以下の「関連カードを埋める」および「表示順序」セクションを参照してください。

## 忘却

復習カードを忘れた場合、それは「忘却」したと言われ、そのカードは再学習する必要があります。忘却した復習のデフォルトの動作は、間隔を1にリセットし（つまり、明日が期限になる）、10分後に再学習キューに入れることです。この動作は、以下のオプションでカスタマイズできます。

### 再学習ステップ

「学習ステップ」と同じですが、忘れた復習用です。カードに失敗した場合（`再度`を押す）、カードは再学習フェーズに入り、再び復習カードになる前にすべての再学習ステップを通過する必要があります。あるいは、カードに`簡単`を押すこともできます。

ステップを空白のままにすると、カードは再学習をスキップし、新しい復習遅延が割り当てられます。

### 最小間隔

カードが再学習を終えた後に待つべき最小の日数を指定します。デフォルトは1日で、再学習が終了すると翌日に再び表示されます。

### リーチ

Ankiがリーチを処理する方法を制御します。詳細については、[リーチ](leeches.md)セクションを参照してください。

## 表示順序

このセクションのオプションは、現在表示されているカードのデッキではなく、学習するために選択したデッキから取得されます。

このセクションは、[v3スケジューラ](https://shigeyukey.github.io/Anki-faqs-jp/the-2021-scheduler.html)が有効になっている場合にのみ利用可能です。

表示順序に関するさらなる情報は、[学習セクション](studying.md#表示順序)で確認できます。

### 新しいカードの収集順序

Ankiが各サブデッキからカードを収集する方法を制御します。オプションは次のとおりです：

- デッキ: 各デッキから順番にカードを収集し、上から始めます。各デッキのカードは昇順で収集されます。選択したデッキの日次制限に達すると、すべてのデッキがチェックされる前に収集が停止することがあります。この順序は大規模なコレクションで最も高速であり、上位に近いサブデッキを優先することができます。

  デッキ/サブデッキは常にアルファベット順に並べられるため、表示順序を制御するために001のような数値プレフィックスを付けることができます。また、アイテムを上部または下部に配置するために`_`や`~`をプレフィックスとして使用することもできます。

  位置順序は最初は上記の「挿入順序」設定に依存しますが、手動でカードを[再配置](https://docs.ankiweb.net/browsing.html#cards)することもできます。

- デッキ、次にランダムノート: 各デッキから順番にカードを収集し、上から始めます。各デッキのカードはランダムに収集されます。

- 昇順位置: 位置（期限番号）でカードを昇順に収集します。通常、最も古く追加されたカードが最初に表示されます。

- 降順位置: 位置（期限番号）でカードを降順に収集します。通常、最新に追加されたカードが最初に表示されます。

- ランダムノート: ランダムに選択されたノートのカードを収集します。兄弟カードの埋め込みが無効になっている場合、1つのセッションでノートのすべてのカードを見ることができます（例：表->裏カードと裏->表カードの両方）。

- ランダムカード: 完全にランダムにカードを収集します。

### 新しいカードのソート順序

新しいカードが**収集された後**にどのようにソートされるかを制御します。オプションは次のとおりです：

- カードタイプ: カードタイプ番号の順にカードを表示します。兄弟カードの埋め込みが無効になっている場合、すべての表→裏カードが裏→表カードよりも先に表示されます。これにより、同じノートのすべてのカードが同じセッションで表示されますが、あまり近くには表示されません。

- 収集順序: カードが収集された順序通りに表示します。兄弟カードの埋め込みが無効になっている場合、通常、ノートのすべてのカードが連続して表示されます。

- カードタイプ、次にランダム: カードタイプと同様ですが、各カードタイプ番号のカードをシャッフルします。最も古いカードを収集するために昇順位置を使用する場合、この設定を使用してそれらのカードをランダムな順序で表示できますが、同じノートのカードがあまり近くに表示されないようにします。

- ランダムノート、次にカードタイプ: ノートをランダムに選択し、その後すべての兄弟カードを順番に表示します。

- ランダム: 収集されたカードを完全にシャッフルします。

### 新しいカード/復習の優先順位

新しいカードを復習と混ぜるか、復習の前または後に表示するかを制御します。

### 日をまたぐ学習/復習の優先順位

1日以上の遅延がある学習カードを復習と混ぜるか、復習の前または後に表示するかを制御します。学習カードは復習よりも難しい傾向があるため、ユーザーによっては（簡単なものを先に終わらせるために）最後に表示するか、（忘れたものを復習する時間を増やすために）最初に表示することを好む場合があります。

### 復習のソート順序

復習中に復習カードがどのようにソートされるかを制御します。オプションは次のとおりです：

- 期限日、次にランダム: デフォルトのオプションは、長く待っているカードを優先し、最新の状態にある場合や小さなバックログがある場合に推奨されます。長期間の休憩を取ったり、復習が遅れたりしている場合は、一時的にソート順序を変更することを検討してください。
- 期限日、次にデッキ: これも長く待っているカードを優先し、その後各サブデッキの復習を順番に表示します。
- デッキ、次に期限日: このオプションは、各サブデッキの復習を順番に表示します。これは一般的には推奨されません。なぜなら、同じ順序で一貫して表示されると、コンテキストに基づいて答えを推測しやすくなり、記憶が弱くなる可能性があるからです。
- 昇順間隔: 短い間隔のカードが最初に表示されるようにします。
- 降順間隔: 長い間隔のカードが最初に表示されるようにします。
- 昇順の容易さ: 最も難しいカードが最初に表示されるようにします。
- 降順の容易さ: 最も簡単なカードが最初に表示されるようにします。
- 相対的な遅延: 忘れる可能性が最も高いカードを最初に表示します。これは、大きなバックログがあり、それを処理するのに時間がかかる場合に役立ち、より多くのカードを忘れる可能性を減らすことができます。

  SM-2スケジューラを使用する場合、遅延はカードがどれだけ遅延しているかとその間隔の長さを比較して決定されます。例えば、現在の間隔が5日で2日遅延しているカードは、現在の間隔が10日で3日遅延しているカードよりも先に表示されます。

  FSRSを使用する場合、遅延は各カードの再取得可能性とデッキプリセットでの望ましい保持率に基づいて計算されます。
## タイマー

Ankiは各カードに回答するのにかかった時間を監視し、毎日どれだけの時間を勉強に費やしたかを表示します。かかった時間はスケジューリングには影響しません。

オプションは次のとおりです：

- 最大回答時間（秒）: デフォルトの制限は60秒です。それ以上かかると、Ankiはコンピュータから離れたか、気が散ったとみなし、記録された時間を60秒に制限します。これにより、不正確な統計が出ないようにします。質問が表示されてから回答ボタンを押すまでに一貫して60秒以上かかる場合、この制限を引き上げるか、理想的にはカードを簡単にすることを検討してください。
- 回答タイマーを表示: 復習スクリーンで、各カードを復習するのにかかっている秒数をカウントするタイマーを表示します。
- 回答時にタイマーを停止: 回答を表示したときにタイマーを停止するかどうかを設定します。

## 自動進行

Anki 23.12以降が必要です。自動進行を使用すると、回答を自動的に表示したり、次のカードに移動したりできます。使用するには、「質問を表示する秒数」および/または「回答を表示する秒数」にゼロ以外の時間を設定する必要があります。その後、復習スクリーンで`More`ボタンから自動進行アクションを使用して進行を開始します。

## 埋め込み

Ankiがカードを収集する際、まず日内学習カード、次に日間学習カード、次に復習、最後に新しいカードを収集します。これにより、埋め込みの動作が影響を受けます：

- すべての埋め込みオプションが有効になっている場合、そのリストで最も早く来る兄弟カードが表示されます。例えば、復習カードは新しいカードよりも優先して表示されます。
- リストの後半にある兄弟カードは、前半のカードタイプを埋めることはできません。例えば、新しいカードの埋め込みを無効にして新しいカードを学習すると、日間学習カードや復習カードを埋めることはなく、同じセッションで復習兄弟カードと新しい兄弟カードの両方を見ることができます。

オプションは次のとおりです：

- 新しい兄弟カードを埋める: 同じノートの他の新しいカード（例：逆カード、隣接する穴埋め問題）が翌日まで遅延されるかどうかを設定します。
- 復習兄弟カードを埋める: 同じノートの他の復習カードが翌日まで遅延されるかどうかを設定します。
- 日間学習兄弟カードを埋める: 間隔が1日以上の同じノートの他の学習カードが翌日まで遅延されるかどうかを設定します。

カードの埋め込みに関する詳細は、マニュアルの[このセクション](./studying.md#兄弟カードと埋める)を参照してください。

## オーディオ

デフォルトでは、Ankiはカードの表と裏で自動的にオーディオを再生します。_オーディオを自動再生しない_にチェックを入れると、`r`キーまたは`F5`キーでオーディオを再生するまで、Ankiはオーディオを再生しません。

_オーディオ再生時に常に質問側を含める_は、回答が表示されている間にオーディオを再生する際に、質問側のオーディオも再生するかどうかを制御します。回答を表示する際の動作については、[このセクション](templates/fields.md#特殊フィールド)を参照してください。

## 高度な設定

### FSRS

[Free Spaced Repetition Scheduler (FSRS)](https://github.com/open-spaced-repetition/fsrs4anki)は、Ankiの従来のSuperMemo 2 (SM2)スケジューラの代替です。忘れる可能性が高い時期をより正確に判断することで、同じ時間でより多くの素材を覚えるのに役立ちます。この設定はすべてのデッキプリセットで共有されます。

FSRSは現在、高度な設定セクションにあります。これは、Ankiの23.10リリースで統合されたばかりだからです。この設定を有効にすると、新しいオプションが利用可能になり、「卒業間隔」や「簡単ボーナス」などのSM-2特有の設定が非表示になります。

**有効にする前に**

- すべてのAnkiクライアントがFSRSをサポートしていることを確認してください。Anki 23.10、AnkiMobile 23.10、およびAnkiWebはすべてサポートしています。AnkiDroidは2.17alpha3+でサポートしています。クライアントのいずれかがサポートしていない場合、正しく動作しません。
- 以前にFSRSの「カスタムスケジューリング」バージョンを使用していた場合、FSRSを有効にする前にカスタムスケジューリングセクションをクリアしてください。

#### FSRSオプション

**望ましい保持率**

望ましい保持率は、カードを復習する際にそれを覚えている可能性を制御します。デフォルト値の0.9は、カードが再び復習されるときに90%の確率で覚えているようにスケジュールします。

以下のグラフは、この値を調整することで作業量にどのような影響があるかを示しています：

<img src="media/FSRS_retention.png" width="600">

注意すべき点が2つあります：

- 望ましい保持率が1.0に近づくと、カードを復習する頻度が急激に増加します。例えば、あるカードを100日後に90%の確率で覚えているとします。望ましい保持率が0.95の場合、47日後に復習する必要があります（約2倍の頻度）。0.97の場合、遅延は27日（約3.7倍の頻度）になります。0.99の場合、9日ごとに復習する必要があります（デフォルトの10倍以上の頻度）。

- 望ましい保持率が低下すると、より多くのカードを忘れることになり、それらのカードを再び復習する必要があります。最終的には、忘れたカードが作業量に対してより多くの負担をかけるようになり、左側のグラフで作業量が増加するのがわかります。また、頻繁に素材を忘れることはモチベーションを低下させることも覚えておいてください。

これらの理由から、この数値を調整する際には慎重になることをお勧めし、0.85から0.95の間に保つことを推奨します。

**SM-2保持率**

FSRSに切り替える前の実際の保持率が0.9と大きく異なる場合、この値を調整することで、復習記録が欠落しているカードに遭遇した際にAnkiが記憶状態をより正確に推定できるようになります。復習記録は、スペースを空けるために明示的に削除しない限り通常は欠落しないため、ほとんどのユーザーはこの設定を調整する必要はありません。

**FSRSパラメータ**

FSRSパラメータはカードのスケジューリングに影響します。手動で変更することは意図されていません。復習が1000回以上蓄積されたら、Ankiが復習履歴に基づいてパラメータを最適化できます。

**変更時のカードの再スケジュール**

このオプションは、FSRSを有効にするかパラメータを変更したときにカードの期限日が変更されるかどうかを制御します。デフォルトではカードの再スケジュールは行われません：将来の復習は新しいスケジューリングを使用しますが、作業量に即時の変化はありません。再スケジュールが有効になると、カードの期限日が変更され、多くのカードが期限になることがよくあります。そのため、**SM2から初めて切り替える際にはこのオプションを有効にすることは推奨されません**。

FSRSが作業量を変更せずにスケジュールをどのように変更するかを視覚化したい場合、次の2つの方法があります：

- 再スケジュールせずにFSRSを有効にし、間隔と安定性のグラフを比較します。間隔グラフはカードの現在の間隔を示し、安定性グラフは望ましい保持率が0.9の場合にFSRSがカードに与える間隔を示します。
- バックアップを作成し、再スケジュールを有効にしてFSRSを有効にし、将来の期限グラフを確認し、その後バックアップから元に戻すか復元します。

**FSRSパラメータの最適化**

FSRSオプティマイザーは機械学習を使用して記憶パターンを学習し、復習履歴に最適なパラメータを見つけます。これを行うには、オプティマイザーがいくつかの復習を必要とします。

復習が1000回未満の場合、「FSRSパラメータ」フィールドに既に入力されているデフォルトパラメータを使用できます。デフォルトパラメータでも、FSRSはほとんどのユーザーにとってうまく機能するはずです。

Ankiで1000回以上の復習を行ったら、`Optimize`ボタンを使用して復習履歴を分析し、記憶と学習内容に最適なパラメータを自動的に生成できます。パラメータはプリセットごとに異なるため、難易度が大きく異なるデッキがある場合は、それぞれに別々のプリセットを割り当てることをお勧めします。簡単なデッキと難しいデッキのパラメータは異なります。パラメータを頻繁に最適化する必要はなく、数ヶ月に一度で十分です。

デフォルトでは、パラメータは現在のプリセットを使用しているすべてのデッキの復習履歴から計算されます。パラメータを最適化するために使用するカードを変更したい場合は、計算前に検索を調整することもできます。

**FSRSパラメータの評価**

「FSRSパラメータの最適化」セクションの`Evaluate`ボタンを使用して、「モデルパラメータ」フィールドのパラメータが復習履歴にどれだけ適合しているかを示すメトリクスを確認できます。数値が小さいほど、復習履歴に適合していることを示します。

ログ損失（log-loss）は直感的な解釈がありません。RMSE（bins）は、カードを思い出す確率（R）の予測値と復習履歴から得られた実測値の平均差として解釈できます。例えば、RMSE=5%は、FSRSがRを予測する際に平均で5%の誤差があることを意味します。

ログ損失とRMSE（bins）は完全には相関していないため、2つのデッキが似たようなRMSE値を持っていても、ログ損失値が大きく異なる場合やその逆もあります。

**最適な保持率の計算**

この実験的なツールは、0枚のカードから始めることを前提としており、指定された期間内にどれだけの素材を保持できるかを計算しようとします。推定される保持率は入力に大きく依存し、0.9から大きく異なる場合は、毎日割り当てている時間が学習しようとしているカードの量に対して少なすぎるか多すぎることを示しています。この数値は参考として役立ちますが、望ましい保持率フィールドにコピーすることは推奨されません。

#### 学習および再学習ステップ

FSRSを使用する場合、1日以上の学習ステップは推奨されません。古いSM-2スケジューラでこれが人気だった主な理由は、学習フェーズを卒業した後にカードに繰り返し失敗すると、その容易さが大幅に低下し、「容易さ地獄」と呼ばれる状態になる可能性があったからです。これはFSRSでは問題になりません。学習ステップを1日未満に保つことで、FSRSがあなたの素材と記憶に最適なタイミングでカードをスケジュールできるようになります。もう一つの理由は、FSRSが最初の復習を最後の学習ステップよりも短い時間にスケジュールする可能性があり、`Hard`ボタンが`Good`ボタンよりも長い時間を表示することになるからです。

また、学習ステップの数を最小限に抑えることをお勧めします。証拠によれば、カードを覚えた後に同じ日に複数回繰り返しても記憶にはあまり役立たないため、その時間を他のカードや短い学習セッションに費やす方が良いです。

#### アドオンの互換性

一部のアドオンはFSRSと競合する可能性があります。一般的なルールとして、カードの間隔に影響を与えるアドオンはFSRSと一緒に使用しないでください。よく使用されるアドオンとそのFSRS互換性のリストは、[アドオンの互換性](https://github.com/open-spaced-repetition/fsrs4anki#add-on-compatibility)で確認できます。

#### 詳細

FSRSの詳細については、以下を参照してください：

- [FSRS4Anki Wiki](https://github.com/open-spaced-repetition/fsrs4anki/wiki)
- [FSRS4Anki on Github](https://github.com/open-spaced-repetition/fsrs4anki)

### 最大間隔

Ankiがカードを再表示するまでの最大時間を設定できます。デフォルトは100年ですが、保持率を高めるために追加の学習時間を費やすことをいとわない場合は、これを小さな数値に減らすことができます。

### 初期の容易さ

カードが最初に学習を卒業したときに設定される容易さを制御します。デフォルトは2.50で、カードの学習を終えた後、次の復習で`Good`と評価すると、遅延が約2.5倍になります（例：前回の遅延が10日だった場合、次の遅延は約25日になります）。その後の復習での評価に基づいて、容易さは初期値から増減することがあります。

### 簡単ボーナス

復習カードに`Easy`と評価したときに間隔に適用される追加の乗数です。デフォルト値の1.30では、`Easy`は`Good`間隔の1.3倍の間隔を与えます（例：Good間隔が10日だった場合、Easy間隔は約13日になります）。

### 間隔修正値

間隔修正値は、すべての復習に適用される追加の乗数です。デフォルトの1.00では何も変更しませんが、例えば0.80に設定すると、間隔は通常の80%のサイズで生成されます（10日の間隔が8日になります）。この乗数を使用して、Ankiがカードを表示する頻度を調整し、学習時間と保持率をトレードオフすることができます。

中程度の難易度の素材の場合、平均的なユーザーは復習に出てくる成熟カードの約90%を覚えているはずです。デッキのグラフ/統計を開き、回答ボタングラフを見て自分のパフォーマンスを確認できます。成熟保持率はグラフの右側に表示される正解率です。学習を始めたばかりの場合、まだ成熟カードがないかもしれません。新しいカードや若いカードのパフォーマンスは大きく異なることがあるため、保持率について結論を出す前に、ある程度の成熟復習を持つまで待つのが良いでしょう。

SuperMemoのウェブサイトでは、望ましい保持率に対する適切な乗数を見つける方法が提案されています。彼らの公式は次のようになります：

    log(望ましい保持率%) / log(現在の保持率%)

例えば、現在の保持率が85%で、それを90%に増やしたいとします。この場合、修正値は次のように計算されます：

    log(90%) / log(85%) = 0.65

Googleを使用して[計算する](https://www.google.com/search?q=log(90%25)+%2F+log(85%25))ことができます。

得られた65%を間隔修正値に入力すると、時間をかけて保持率が望ましい保持率に近づくはずです。

しかし、学習に費やす時間と保持率のトレードオフは線形ではないことに注意してください。保持率を5パーセントポイント増やすためには、学習頻度を35%増やす必要があります。学習している素材が非常に重要であれば、追加の努力をする価値があるかもしれませんが、それは自分で決める必要があります。単に忘れすぎていることを心配している場合は、初期学習段階でより多くの時間を投資するか、または記憶術を使用することで、より少ない努力でより多くの成果を得ることができるかもしれません。

最後に、Ankiは新しい間隔が以前より少なくとも1日長くなるように強制します。これにより、同じ間隔で永遠に復習することがなくなります。カードを複数日にわたって1日1回繰り返すことが目標であれば、この修正値を調整するのではなく、学習モードのステップを増やすことで実現できます。

### ハード間隔

`Hard`ボタンを使用したときに適用される乗数です。このパーセンテージは前回の間隔に対する相対値です。例えば、デフォルトの1.20では、10日の間隔が12日になります。

### 新しい間隔

復習カードで`Again`ボタンを使用したときに適用される乗数です。デフォルトの0.00は、復習カードの遅延がゼロにリセットされることを意味します（その後、[最小間隔](#最小間隔)が適用されて1日になります）。

デフォルトから変更すると、忘れたカードが以前の遅延の一部を保持することが可能になります。例えば、カードの間隔が100日で、新しい間隔を0.20に設定すると、新しい間隔は20日になります。

間隔の一部を保持することは理にかなっているように思えるかもしれませんが、SuperMemoは遅延の一部を保持することが実際には[逆効果](https://supermemo.guru/wiki/Post-lapse_stability)であることを観察しています。このため、デフォルト設定のままにしておくことをお勧めします。

## カスタムスケジューリング

[このページ](https://shigeyukey.github.io/Anki-faqs-jp/the-2021-scheduler.html#アドオンとカスタムスケジューリング)をご覧ください。



<!-- # Deck Options

<!-- toc -->
<!-- 
Deck options primarily control the way Anki schedules cards. It is recommended
that you spend a few weeks with the defaults to get a feel for how Anki works
before you start adjusting options. Please make sure you understand the options
before changing them, as mistakes could reduce Anki's effectiveness.

Deck options are accessed by:

- Clicking the gear icon on the `Decks` screen.
- Selecting a deck on the `Decks` screen, and then clicking `Options`
  at the bottom of the screen.
- Clicking on `More` > `Options` while in review mode.
- Pressing `o` while in review mode.

This page describes the options shown in Anki 2.1.45+, when you have the v2 or
v3 scheduler enabled. On older versions, some options will not be available, or
will appear in a different section. Please keep in mind that the v1 scheduler
is no longer supported in Anki 2.1.50+. If you have not yet updated to v2 or v3,
you will be prompted to update when you attempt to review cards in 2.1.50+.

For more info on deck options, please check:

- [Deck Options Explained](https://forums.ankiweb.net/t/deck-options-explained/213)
- [Deck Options in a Mental Map](https://forums.ankiweb.net/t/deck-options-in-a-mental-map/15757)

## Presets

Anki allows you to share options between different decks, to make
it easy to update options in many decks at once. To do this, options are
grouped into _presets_. By default, all newly created decks use
the same preset.

If you’d like to alter the settings on one deck but not other decks, click the
arrow icon in the top right of the Deck Options window. The options are:

- **Save**: Saves all modifications you've made since opening the deck options screen.
- **Add**: Add a new preset, with the default options.
- **Clone**: Clone your current present, which is useful if you
  just want to modify certain options, keeping the rest as they are.
- **Rename** Changes the name of the current preset.
- **Delete** Deletes the current preset. This will require that the next sync is
  a one-way sync.
- **Save to all subdecks**. Like _Save_, but also assigns the selected preset to all
  subdecks of the currently selected deck.

Deck Options are not retroactive. For example, if you change an option that
controls the delay after failing a card, cards that you failed prior to
changing the option will have the old delay, not the new one.

## Subdecks

If your deck has subdecks, each deck can optionally be assigned a different preset.
When Anki shows a card, it will check which subdeck the card is in, and use the options
for that deck. There are some exceptions:

- The new cards/day and reviews/day [limits](#daily-limits) behave differently
  depending on the scheduler version you have selected.
- The [display order](#display-order) options in the v3 scheduler are taken from the
  deck you select to study, not the deck of the current card.

For example, let's say you have this collection:

    - Deck A (Preset 1)
      - Deck A::Subdeck B (Preset 2)
        - Card B1
        - Card B2

Preset 1 and 2 are identical, with two exceptions:

- Preset 1:
- New Cards - Learning steps: 1m 10m
- Display Order - New/review priority: Mix with reviews
- Preset 2:
- New Cards - Learning steps: 20m 2h
- Display Order - New/review priority: Show after reviews

If you choose to study Deck A:

- Learning steps for all new cards will be 1m 10m (preset 1 applies)
- All new cards will be mixed with reviews (preset 1 applies)

If you choose to study Subdeck B:

- Learning steps for all new cards will be 20m 2h (preset 2 applies)
- All new cards will be shown after reviews (preset 2 applies)

## Daily Limits

### New Cards/Day

Controls how many new cards are introduced each day you open the program. If you
study fewer than the limit, or miss a day, the next day the counts will be back
to your limit - they do not accumulate.

When decks are nested (e.g Parent, Parent::Child, Parent::Child::Grandchild),
the way the limits are applied depends on the scheduler version.

- v1 applies parent limits to children, regardless of which deck you click on
- v2 behaves similarly to v1 for new cards. For reviews, only the limits of
  the deck you click on are honored.
- v3 honors the limits of the deck you click on, and any decks inside it.
  Limits from parents above the deck you clicked on are ignored.

For more information, please see the [v3 scheduler](https://shigeyukey.github.io/Anki-faqs-jp/the-2021-scheduler.html#daily-limits) page.

Studying new cards will temporarily increase the number of reviews you need to
do a day, as freshly learnt material needs to be repeated a number of times
before the delay between repetitions can increase appreciably. If you are
consistently learning 20 new cards a day, you can expect your daily reviews to
be roughly about 200 cards/day. You can decrease the reviews required by
introducing fewer new cards each day, or by turning off new card display until
your review burden decreases. More than one Anki user has excitedly studied
hundreds of new cards over their first few days of using the program, and then
become overwhelmed by the reviews required.

### Maximum Reviews/Day

Allows you to set an upper limit on the number of reviews to show each day.
When this limit is reached, Anki will not show any more review cards for the
day, even if there are some waiting. If you study consistently, this setting can
help to smooth out occasional peaks in due card counts, and can save you from a
heart attack when returning to Anki after a week off. When reviews have been
hidden due to this option, a message will appear in the congratulations screen,
suggesting you consider increasing the limit if you have time.

In [the v3 scheduler](https://shigeyukey.github.io/Anki-faqs-jp/the-2021-scheduler.html#daily-limits) and
v1 schedulers, the counts are affected by parents/selected decks in the same way
as new cards.

In the v2 scheduler, the limit is taken solely from the deck you select - any
limits on its parents or child decks are ignored.

The v3 scheduler includes learning cards with a 1+ day delay in the review count,
so those learning cards will be subject to the daily limit.

### New Cards Ignore Review Limit

If using [the v3 scheduler](https://shigeyukey.github.io/Anki-faqs-jp/the-2021-scheduler.html#daily-limits),
please keep in mind that the new count is capped by the review count by default. If your
review limit is set to 200, and you have 190 reviews waiting, a maximum of 10
new cards will be introduced. If your review limit has been reached, no new
cards will be shown. If you have a backlog of reviews and still want to
introduce new cards, you can do so by suspending the reviews, or increasing your
review limit. That said, it is recommended you hold off on new cards until you
catch up instead, as introducing more new cards when you're behind will only
make the backlog worse.

From Anki 2.1.61 this feature is optional, and can be deactivated globally from the
deck options screen.

### Per-Deck Daily Limits

From version 2.1.55 it is possible to use the same preset for different decks / subdecks, with customized
limits for each one of them. This eliminates the need to create cloned presets just for that
purpose, and makes it easier to set custom limits on sub-decks when you have many nested decks.

The options are:

- Preset: The limit is shared with all decks using this preset.
- This deck: The limit is specific to this deck.
- Today only: Make a temporary change to this deck's limit.

## New Cards

The settings in this section only affect new cards and cards in initial
[learning](studying.md#learningrelearning-cards) mode. Once a card
has graduated (i.e. there are no more learning steps for this card), it becomes a
[review card](studying.md#review-cards), and the
settings in this section are no longer applicable.

### Learning Steps

Controls the number of learning repetitions, and the delay
between them. One or more delays, separated by spaces must be entered.
Each time you press `Good` during review, the card moves to the next step.

For example, let's say that your learning steps are **1m 10m 1d**.

- When you press `Again`, the card goes back to first step, and will be shown
  again approximately 1 minute later.
- When you press `Good` on a new card, or a card answered `Again`, it will move
  to the next step, and be shown again in approximately 10 minutes.
- When you press `Good` on a card after the 10 minute step, it will be delayed
  until the next day.
- When you press `Good` on the card the next day, it will leave learning (i.e. it will graduate), and
  become a review card. It will be shown again after the delay configured by the
  _graduating interval_.

If there’s nothing else to study, Anki will show cards up to 20 minutes
early by default. The amount of time to look ahead is configurable in
the [preferences](preferences.md).

Please see the [learning](studying.md#learningrelearning-cards) section for more info on how
steps work.

#### Day Boundaries

Anki treats small steps and steps that [cross a day boundary](./preferences.md#review) differently.
With small steps, the cards are shown as soon as the delay has passed,
in preference to other waiting cards like reviews. This is done so that
you can answer the card as closely to your requested delay as possible.
In contrast, if the interval crosses a day boundary, it is automatically
converted to days.

### Graduating Interval

The delay in days between answering "Good" on a learning card with no steps left,
and seeing the card again as a review card. This means that it is the first interval
after the learning card becomes a review card. Please see the example
in the previous section.

### Easy Interval

The delay between answering `Easy` on a learning
card, and seeing it in review mode for the first time.

The `Easy` button immediately turns a learning card into a review card,
and assigns it the delay you have configured. It should always be at least
as long as the _graduating interval_, and typically a few days longer.

### Insertion Order

Controls whether Anki should add new cards into the deck randomly, or in order.
When you change this option, Anki will re-sort the decks using the current
Option Group. Cards with a lower due number will be shown first when studying, by
default. Changing this option will automatically update the existing position of
new cards.

One caveat with random order mode: if you review many of your new cards, and then
add more new cards, the newly added material is statistically more likely to
appear than the new cards that were already in the deck. For example, if you have 100 cards
in random order, then review the first 50, newly added cards are still given
position 1-100, but as you have already reviewed the first 50, the newly added
cards are more likely to appear earlier. To correct this, you can change the
order to Ordered mode and back again to force a re-sort.

When you select random order, Anki will randomize your notes, keeping
the cards of a given note close together. The cards of a given note are
shown in the order in which their card types appear, so that siblings are
introduced consistently — otherwise you could end up in a state where
some notes had all their cards introduced and other notes had only one
or two. Please see the "bury related" and "display order" sections below
for more info.

## Lapses

When you forget a review card, it is said to have 'lapsed', and the card must be
relearnt. The default behaviour for lapsed reviews is to reset the interval to
1 (i.e. make it due tomorrow), and put it in the learning queue for a refresher
in 10 minutes. This behaviour can be customized with the options listed below.

### Relearning Steps

The same as 'learning steps', but for forgotten reviews. When you fail a card
(press `Again`), the card enters the relearning phase, and before it becomes a
review card again, you will have to pass all the relearning steps — or, alternatively, press
`Easy` on the card.

If you leave the steps blank, the card will skip relearning, and will be assigned
a new review delay.

### Minimum Interval

Specifies a minimum number of days a card should wait after it finishes relearning.
The default is one day, meaning once relearning is finished, it will be shown again
the next day.

### Leeches

Control the way Anki handles leeches. Please see the [leeches](leeches.md)
section for more information.

## Display Order

The options in this section are taken from the deck you select to study, not
the deck of the currently displayed card.

This section is only available when you have [the v3 scheduler](https://shigeyukey.github.io/Anki-faqs-jp/the-2021-scheduler.html) enabled.

Some further information about display order is available in the [studying section](studying.md#display-order).

### New Card Gather Order

Controls how Anki gathers cards from each subdeck. The options are:

- Deck: gathers cards from each deck in order, starting from the top. Cards from
  each deck are gathered in ascending position. If the daily limit of the selected
  deck is reached, gathering may stop before all decks have been checked. This
  order is fastest in large collections, and allows you to prioritize subdecks that
  are closer to the top.

  Decks / subdecks are always ordered alphabetically, so you can give them a numeric prefix like
  001 to control the order they are shown. You can also use `_` and `~` as a
  prefix to place items at the top or bottom.

  Although position order depends initially on the 'Insertion Order' setting
  above, you can manually
  [reposition](https://docs.ankiweb.net/browsing.html#cards) cards in different
  ways.

- Deck, then random notes: gathers cards from each deck in order, starting from the top.
  Cards from each deck are gathered randomly.

- Ascending position: gathers cards by ascending position (due #), which is typically the oldest-added first.

- Descending position: gathers cards by descending position (due #), which is typically the latest-added first.

- Random notes: gathers cards of randomly selected notes. When sibling burying is disabled, this allows all cards of a note to be seen in a session (eg. both a front->back and back->front card)

- Random cards: gathers cards completely randomly.

### New Card Sort Order

Controls how new cards are sorted **after they have been gathered**. The options are:

- Card type: Displays cards in order of card type number. If you have sibling burying disabled, this will ensure all front→back cards are seen before any back→front cards. This is useful to have all cards of the same note shown in the same session, but not too close to one another.

- Order gathered: Shows cards exactly as they were gathered. If sibling burying is disabled, this will typically result in all cards of a note being seen one after the other.

- Card type, then random: Like Card type, but shuffles the cards of each card type number. If you use Ascending position to gather the oldest cards, you could use this setting to see those cards in a random order, but still ensure cards of the same note do not end up too close to one another.

- Random note, then card type: Picks notes at random, then shows all of their siblings in order.

- Random: Fully shuffles the gathered cards.

### New/Review Priority

Whether new cards should be mixed in with reviews, or shown before or after them.

### Interday Learning/Review Priority

Whether learning cards with a 1+ day delay should be mixed in with reviews, or
shown before or after them. Because learning cards tend to be harder than
reviews, some users prefer to see them at the end (getting the easy stuff done
first), or at the start (allowing more time to review forgotten ones).

### Review Sort Order

Controls how review cards are sorted while reviewing. The options are:

- Due date, then random: The default option prioritizes cards that have been waiting
  longer, and it's the recomended option when you are up to date, or when you only have a small
  backlog. If you have taken an extended break or have fallen behind in your reviews,
  you may want to consider changing the sort order temporarily.
- Due date, then deck. This also prioritizes cards that have been waiting
  longer, and then will show reviews for each subdeck in turn.
- Deck, then due date: This option will ensure reviews are shown for each
  subdeck in turn. This is generally not recommended, as having material appear
  consistently in the same order makes it easier to guess the answer based on context,
  and may lead to weaker memories.
- Ascending intervals: This will ensure cards with shorter intervals are shown first.
- Descending intervals: This will ensure cards with larger intervals are shown first.
- Ascending ease: This will show most difficult cards first.
- Descending ease: This will allow you to work through the easier material first.
- Relative overdueness: Display cards that you're most likely to have forgotten first. This is useful if
  you have a large backlog that may take some time to get through, and you want to
  reduce the chances of forgetting more cards.

  When using the SM-2 scheduler, overdueness is determined by comparing how
  overdue cards are, and how long their interval is. For example, a card with a
  current interval of 5 days that is overdue by 2 days, will display before a card
  with a current interval of 10 days that is overdue by 3 days.

  When using FSRS, overdueness is calculated based on on each card's retrievability,
  and the desired retention in the deck preset.

## Timer

Anki monitors how long it takes you to answer each card, so that it
can show you how long was spent studying each day. The time taken does
not influence scheduling.

The options are:

- Maximum answer seconds: The default limit is 60 seconds. If you take
  longer than that, Anki assumes you have walked away from your computer
  or have been distracted, and limits the recorded time to 60 seconds, so
  that you don’t end up with inaccurate statistics. If you consistently
  take longer than 60 seconds to answer a card (from when question is shown
  until you press an answer button), you may want to either consider raising
  this limit, or, ideally, making your cards simpler.
- Show answer timer: In the review screen, show a timer that counts the number
  of seconds you're taking to review each card.
- Stop timer on answer: whether the timer should keep running when you show
  the answer.

## Auto Advance

Requires Anki 23.12 or later. Auto Advance allows you to automatically reveal
the answer and/or move to the next card. To use it, you must first set a non-zero
time in "seconds to show question" and/or "seconds to show answer". Then, in the
review screen, use the Auto Advance action from the `More` button to start advancing.

## Burying

When Anki gathers cards, it first gathers intraday learning cards, then interday learning cards, then reviews, and finally new cards. This affects how burying works:

- If you have all burying options enabled, the sibling that comes earliest in that list will be shown. For example, a review card will be shown in preference to a new card.
- Siblings later in the list can not bury earlier card types. For example, if you disable burying of new cards, and study a new card, it will not bury any interday learning or review cards, and you may see both a review sibling and new sibling in the same session.

The options are:

- Bury new siblings: whether other new cards of the same note (e.g., reverse cards, adjacent cloze deletions) will be delayed until the next day.
- Bury review siblings: whether other review cards of the same note will be delayed until the next day.
- Bury interday learning siblings: whether other learning cards of the same note with intervals >= 1 day will be delayed until the next day.

For more info about burying cards, please see [this section](./studying.md#siblings-and-burying) of the manual.

## Audio

By default, Anki automatically plays audio on the front and back of
cards. If you check _Don't play audio automatically_, Anki will not play
audio until you press the replay audio key, `r` or `F5`.

_Always include question side when replaying audio_ controls whether audio from
the question side should be played when replaying the audio while an answer is
shown. Please note that it does not control what happens when you show the
answer; for that please see [this section](templates/fields.md#special-fields).

## Advanced

### FSRS

The [Free Spaced Repetition Scheduler (FSRS)](https://github.com/open-spaced-repetition/fsrs4anki) is an alternative to Anki's legacy
SuperMemo 2 (SM2) scheduler. By more accurately determining when you are likely
to forget, it can help you remember more material in the same amount of time.
This setting is shared by all deck presets.

FSRS is currently in the advanced section, as it was only just integrated into
Anki in the 23.10 release. When you enable the setting, some new options will
become available, and SM-2 specific settings, such as "Graduating interval",
"Easy bonus", etc, will be hidden.

**Before Enabling**

- Please ensure all of your Anki clients support FSRS. Anki 23.10, AnkiMobile 23.10,
  and AnkiWeb all support it. AnkiDroid supports it in 2.17alpha3+. If
  one of your clients doesn't support it, things will not work correctly.
- If you previously used the 'custom scheduling' version of FSRS, please make
  sure you clear out the custom scheduling section before enabling FSRS.

#### FSRS Options

**Desired Retention**

Desired retention controls how likely you are to remember cards when they are reviewed.
The default value of 0.9 will schedule cards so you have a 90% chance of remembering
them when they come up for review again.

Here is a graph that shows how adjusting this value will affect your workload:

<img src="media/FSRS_retention.png" width="600">

There are two things to notice:

- As desired retention approaches 1.0, the frequency that you need to review cards
  increases drastically. For example, imagine you have a card that you have a 90%
  chance of remembering after 100 days. If your desired retention was 0.95, you'd
  need to review it after 47 days instead (approximately twice as frequently).
  At 0.97, the delay would be only 27 days (approximately 3.7x as frequently).
  At 0.99, you'd be reviewing every 9 days (more than 10x what you'd be doing with
  the defaults).

- As desired retention decreases, you'll forget a greater percentage of your
  cards, and those cards will need to be reviewed again. Eventually, you'll
  get to a point where the forgotten cards contribute more to your workload
  than you gain from the longer delays, which is why you see the workload
  on the left of the graph increasing. Also, bear in mind that forgetting
  material frequently is demotivating.

For these reasons, we suggest you be conservative when adjusting this
number, and recommend you keep it between 0.85 and 0.95.

**SM-2 retention**

If your actual retention before switching to FSRS was significantly different
from 0.9, adjusting this value will allow Anki to better estimate your memory
state when it encounters cards that are missing review logs. Since review
logs typically won't be missing unless you explicitly deleted them to free
up space, most users will not need to adjust this.

**FSRS parameters**

FSRS parameters affect how cards are scheduled. They are not intended to be
manually modified. Once you've accumulated 1000+ reviews, you can have Anki
optimize the parameters for you, based on your review history.

**Reschedule cards on change**

This option controls whether the due dates of cards will be changed when you
enable FSRS, or change the parameters. The default is not to reschedule
cards: future reviews will use the new scheduling, but there will be no
immediate change to your workload. If rescheduling is enabled, the due dates
of cards will be changed, often resulting in a large number of cards becoming
due, so **activating this option is not recommended** when first switching from SM2.

If you wish to visualize how FSRS would change your schedule without altering
your workload, there are two ways you can do so:

- Enable FSRS without rescheduling, and compare the interval and stability
  graphs. The interval graph will show the current intervals of cards; the stability
  graph will show the intervals FSRS would give cards if the desired retention is 0.9.
- Create a backup, enable FSRS with rescheduling, check the future due graph, and then
  undo or restore from the backup.

**Optimize FSRS parameters**

The FSRS optimizer uses machine learning to learn your memory patterns
and find parameters that best fit your review history. To do this, the optimizer
requires several reviews to fine-tune the parameters.

If you have less than 1,000 reviews, you can use the default parameters that
are already entered into the "FSRS parameters" field. Even with the default
parameters, FSRS should work well for most users.

Once you've done 1000+ reviews in Anki, you can use the `Optimize` button to
analyze your review history, and automatically generate parameters that are
optimal for your memory and the content you're studying. Parameters are
preset-specific, so if you have decks that vary wildly in difficulty, it
is recommended to assign them separate presets, as the parameters for easy
decks and hard decks will be different. There is no need to optimize your
parameters frequently - once every few months is sufficient.

By default, parameters will be calculated from the review history of all
decks using the current preset. You can optionally adjust the search
before calculating the parameters, if you'd like to alter which cards
are used for optimizing the parameters.

**Evaluate FSRS parameters**

You can use the `Evaluate` button in the "Optimize FSRS parameters"
section to see metrics that show how well the parameters in the
"Model parameters" field fit your review history. Smaller numbers
indicate a better fit to your review history.

Log-loss doesn't have an intuitive interpretation. RMSE (bins) can be
interpreted as the average difference between the predicted probability
of recalling a card (R) and the measured (from the review history)
probability. For example, RMSE=5% means that, on average, FSRS
is off by 5% when predicting R.

Note that log-loss and RMSE (bins) are not perfectly correlated,
so two decks may have similar RMSE values but very different log-loss values,
and vice-versa.

**Compute optimal retention**

This experimental tool assumes you're starting with 0 cards, and will
attempt to calculate the amount of material you'll be able to retain
in the given time frame. The estimated retention will greatly depend
on your inputs, and if it significantly differs from 0.9, it's a sign
that the time you've allocated each day is either too low or too high
for the amount of cards you're trying to learn. This number can be
useful as a reference, but it is not recommended to copy it into the
desired retention field.

#### Learning and Re-learning Steps

(Re)learning steps of 1+ days are not recommended when using FSRS. The main 
reason they were popular with the old SM-2 scheduler is because repeatedly 
failing a card after it has graduated from the learning phase could reduce 
its ease a lot, leading to what some people called "ease hell". This is not 
a problem that FSRS suffers from.  By keeping your learning steps under a 
day, you will allow FSRS to schedule cards at times it has calculated are 
optimum for your material and memory.  Another reason not to use longer 
learning steps is because FSRS may end up scheduling the first review for a 
shorter time than your last learning step, leading to the `Hard` button 
showing a longer time than `Good`.

We also recommend you keep the number of learning steps to a minimum. Evidence
shows that repeating a card multiple times in a single day after you've
remembered it does not significantly help with memory, so your time is
better spent on other cards or a shorter study session

#### Add-On Compatibility

Some add-ons can cause conflicts with FSRS. As a general rule of thumb,
if an add-on affects a card's intervals, it shouldn't be used with FSRS.
A list of commonly used add-ons and their FSRS compatibility can be found in [Add-on Compatibility](https://github.com/open-spaced-repetition/fsrs4anki#add-on-compatibility).

#### More

For more info on FSRS, please check:

- [FSRS4Anki Wiki](https://github.com/open-spaced-repetition/fsrs4anki/wiki)
- [FSRS4Anki on Github](https://github.com/open-spaced-repetition/fsrs4anki)

### Maximum Interval

Allows you to place an upper limit on the time Anki
will wait to reshow a card. The default is 100 years; you can decrease
this to a smaller number if you’re willing to trade extra study time for
higher retention.

### Starting Ease

Controls the easiness that cards start out with. It is
set when a card graduates from learning for the first time. It defaults
to 2.50, meaning that once you have finished learning a card, answering
`Good` on subsequent reviews will increase the delay by approximately
2.5x (e.g. if the last delay was 10 days, the next delay would be around 25
days). Based upon how you rate the card in subsequent reviews, the
easiness may increase or decrease from its starting value.

### Easy Bonus

An extra multiplier applied to the interval when a review card is answered
`Easy`. With the default value of 1.30, `Easy` will give an interval that is
1.3 times the `Good` interval (e.g. if the Good interval was 10 days, the Easy
interval would be around 13 days).

### Interval Modifier

An extra multiplier that is applied to all reviews. At its default of 1.00 it
does nothing. If you set it to 0.80, though, for example, intervals will be generated at
80% of their normal size (so a 10 day interval would become 8 days). You can
thus use the multiplier to make Anki present cards more or less frequently than
it would otherwise, trading study time for retention or vice versa.

For moderately difficult material, the average user should find they
remember approximately 90% of mature cards that come up for review. You
can find out your own performance by opening the graphs/statistics for a
deck and looking at the Answer Buttons graph - mature retention is the
correct% on the right side of the graph. If you haven’t been studying
long, you may not have any mature cards yet. As performance with new
cards and younger cards can vary considerably, it’s a good idea to wait
until you have a reasonable amount of mature reviews before you start
drawing conclusions about your retention rate.

On the SuperMemo website, they suggest that you can find an appropriate
multiplier for a desired retention rate. Their formula boils down to:

    log(desired retention%) / log(current retention%)

Imagine we have a current retention rate of 85% and we want to increase
it to 90%. We’d calculate the modifier as:

    log(90%) / log(85%) = 0.65

You can use Google to [calculate it](https://www.google.com/search?q=log(90%25)+%2F+log(85%25)) for you.

If you plug the resulting 65% into the interval modifier, you should
find over time that your retention moves closer to your desired
retention.

One important thing to note however is that the trade-off between time
spent studying and retention is not linear: we can see here that to
increase our retention by 5 percentage points, we would have to study 35%
more frequently. If the material you are learning is very important then
it may be worth the extra effort – that is, of course, something you will need to
decide for yourself. If you are simply worried that you are forgetting too
much, then you may find investing more time at the initial learning stage
and/or using mnemonics will give you more gain for less effort.

One final thing to note is that Anki forces a new interval to be at
least 1 day longer than it was previously, so that you do not get stuck
reviewing with the same interval forever. If your goal is to repeat a
card once a day for multiple days, you can do that by setting more
learning mode steps, instead of by adjusting this modifier.

### Hard Interval

The multiplier used when you use the `Hard` button. The percentage is relative
to the previous interval: e.g. with a default of 1.20, a card with a 10-day interval
will be given 12 days.

### New Interval

The multiplier used when you use the `Again` button on a review card. The
default 0.00 means that a review card's delay is reset to zero when you forget it
(which then becomes 1 day after the [minimum interval](#minimum-interval) is
applied).

If changed from the default, it is possible for forgotten cards to preserve part
of their previous delay. For example, if a card had a 100 day interval, and you set
the _New Interval_ to 0.20, the new interval would be 20 days.

While preserving part of the interval may seem to make sense, SuperMemo has observed
that preserving part of the delay can actually [be counter-productive](https://supermemo.guru/wiki/Post-lapse_stability). For this reason, we recommend you leave it on the default setting.

## Custom Scheduling

Please see [this page](https://shigeyukey.github.io/Anki-faqs-jp/the-2021-scheduler.html#add-ons-and-custom-scheduling). -->
