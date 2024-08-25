# 数学と記号

<!-- toc -->

## MathJax

[MathJax](https://www.mathjax.org)は、現代のブラウザベースの組版システムで、数学や化学の方程式に便利です。追加のソフトウェアをインストールする必要がないため、簡単に使用でき、ほとんどのユーザーに推奨されます。

MathJaxはAnki 2.1+、AnkiMobile、およびAnkiDroid 2.9+で標準サポートされています。

試してみるには：

1. フィールドに次のように入力します：

       \sqrt{x}

2. 今入力したテキストを選択します。

3. エディタの一番右のボタンをクリックし、メニューから「MathJaxインライン」を選択します。Ankiはテキストを次のように変更します：

       \(\sqrt{x}\)

4. 「カード…」ボタンをクリックすると、カードが復習されるときに方程式がどのように表示されるかのプレビューが表示されます。

AnkiのMathJaxサポートはTeX形式のコンテンツを期待しています。TeX形式に慣れていない場合は、[このチートシート](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)を参照してください。ポイント2はAnkiには適用されないことに注意してください。Ankiではインライン方程式に`\(`と`\)`、表示方程式に`\[`と`\]`を使用します。

MathJax式で改行を使用したい場合は、通常の改行ではMathJaxが正しく動作しないため、<kbd>Shift</kbd>+<kbd>Enter</kbd>を使用してください。

Ankiには化学方程式をレンダリングするためのmhchemの組み込みサポートが含まれています。詳細については、「化学方程式」セクションおよび以下のセクションを参照してください：
<https://mhchem.github.io/MathJax-mhchem/>

いくつかの設定を[カスタマイズすること](https://shigeyukey.github.io/Anki-faqs-jp/customizing-mathjax.html)も可能です。

## LaTeX

LaTeXは強力な組版システムで、数学の公式、化学式、楽譜などの入力に便利です。AnkiはLaTeXのサポートを提供しており、ノートにLaTeXコードを入力することができます。カードを復習するとき、AnkiはLaTeXを呼び出して生成された画像を表示します。

LaTeXの設定は少し手間がかかり、画像はAnkiのコンピュータ版でのみ生成できますが、一度生成されるとモバイルクライアントでも画像を表示できます。MathJaxが提供する機能以上のものが必要なユーザーにのみ、LaTeXの使用をお勧めします。

### 前提知識

AnkiのLaTeXサポートはすぐに使えるものではありません。LaTeXの使用方法を既に知っており、インストールされていることが前提です。LaTeXの経験がない場合は、インターネット上の多くのガイドを参照してください。マークアップに問題がある場合は、LaTeXフォーラムで質問してください。

LaTeXをインストールするには、WindowsではMiKTeXを、macOSではMacTeXを、Linuxではディストリビューションのパッケージマネージャを使用してください。dvipngもインストールする必要があります。

Windowsでは、MikTeXのメンテナンスウィンドウの設定に移動し、「Install missing packages on the fly」を「Always」に設定し、「Ask me first」には設定しないでください。引き続き問題が発生する場合、あるユーザーはすべてのパッケージが取得されるまでAnkiを管理者として実行することで解決したと報告しています。

macOSでは、LaTeXはMacTeXおよびBasicTeXでのみテストされています。BasicTeXを使用する場合は、以下のコマンドでdvipngを別途インストールする必要があります：

    sudo tlmgr update --self; sudo tlmgr install dvipng

コマンドがパスに含まれていない場合があるため、フルパスを指定する必要があるかもしれません。例：/usr/local/texlive/2014basic/bin/x86_64-darwin/tlmgr

上記のLaTeXパッケージを使用していない場合は、[edit LaTeX](https://ankiweb.net/shared/info/937148547)アドオンを使用して、latexおよびdvipngへのフルパスを指定する必要があります。

### Web/モバイル

LaTeXを含むカードを復習すると、AnkiはそのLaTeXの画像を生成し、将来使用するためにコレクションのメディアフォルダに画像を配置します。Webおよびモバイルクライアントは、既に存在するこれらの画像を表示しますが、自分で画像を生成することはできません。

他のクライアントで学習する前にすべてのカードを少なくとも一度復習する必要がないようにするために、Ankiは一括で画像を生成することができます。すべての画像を生成するには、ツール > メディアの確認に移動してください。その後、同期すると生成されたメディアがAnkiWebおよび他のクライアントにアップロードされます。

## 例

LaTeXコンテンツを入力する最も一般的な方法は、\[latex\]\[/latex\]タグで囲むことです。このショートカットボタンについては[エディタ](editing.md)セクションに記載されています。

\[latex\]タグはフィールド内で使用する必要があります。カードテンプレートに配置すると[問題が発生します](templates/fields.md)。

例えば、Ankiのフラッシュカードの表面に次のように入力すると：

    Does [latex]\begin{math}\sum_{k = 1}^{\infty}\frac{1}{k}\end{math}[/latex] converge?

フラッシュカードを表示したときに次のように表示されます：

![収束の質問](math/convergence_question.png)

上記の例の数式は「テキスト数式」と呼ばれ、非数学的なテキスト内に直接表示されます。対照的に、次の例は「表示数式」を示しています：

    Does the sum below converge?

    [latex]\begin{displaymath}\sum_{k = 1}^{\infty}\frac{1}{k}\end{displaymath}[/latex]

![収束の質問 2](math/convergence_question_2.png)

「テキスト数式」と「表示数式」は最も一般的なタイプのLaTeX表現であるため、Ankiはそれらの省略形を提供しています。次の形式の表現：

    [latex]\begin{math}...\end{math}[/latex]

は次のように短縮できます：

    [$]...[/$]

また、次の形式の表現：

    [latex]\begin{displaymath}...\end{displaymath}[/latex]

は次のように短縮できます：

    [$$]...[/$$]

例えば、前述の2つのLaTeXスニペットはそれぞれ次のように等価です：

    Does [$]\sum_{k = 1}^{\infty}\frac{1}{k}[/$] converge?

および

    Does the sum below converge?

    [$$]\sum_{k = 1}^{\infty}\frac{1}{k}[/$$]

それぞれ。

### パッケージ

Ankiでは、LaTeXのプリアンブルをカスタマイズして、化学や音楽などのカスタムパッケージをインポートすることができます。例えば、インターネットでchemtexのサンプルファイルを見つけたとします：

    \documentclass[a4paper,12pt]{report}
    \usepackage{chemtex}
    \begin{document}

    \initial
    \begin{figure}[h]\centering
    \parbox{.3\textwidth}{\ethene{H}{H$_3$C}{CH$_3$}{Br}}
    \hfil
    \parbox{.3\textwidth}{\cbranch{H}{S}{H}{S}{C}{S}{}{S}{H}
      \xi=-200 \cright{}{Q}{C}{D}{O}{S}{OH}}
    \hfil
    \parbox{.3\textwidth}{\hetisix{Q}{Q}{Q}{Q}{Q}{Q}{O}{Q}{O}
      \xi=-171 \fuseup{Q}{Q}{Q}{Q}{D}{Q}{D}{Q}{D}}
    \caption{Chemie mit {\tt CHEMTEX}\label{a1}}
    \end{figure}

    \end{document}

まず、パッケージとMiKTeX/MacTeXのドキュメントに従ってパッケージをインストールします。パッケージが動作しているか確認するために、上記のようなコードを.latexファイルに入れ、コマンドラインからコンパイルできるかテストします。パッケージが利用可能で動作していることを確認したら、Ankiに統合できます。

Ankiでパッケージを使用するには、メインウィンドウで「追加」をクリックし、ノートタイプ選択ボタンをクリックします。「管理」ボタンをクリックし、使用する予定のノートタイプを選択して「オプション」をクリックします。LaTeXのヘッダーとフッターが表示されます。ヘッダーは次のようになっています：

    \documentclass[12pt]{article}
    \special{papersize=3in,5in}
    \usepackage{amssymb,amsmath}
    \pagestyle{empty}
    \setlength{\parindent}{0in}
    \begin{document}

chemtexを使用するには、先ほどの例のようにusepackage行を追加し、次のようにします：

    \documentclass[12pt]{article}
    \special{papersize=3in,5in}
    \usepackage{amssymb,amsmath}
    \usepackage{chemtex}
    \pagestyle{empty}
    \setlength{\parindent}{0in}
    \begin{document}

その後、Ankiカードに次のような行を含めることができるようになります：

    [latex]\ethene{H}{H$_3$C}{CH$_3$}{Br}[/latex]

### テンプレートの競合

Anki 2.1.20 / AnkiMobile 2.0.56 / AnkiDroid 2.13以降、この回避策は不要になりました。フィールド内の`{{field}}`テキストが問題を引き起こさなくなったためです。古いバージョンをサポートする必要があり、この構文を使用し続けたい場合は、`{{=<% %>=}}`文字列を表と裏のテンプレートの最上部に配置してください。最近のAnkiバージョンでは、これが先頭以外の場所にあると認識されません。

古いバージョンの場合：

数学の方程式を書くときに、LaTeXコード内に{{と}}が現れることは珍しくありません。LaTeX方程式がAnkiのフィールド置換と競合しないようにするために、セパレータを別のものに変更することが可能です。

例えば、テンプレートが次のようになっている場合：

    {{latex field}}

次のように変更すると、LaTeXが競合する可能性が低くなります：

    {{=<% %>=}}
    <%latex field%>

### クローズの競合

穴埋め問題は`}}`で終了しますが、これはLaTeX内に現れる`}}`と競合する可能性があります。LaTeXがクローズの終了マーカーとして解釈されないようにするために、クローズの終了を示さない二重閉じ中括弧の間にスペースを入れることができます。例えば、

    {{c1::[$]\frac{foo}{\frac{bar}{baz}}[/$] blah blah blah.}}

は動作しませんが、

    {{c1::[$]\frac{foo}{\frac{bar}{baz} }[/$] blah blah blah.}}

は動作します（LaTeXは数式モードでスペースを無視するため、方程式は同じようにレンダリングされます）。レンダリングされたテキストに余分なスペースを追加したくない場合（例えば、プログラミング言語を学習するためのクローズカードを作成する場合）、HTMLモードでカードを編集するときにHTMLコメントを使用する別の方法があります：

    {{c1::[$]\frac{foo}{\frac{bar}{baz}<!-- -->}[/$] blah blah blah.}}

穴埋め問題されたテキスト内で`::`文字列を使用する必要がある場合、どちらの回避策も使用できます。次のノートテキストに対して生成される最初のカードは`[type] in C++ is a type-safe union`となります：

    {{c1::std:<!-- -->:variant::~type~}} in C++ is a {{c2::type-safe union}}

### 安全でないコマンド

Ankiは、\\inputや\\defなどの特定のコマンドをカードやテンプレートで使用することを禁止しています。これらのコマンドを許可すると、悪意のある共有デッキがシステムに損害を与える可能性があるためです。（安全のため、これらのコマンドはコメント内でも禁止されています。そのため、このエラーが発生しているが使用していないと思われる場合は、ヘッダー、テンプレート、およびカード内のコメントを再確認してください。）これらのコマンドを使用する必要がある場合は、システムパッケージに追加し、前のセクションで説明したようにそのパッケージをインポートしてください。