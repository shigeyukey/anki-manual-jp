# 検索

<!-- toc -->

Ankiのブラウズ画面とフィルターデッキ機能は、特定のカードやノートを検索するための共通の方法を使用します。

## シンプルな検索

検索ボックスにテキストを入力すると、Ankiは一致するノートを見つけてそのカードを表示します。Ankiはノートのすべてのフィールドを検索しますが、タグは検索しません（タグの検索方法についてはこのセクションの後半を参照してください）。いくつかの例を示します：

`dog`\
「dog」を検索します - 「doggy」や「underdog」のような単語も一致します。

`dog cat`\
「dog」と「cat」の両方を含むノートを見つけます。例えば、「raining cats and dogs」などです。

`dog or cat`\
「dog」または「cat」を含むノートを見つけます。

`dog (cat or mouse)`\
「dog」と「cat」、または「dog」と「mouse」を含むノートを見つけます。

`-cat`\
「cat」という単語を含まないノートを見つけます。

`-cat -mouse`\
「cat」も「mouse」も含まないノートを見つけます。

`-(cat or mouse)`\
上記と同じです。

`"a dog"`\
「a dog」という正確な文字列を含むノートを見つけます。例えば、「atta dog」などですが、「dog a」や「adog」は含まれません。

`-"a dog"`\
「a dog」という正確なフレーズを含まないノートを見つけます。

`d_g`\
「d」と任意の1文字と「g」を含むノートを見つけます。例えば、dog、dig、dugなどです。

`d*g`\
「d」と0文字以上の任意の文字列と「g」を含むノートを見つけます。例えば、dg、dog、dungなどです。

`w:dog*`\
「dog」と「doggy」には一致しますが、「underdog」には一致しません。

`w:*dog`\
「dog」と「underdog」には一致しますが、「doggy」には一致しません。

上記の点に注意してください：

- 検索用語はスペースで区切られます。

- 複数の検索用語が提供された場合、Ankiはすべての用語に一致するノートを探します。各用語の間に暗黙の「and」が挿入されます。Anki 2.1.24+およびAnkiMobile 2.0.60+では、明示的に指定することもできます（「dog and cat」は「dog cat」と同じです）が、古いAnkiバージョンでは「and」を単なる検索用語として扱います。

- 用語のいずれか一つに一致するだけでよい場合は、「or」を使用できます。

- 用語の前にマイナス記号を付けると、その用語に一致しないノートを見つけることができます。

- 検索用語を括弧で囲むことでグループ化できます。例えば、**dog (cat or mouse)** のようにします。これは、OR検索とAND検索を組み合わせる際に重要になります。この例では、括弧があると「dog cat」または「dog mouse」に一致しますが、括弧がないと「dog and cat」または「mouse」に一致します。

- Ankiは、設定した[ソートフィールド](editing.md#フィールドのカスタマイズ)内の書式設定に対してのみ検索を行うことができます。例えば、フィールドの一つに「**exa**mple」と追加した場合、そのフィールドがソートフィールドでない限り、「example」を検索しても一致しません。単語が書式設定されていない場合、または単語の途中で書式設定が変更されない場合、Ankiは任意のフィールドでそれを見つけることができます。

- 標準の検索はラテン文字に対して大文字小文字を区別しません。a-zはA-Zと一致し、その逆も同様です。キリル文字などの他の文字は標準の検索では大文字小文字を区別しますが、単語境界や正規表現（`w:`, `re:`）で検索することで大文字小文字を区別しないようにできます。

## フィールドに限定する

特定のフィールドにテキストが含まれている場合にのみ一致させるようにAnkiに指示することもできます。上記の検索とは異なり、フィールド検索はデフォルトで「完全一致」を要求します。

`front:dog`\
Frontフィールドが正確に「dog」であるノートを見つけます。「a dog」と書かれているフィールドは一致しません。

`"animal front:a dog"`\
「Animal Front」フィールドが正確に「a dog」であるノートを見つけます。ダブルクォートは必須です。詳細は[こちら](#特殊文字の一致)を参照してください。

`front:*dog*`\
Frontフィールドに「dog」が含まれているノートを見つけます。

`front:`\
Frontフィールドが空のノートを見つけます。

`front:_*`\
Frontフィールドが空でないノートを見つけます。

`front:*`\
Frontフィールドが存在するノートを見つけます（空かどうかは問いません）。

`fr*:text`\
「fr」で始まるフィールドに「text」が含まれているノートを見つけます。Anki 2.1.24+またはAnkiMobile 2.1.60+が必要です。

## タグ デッキ カード ノート

`tag:animal`\
「animal」タグ、または「animal::mammal」のようなサブタグを持つノートを見つけます。

`tag:none`\
タグがないノートを見つけます。

`tag:ani*`\
「ani」で始まるタグを持つノートを見つけます。

`deck:french`\
「French」デッキ、または「French::Vocab」のようなサブデッキにあるカードを見つけます。

`deck:french -deck:french::*`\
「French」デッキにあるが、サブデッキにはないカードを見つけます。

`deck:"french vocab"`\
デッキ名にスペースが含まれる場合の検索。

`"deck:french vocab"`\
これも同様に機能します。

`deck:filtered`\
フィルターデッキのみを検索します。

`-deck:filtered`\
通常のデッキのみを検索します。

`card:forward`\
「Forward」カードを検索します。

`card:1`\
テンプレート番号でカードを検索します。例えば、ノートの2番目の穴埋め問題を見つけるには、`card:2`を使用します。

`note:basic`\
Basicノートタイプのカードを検索します。

## アクセント 結合文字を無視する

Anki 2.1.24+ または AnkiMobile 2.0.60+ が必要です。

`nc:` を使用して結合文字を削除できます（「結合なし」）。例えば：

`nc:uber`\
「uber」、「über」、「Über」などを含むノートに一致します。

`nc:は`\
「は」、「ば」、「ぱ」に一致します。

結合文字を無視する検索は、通常の検索よりも遅くなります。

## 正規表現

Anki 2.1.24+ および AnkiMobile 2.0.60+ は、ノート内を「正規表現」で検索することをサポートしています。正規表現は、テキスト検索の標準かつ強力な方法です。

検索を `re:` で始めると、正規表現で検索できます。Ankiはこれを[生の入力](#生の入力)として扱うので、そこに記載されているルールを考慮してください。

いくつかの例を示します：

`"re:(some|another).*thing"`\
「some」または「another」に続いて0文字以上の任意の文字があり、その後に「thing」が続くノートを見つけます。

`re:\d{3}`\
3つの連続した数字を含むノートを見つけます。

正規表現は特定のフィールドに限定することもできます。通常の特定フィールド検索とは異なり、フィールド内の正規表現は完全一致を必要としないことに注意してください。例えば：

`front:re:[a-c]1`\
「Front」フィールド内の任意の場所に大文字または小文字のa1、B1、c1が含まれるノートに一致します。

`front:re:^[a-c]1$`\
上記と似ていますが、a1/b1/c1の前後に他のテキストがある場合は一致しません。

Anki 2.1.50 ではタグの正規表現サポートが追加されました：

`tag:re:^parent$`\
「parent」という正確なタグを持つノートを見つけます。「parent::child」のような子タグは無視されます。

`"tag:re:lesson-(1[7-9]|2[0-5])"`\
「lesson-17」から「lesson-25」までのタグを持つノートを見つけます。

正規表現についての詳細は、こちらで学ぶことができます：<https://regexone.com/lesson/introduction_abcs>

注意点：

- 検索はデフォルトで大文字小文字を区別しません。大文字小文字を区別するには、先頭に `(?-i)` を追加します。
- スペースや改行などの一部のテキストはHTMLで異なる表現をされる場合があります。編集画面のHTMLエディタを使用して、基礎となるHTML内容を確認できます。
- Ankiの正規表現サポートの詳細については、regex crateのドキュメントを参照してください：<https://docs.rs/regex/1.3.9/regex/#syntax>

## カードの状態

`is:due`\
復習カードと学習待ちのカード

`is:new`\
新しいカード

`is:learn`\
習得中のカード

`is:review`\
復習（期限があるものとないもの）および失効したカード

`is:suspended`\
手動で一時停止されたカード

`is:buried`\
[自動的](studying.md#兄弟カードと埋める)または手動で埋められたカード

新しいスケジューラーでは、手動で埋められたカードと自動的に埋められたカードを区別するため、一方を解除しても他方は解除されません。

失効したカードはこれらのカテゴリのいくつかに該当するため、より正確な結果を得るためにそれらを組み合わせると便利です：

`is:learn is:review`\
失効して再学習待ちのカード

`-is:learn is:review`\
失効カードを含まない復習カード

`is:learn -is:review`\
初めて習得中のカード

`flag:1`\
赤いフラグが付いたカード

`flag:2`\
オレンジ色のフラグが付いたカード

`flag:3`\
緑色のフラグが付いたカード

`flag:4`\
青いフラグが付いたカード

`flag:5`\
ピンク色のフラグが付いたカード

`flag:6`\
ターコイズ色のフラグが付いたカード

`flag:7`\
紫色のフラグが付いたカード

## カードのプロパティ

`prop:ivl>=10`\
間隔が10日以上のカード

`prop:due=1`\
明日が期限のカード

`prop:due=-1`\
昨日が期限でまだ回答されていないカード

`prop:due>-1 prop:due<1`\
昨日から明日までの間に期限があるカード

`prop:reps<10`\
回答回数が10回未満のカード

`prop:lapses>3`\
再学習に移行した回数が3回を超えるカード

`prop:ease!=2.5`\
デフォルトよりも簡単または難しいカード

`prop:cdn:d>5`（Anki 2.1.64+が必要です。）\
カスタムデータ内の `d` の値（通常はFSRSの難易度を指します）が5を超えるカード

`prop:cds:v=reschedule`（Anki 23.10+が必要です。）\
カスタムデータ内の文字列 `v` が `reschedule` と等しいカード

`prop:s>21`（Anki 23.10+およびFSRSが有効であることが必要です。）\
安定性が21日を超えるカード

`prop:d>0.3`（Anki 23.10+およびFSRSが有効であることが必要です。）\
難易度が0.3を超えるカード

`prop:r<0.9`（Anki 23.10+およびFSRSが有効であることが必要です。）\
保持率が0.9未満のカード

## 最近のイベント

### 追加

`added:1`\
今日追加されたカード

`added:7`\
過去1週間に追加されたカード

このチェックはノートの作成時間ではなくカードの作成時間に対して行われるため、ノートが長い間前に追加されていても、指定された期間内に生成されたカードが含まれます。

### 編集

`edited:n`\
ノートのテキストが過去n日以内に追加/編集されたカード。

これにはAnki 2.1.28+ / AnkiMobile 2.0.64+が必要です。

### 回答

`rated:1`\
今日回答されたカード

`rated:1:2`\
今日「難しい (2)」と評価されたカード

`rated:7:1`\
過去7日間に「再学習 (1)」と評価されたカード

`rated:31:4`\
過去1ヶ月間に「簡単 (4)」と評価されたカード

評価検索はバージョン2.1.39以前では31日間に制限されていました。

### 最初の回答

バージョン2.1.45+では、最初の復習のみを検索することもできます：

`introduced:1`\
今日初めて回答されたカード

`introduced:365`\
過去365日以内に初めて回答されたカード

## 特殊文字の一致

このセクションはAnki 2.1.36+用に書かれています。以前のバージョンでは、特定の状況で文字のエスケープをサポートしていませんでした。

前のセクションで示したように、`*`、`_`、`"`などの文字はAnkiで特別な意味を持ちます。これらの文字を検索で見つける必要がある場合、Ankiにそれらを特別扱いしないように指示する必要があります。

- _スペース_\
  スペースを含むものに一致させるには、`"全体の用語"`を二重引用符で囲みます。コロン検索の場合、`コロンの後:"の部分"`だけを引用符で囲むこともできます（コロンの前にもスペースがある場合を除きます）。

- `"`, `*` および `_`\
  これらの文字を文字通りに扱うには、文字の前にバックスラッシュを追加します。例えば、`_`は任意の1文字に一致しますが、`\_`は実際のアンダースコアにのみ一致します。

- `\`\
  バックスラッシュは他の文字の特別な意味を取り除くために使用されるため、それ自体も特別に扱われます。実際のバックスラッシュを検索する必要がある場合は、`\`の代わりに`\\`を使用します。

- `(` および `)`\
  括弧を検索するには、用語全体を引用符で囲むか、バックスラッシュを使用します。つまり、`"some(text)"`、`some\(text\)`、および`"some\(text\)"`はすべて同等ですが、`some(text)`はそうではありません。

- `-`\
  検索用語を`-`で始めると通常は反転します。例えば、`-dog`はdog以外のすべてに一致します。実際のハイフンを含めたい場合は、バックスラッシュを使用するか、テキストを引用符で囲むことができます。例えば、`\-.-`または`"-.-"`です。

- `:`\
  コロンは、他のエスケープされていないコロンの後に続かない限り、エスケープする必要があります。したがって、`w:e:b`は`e:b`の単語境界検索であり、`w\:e\:b`は文字通り`w:e:b`を検索し、`w\:e:b`はフィールド`w:e`で`b`を検索します（[フィールド検索](#フィールドに限定する)を参照）。

- `&`、`<`、および `>`\
  `&`、`<`、および `>`はAnkiで検索する際にHTMLとして扱われるため、これらを含む検索は期待通りに動作しません。ただし、対応するHTMLエンティティ名（`&`は`&amp;`、`<`は`&lt;`、`>`は`&gt;`）を使用して検索することができます。例えば、`&lt;&amp;text&gt;`を検索すると、フィールドに`<&text>`が含まれるカードが検索されます。

### 生の入力

特定のキーワード（`re:`など）の前にあるテキストは、生の入力として扱われます。つまり、上記の文字は特別な意味をほとんど失います。このような文脈では、曖昧さを防ぐために最小限のエスケープが必要です：

- `"` はエスケープする必要があります。

- スペースとエスケープされていない括弧は、検索用語を引用符で囲む必要があります。

- 検索用語は奇数個のバックスラッシュで終わってはいけません。

## オブジェクトID

`nid:123`\
ノートIDが123のノート

`cid:123,456,789`\
カードIDが123、456、789のすべてのカード

ノートおよびカードIDは、ブラウザの[カード情報](stats.md)ダイアログで確認できます。これらの検索は、アドオンの開発やデータベースと密接に連携する場合にも役立ちます。
