<!--
AUTHORS:
Prefer only GitHub-flavored Markdown in external text.
See README.md for details.
-->

# Google Python Style Guide 和訳

<!-- markdown="1" is required for GitHub Pages to render the TOC properly. -->

1. [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html)の和訳(途中)を CC-By 3.0 License で公開します．
2. markdownからhtmlを生成してgithub.ioで公開する方法が分からなくて泣きそうです．
3. 翻訳に関する指摘・コメントは Issues or Pull Requests でお願いします．

<details markdown="1">
  <summary>Table of Contents</summary>

- [Google Python Style Guide 和訳](#google-python-style-guide-和訳)
  - [1 背景](#1-背景)
  - [2 Pythonの言語に関する規約](#2-pythonの言語に関する規約)
    - [2.1 Lint](#21-lint)
      - [2.1.1 定義](#211-定義)
      - [2.1.2 利点](#212-利点)
      - [2.1.3 欠点](#213-欠点)
      - [2.1.4 決定](#214-決定)
    - [2.2 Imports](#22-imports)
      - [2.2.1 定義](#221-定義)
      - [2.2.2 利点](#222-利点)
      - [2.2.3 欠点](#223-欠点)
      - [2.2.4 決定](#224-決定)
    - [2.3 Packages](#23-packages)
      - [2.3.1 利点](#231-利点)
      - [2.3.2 欠点](#232-欠点)
      - [2.3.3 決定](#233-決定)
    - [2.4 Exception (例外)](#24-exception-例外)
      - [2.4.1 定義](#241-定義)
      - [2.4.2 利点](#242-利点)
      - [2.4.3 欠点](#243-欠点)
      - [2.4.4 決定](#244-決定)
    - [2.5 Global variables (グローバル変数)](#25-global-variables-グローバル変数)
      - [2.5.1 定義](#251-定義)
      - [2.5.2 利点](#252-利点)
      - [2.5.3 欠点](#253-欠点)
      - [2.5.4 決定](#254-決定)
    - [2.6 Nested/Local/Inner Classes and Functions (ネストされたローカル/内部クラスと関数)](#26-nestedlocalinner-classes-and-functions-ネストされたローカル内部クラスと関数)
      - [2.6.1 定義](#261-定義)
      - [2.6.2 利点](#262-利点)
      - [2.6.3 欠点](#263-欠点)
      - [2.6.4 決定](#264-決定)
    - [2.7 Comprehensions & Generator Expressions (内包表記とジェネレータ式)](#27-comprehensions--generator-expressions-内包表記とジェネレータ式)
      - [2.7.1 定義](#271-定義)
      - [2.7.2 利点](#272-利点)
      - [2.7.3 欠点](#273-欠点)
      - [2.7.4 決定](#274-決定)
    - [2.8 Default Iterators and Operators (デフォルトのイテレータとオペレータ)](#28-default-iterators-and-operators-デフォルトのイテレータとオペレータ)
      - [2.8.1 定義](#281-定義)
      - [2.8.2 利点](#282-利点)
      - [2.8.3 欠点](#283-欠点)
      - [2.8.4 決定](#284-決定)
    - [2.9 Generators (ジェネレータ)](#29-generators-ジェネレータ)
      - [2.9.1 定義](#291-定義)
      - [2.9.2 利点](#292-利点)
      - [2.9.3 欠点](#293-欠点)
      - [2.9.4 決定](#294-決定)
    - [2.10 Lambda Functions (ラムダ関数)](#210-lambda-functions-ラムダ関数)
      - [2.10.1 定義](#2101-定義)
      - [2.10.2 利点](#2102-利点)
      - [2.10.3 欠点](#2103-欠点)
      - [2.10.4 決定](#2104-決定)
    - [2.11 Conditional Expressions (条件式)](#211-conditional-expressions-条件式)
      - [2.11.1 定義](#2111-定義)
      - [2.11.2 利点](#2112-利点)
      - [2.11.3 欠点](#2113-欠点)
      - [2.11.4 決定](#2114-決定)
    - [2.12 Default Argument Values (引数のデフォルト値)](#212-default-argument-values-引数のデフォルト値)
      - [2.12.1 定義](#2121-定義)
      - [2.12.2 利点](#2122-利点)
      - [2.12.3 欠点](#2123-欠点)
      - [2.12.4 決定](#2124-決定)
    - [2.13 Properties (プロパティ)](#213-properties-プロパティ)
      - [2.13.1 定義](#2131-定義)
      - [2.13.2 利点](#2132-利点)
      - [2.13.3 欠点](#2133-欠点)
      - [2.13.4 決定](#2134-決定)
    - [2.14 True/False Evaluations (真偽の評価)](#214-truefalse-evaluations-真偽の評価)
      - [2.14.1 定義](#2141-定義)
      - [2.14.2 利点](#2142-利点)
      - [2.14.3 欠点](#2143-欠点)
      - [2.14.4 決定](#2144-決定)
    - [2.16 Lexical Scoping (レキシカルスコープ)](#216-lexical-scoping-レキシカルスコープ)
      - [2.16.1 定義](#2161-定義)
      - [2.16.2 利点](#2162-利点)
      - [2.16.3 欠点](#2163-欠点)
      - [2.16.4 決定](#2164-決定)
    - [2.17 Function and Method Decorators (デコレータ)](#217-function-and-method-decorators-デコレータ)
      - [2.17.1 定義](#2171-定義)
      - [2.17.2 利点](#2172-利点)
      - [2.17.3 欠点](#2173-欠点)
      - [2.17.4 決定](#2174-決定)
    - [2.18 Threading (スレッド)](#218-threading-スレッド)
    - [2.19 Power Features](#219-power-features)
      - [2.19.1 定義](#2191-定義)
      - [2.19.2 利点](#2192-利点)
      - [2.19.3 欠点](#2193-欠点)
      - [2.19.4 決定](#2194-決定)
    - [2.20 Modern Python: from \_\_future\_\_ imports (\_\_future\_\_ からimportできるモダンな機能)](#220-modern-python-from-__future__-imports-__future__-からimportできるモダンな機能)
      - [2.20.1 定義](#2201-定義)
      - [2.20.2 利点](#2202-利点)
      - [2.20.3 欠点](#2203-欠点)
      - [2.20.4 決定](#2204-決定)
        - [from \_\_future\_\_ imports](#from-__future__-imports)
        - [The six, future, and past libraries](#the-six-future-and-past-libraries)
    - [2.21 Type Annotated Code (型ヒント)](#221-type-annotated-code-型ヒント)
      - [2.21.1 定義](#2211-定義)
      - [2.21.2 利点](#2212-利点)
      - [2.21.3 欠点](#2213-欠点)
      - [2.21.4 決定](#2214-決定)
  - [3 書き方に関する規約](#3-書き方に関する規約)
    - [3.1 Semicolons (セミコロン)](#31-semicolons-セミコロン)
    - [3.2 Line length (1行の長さ)](#32-line-length-1行の長さ)
    - [3.3 Parentheses (丸括弧)](#33-parentheses-丸括弧)
    - [3.4 Indentation (インデント)](#34-indentation-インデント)
      - [3.4.1 Trailing commas in sequences of items? (末尾のカンマ)](#341-trailing-commas-in-sequences-of-items-末尾のカンマ)
    - [3.5 Blank Lines (空行)](#35-blank-lines-空行)
    - [3.6 Whitespace (スペース)](#36-whitespace-スペース)
    - [3.7 Shebang Line (先頭行のシバン)](#37-shebang-line-先頭行のシバン)
    - [3.8 Comments and Docstrings (コメントとDocstring)](#38-comments-and-docstrings-コメントとdocstring)
      - [3.8.1 Docstrings](#381-docstrings)
      - [3.8.2 Modules (モジュール)](#382-modules-モジュール)
      - [3.8.3 Functions and Methods (関数とメソッド)](#383-functions-and-methods-関数とメソッド)
      - [3.8.4 Classes (クラス)](#384-classes-クラス)
      - [3.8.5 Block and Inline Comments (ブロックとインラインのコメント)](#385-block-and-inline-comments-ブロックとインラインのコメント)
      - [3.8.6 Punctuation, Spelling, and Grammar (カンマ，ピリオド，スペル，文法)](#386-punctuation-spelling-and-grammar-カンマピリオドスペル文法)
    - [3.10 Strings (文字列)](#310-strings-文字列)
      - [3.10.1 Logging (ログ)](#3101-logging-ログ)
      - [3.10.2 Error Messages (エラーメッセージ)](#3102-error-messages-エラーメッセージ)
    - [3.11 Files, Sockets, and similar Stateful Resources (ファイル，ソケット等のステートフルなリソース)](#311-files-sockets-and-similar-stateful-resources-ファイルソケット等のステートフルなリソース)
    - [3.12 TODO Comments (TODOコメント)](#312-todo-comments-todoコメント)
    - [3.13 Imports formatting (import文の書き方)](#313-imports-formatting-import文の書き方)
    - [3.14 Statements (ブロックを構成する最小単位)](#314-statements-ブロックを構成する最小単位)
    - [3.15 Getters and Setters (getterとsetter)](#315-getters-and-setters-getterとsetter)
    - [3.16 Naming (命名規則)](#316-naming-命名規則)
      - [3.16.1 Names to Avoid (割けるべき名前)](#3161-names-to-avoid-割けるべき名前)
      - [3.16.2 Naming Conventions](#3162-naming-conventions)
      - [3.16.3 File Naming (ファイル名)](#3163-file-naming-ファイル名)
      - [3.16.4 Guidelines derived from Guido's Recommendations ([Guido](https://en.wikipedia.org/wiki/Guido_van_Rossum)の推奨を基にしたガイドライン)](#3164-guidelines-derived-from-guidos-recommendations-guidoの推奨を基にしたガイドライン)
      - [3.16.5 Mathematical Notation (数学表記)](#3165-mathematical-notation-数学表記)
    - [3.17 Main (main文)](#317-main-main文)
    - [3.18 Function length (関数の長さ)](#318-function-length-関数の長さ)
    - [3.19 Type Annotations (型ヒント)](#319-type-annotations-型ヒント)
      - [3.19.1 General Rules (一般的なルール)](#3191-general-rules-一般的なルール)
      - [3.19.2 Line Breaking (改行)](#3192-line-breaking-改行)
      - [3.19.3 Forward Declarations (前方宣言)](#3193-forward-declarations-前方宣言)
      - [3.19.4 Default Values (デフォルト値)](#3194-default-values-デフォルト値)
      - [3.19.5 NoneType (`NoneType`)](#3195-nonetype-nonetype)
      - [3.19.6 Type Aliases (型エイリアス)](#3196-type-aliases-型エイリアス)
      - [3.19.7 Ignoring Types (型の無視)](#3197-ignoring-types-型の無視)
      - [3.19.8 Typing Variables (変数の型付け)](#3198-typing-variables-変数の型付け)
      - [3.19.9 Tuples vs Lists (tupleとlist)](#3199-tuples-vs-lists-tupleとlist)
      - [3.19.10 TypeVars (`TypeVar`)](#31910-typevars-typevar)
      - [3.19.11 String types (文字列型)](#31911-string-types-文字列型)
      - [3.19.12 Imports For Typing (型付けのためのimport)](#31912-imports-for-typing-型付けのためのimport)
      - [3.19.13 Conditional Imports (条件付きimport)](#31913-conditional-imports-条件付きimport)
      - [3.19.14 Circular Dependencies (循環import依存)](#31914-circular-dependencies-循環import依存)
      - [3.19.15 Generics (ジェネリクス？)](#31915-generics-ジェネリクス)
  - [4 おわりに](#4-おわりに)

</details>

<a id="s1-background"></a>
<a id="1-background"></a>

<a id="background"></a>
## 1 背景

Python is the main dynamic language used at Google. This style guide is a list of dos and don'ts for Python programs.  
PythonはGoogleで使われている主要な動的言語です．
このスタイルガイドはPythonでプログラミングをする際の *べき集・べからず集* のリストです．

To help you format code correctly, we've created a [settings file for Vim](google_python_style.vim). For Emacs, the default settings should be fine.  
Pythonで書いたプログラムを正しく整形するために，[Vim用の設定ファイル](google_python_style.vim)を作成しました．
Emacsはデフォルトの設定で問題ありません．

Many teams use the [yapf](https://github.com/google/yapf/) auto-formatter to avoid arguing over formatting.  
多くのチームが自動整形に[yapf](https://github.com/google/yapf/)を使い，過剰な整形を避けるようにしています．

<a id="s2-python-language-rules"></a>
<a id="2-python-language-rules"></a>

<a id="python-language-rules"></a>
## 2 Pythonの言語に関する規約

<a id="s2.1-lint"></a>
<a id="21-lint"></a>

<a id="lint"></a>
### 2.1 Lint

Run `pylint` over your code using this [pylintrc](https://google.github.io/styleguide/pylintrc).  
自分が書いたプログラムを `pylint` で確認する (pylintの設定ファイルは，この [pylintrc](https://google.github.io/styleguide/pylintrc) を使う).

<a id="s2.1.1-definition"></a>
<a id="211-definition"></a>

<a id="lint-definition"></a>
#### 2.1.1 定義

`pylint` is a tool for finding bugs and style problems in Python source code. It finds problems that are typically caught by a compiler for less dynamic languages like C and C++. Because of the dynamic nature of Python, some warnings may be incorrect; however, spurious warnings should be fairly
infrequent.  
`pylint` はPythonのソースコード中のバグや書き方の問題を発見するためのツールです．
CやC++のようなあまり動的ではない言語のコンパイラによって発見される問題を見つけます．
Pythonの動的性質により一部の警告が正しくないこともあります．
ただし，誤った警告が発生することはかなりまれです．

<a id="s2.1.2-pros"></a>
<a id="212-pros"></a>

<a id="lint-pros"></a>
#### 2.1.2 利点

Catches easy-to-miss errors like typos, using-vars-before-assignment, etc.  
やりがちなミス(例: タイプミスや未定義変数の使用)を見つけてくれます．

<a id="s2.1.3-cons"></a>
<a id="213-cons"></a>

<a id="lint-cons"></a>
#### 2.1.3 欠点

`pylint` isn't perfect. To take advantage of it, sometimes we'll need to write around it, suppress its warnings or fix it.  
`pylint` は完璧ではありません．
`pylint`の利点を享受するためには，警告の抑制や修正，書き留めることが必要になるときがあります．

<a id="s2.1.4-decision"></a>
<a id="214-decision"></a>

<a id="lint-decision"></a>
#### 2.1.4 決定

Make sure you run
`pylint`
on your code.  
自分が書いたコードに対して必ず `pylint` を実行してください．

Suppress warnings if they are inappropriate so that other issues are not hidden.
To suppress warnings, you can set a line-level comment:  
不適切な警告は抑制し，その他の問題が隠れないようにしてください．
警告の抑制には，以下のように行レベルのコメント(`pylint: disable=`)を設定します．

```python
dict = 'something awful'  # Bad Idea... pylint: disable=redefined-builtin
```

`pylint` warnings are each identified by symbolic name (`empty-docstring`)
Google-specific warnings start with `g-`.  
`pylint` の警告はそれぞれ記号名で識別されます(例: `empty-docstring`)．
Google特有の警告は，接頭語として `g-` がついています.

If the reason for the suppression is not clear from the symbolic name, add an
explanation.  
記号名から抑制の理由が不明瞭な場合は，説明を追加してください．

Suppressing in this way has the advantage that we can easily search for
suppressions and revisit them.  
このような方法で抑制することで抑制の検索・再検討を容易にできます．

You can get a list of
`pylint`
warnings by doing:  
以下のコマンドを実行すると `pylint` の警告一覧を取得できます．

```shell
pylint --list-msgs
```

To get more information on a particular message, use:  
特定のメッセージに関する詳細を知りたい場合は，以下のコマンドを実行します．

```shell
pylint --help-msg=C6409
```

Prefer `pylint: disable` to the deprecated older form `pylint: disable-msg`.  
警告の抑制をする際，非推奨の古い `pylint: disable-msg` ではなく `pylint: disable` を使うようにしてください．

Unused argument warnings can be suppressed by deleting the variables at the
beginning of the function. Always include a comment explaining why you are
deleting it. "Unused." is sufficient. For example:  
未使用の変数に関する警告に関しては，関数の最初で変数を削除する抑制方法が挙げられます．
この抑制を実施する際は，必ず変数を削除する理由をコメントとして書くようにしてください．
単に "Unused." と書くだけでは不十分です．ｔ
例えば:

```python
def viking_cafe_order(spam: str, beans: str, eggs: Optional[str] = None) -> str:
    del beans, eggs  # Unused by vikings.
    return spam + spam + spam
```

Other common forms of suppressing this warning include using '`_`' as the
identifier for the unused argument or prefixing the argument name with
'`unused_`', or assigning them to '`_`'. These forms are allowed but no longer
encouraged. These break callers that pass arguments by name and do not enforce
that the arguments are actually unused.  
上記の方法以外でこの警告を抑制する一般的な方法は，未使用の変数に識別子として '`_`' を含める，'`unused_`' という接頭語を追加する， '`_`' という変数に割り当てるといった方法が挙げられます．
これらの方法は許可されていますが，推奨されなくなりました．
なぜなら，これらの方法は関数の呼び出し元を名前によって破壊し，その引数が実際に未使用であることを強制しないためです．

<a id="s2.2-imports"></a>
<a id="22-imports"></a>

<a id="imports"></a>
### 2.2 Imports

Use `import` statements for packages and modules only, not for individual
classes or functions. Classes imported from the
[`typing` module](#typing-imports), [`collections.abc` module](#typing-imports),
[`typing_extensions` module](https://github.com/python/typing/tree/master/typing_extensions),
and redirects from the
[six.moves module](https://six.readthedocs.io/#module-six.moves)
are exempt from this rule.  
`import`文はパッケージとモジュールのために使い，個別のクラスや関数のために使わないでください．
ただし，[`typing`モジュール](#typing-imports), [`collections.abc` module](#typing-imports)と
[`typing_extensions`モジュール](https://github.com/python/typing/tree/master/typing_extensions)からインポートされたクラス・関数及び
[six.movesモジュール](https://six.readthedocs.io/#module-six.moves)
からリダイレクトされたクラス・関数はこのルールから除外されます．

<a id="s2.2.1-definition"></a>
<a id="221-definition"></a>

<a id="imports-definition"></a>

#### 2.2.1 定義

Reusability mechanism for sharing code from one module to another.  
あるモジュールから別のモジュールへソースコードを共有するための再利用メカニズムです．

<a id="s2.2.2-pros"></a>
<a id="222-pros"></a>

<a id="imports-pros"></a>
#### 2.2.2 利点

The namespace management convention is simple. The source of each identifier is
indicated in a consistent way; `x.Obj` says that object `Obj` is defined in
module `x`.  
名前空間を管理する基準は単純です．
各識別子のソースは一貫して `x.Obj` という風に示され，これは `Obj` というオブジェクトが `x` というモジュールで定義されていることを意味します．

<a id="s2.2.3-cons"></a>
<a id="223-cons"></a>

<a id="imports-cons"></a>
#### 2.2.3 欠点

Module names can still collide. Some module names are inconveniently long.  
モジュールの名前が衝突したり，不便なほど長いことがあります．

<a id="s2.2.4-decision"></a>
<a id="224-decision"></a>

<a id="imports-decision"></a>
#### 2.2.4 決定

*   Use `import x` for importing packages and modules.
*   `import x` を使う: パッケージ・モジュールをimportするとき
*   Use `from x import y` where `x` is the package prefix and `y` is the module
    name with no prefix.
*   `from x import y` を使う: `x` はパッケージ名， `y` はパッケージ名なしのモジュール名
*   Use `from x import y as z` if two modules named `y` are to be imported, if
    `y` conflicts with a top-level name defined in the current module, or if `y`
    is an inconveniently long name.
*   `from x import y as z` を使う: `y` という名前のモジュールを2つimportするとき，`y` という名前が現在のモジュールで定義されているトップレベルの名前としょうとするとき，`y`が不便なほど長いとき
*   Use `import y as z` only when `z` is a standard abbreviation (e.g., `np` for
    `numpy`).
*   `import y as z` を使う: `z`が一般的な省略形であるときのみ使って良い
    (例: `numpy` を `np` とする).

For example the module `sound.effects.echo` may be imported as follows:  
例えば， `sound.effects.echo` モジュールは以下のようにimportできます．

```python
from sound.effects import echo
...
echo.EchoFilter(input, output, delay=0.7, atten=4)
```

Do not use relative names in imports. Even if the module is in the same package,
use the full package name. This helps prevent unintentionally importing a
package twice.  
import文では相対名は使用しないでください．
同じパッケージ内のモジュールであったとしても，絶対名を使っtください．
絶対名を使うことで，意図せずパッケージを二度importする事態を防げます．

<a id="s2.3-packages"></a>
<a id="23-packages"></a>

<a id="packages"></a>
### 2.3 Packages

Import each module using the full pathname location of the module.  
モジュールをimportするときは，各モジュールの絶対パスを使ってください．

<a id="s2.3.1-pros"></a>
<a id="231-pros"></a>

<a id="packages-pros"></a>
#### 2.3.1 利点

Avoids conflicts in module names or incorrect imports due to the module search
path not being what the author expected. Makes it easier to find modules.  
モジュール名の衝突やプログラマの期待と異なるモジュールの検索パスによって生じる誤ったimportを防ぐことができます．
また，絶対パスを書くことでモジュールを見つけやすくなるというメリットもありまｓ．

<a id="s2.3.2-cons"></a>
<a id="232-cons"></a>

<a id="packages-cons"></a>
#### 2.3.2 欠点

Makes it harder to deploy code because you have to replicate the package
hierarchy. Not really a problem with modern deployment mechanisms.  
パッケージを階層的に複製する必要があるため，コードのデプロイが難しくなりますが，最新のデプロイ方法を使えば実用的に問題になることはありません．

<a id="s2.3.3-decision"></a>
<a id="233-decision"></a>

<a id="packages-decision"></a>
#### 2.3.3 決定

All new code should import each module by its full package name.  
全ての新しいソースコードで各モジュールを完全なパッケージ名でimportしてください．

Imports should be as follows:  
具体的には，以下のようにimportします．

```python
Yes:
  # Reference absl.flags in code with the complete name (verbose).
  # 完全な名前(absl.flags)を参照
  import absl.flags
  from doctor.who import jodie

  _FOO = absl.flags.DEFINE_string(...)
```

```python
Yes:
  # Reference flags in code with just the module name (common).
  # モジュール名(flags)を参照
  from absl import flags
  from doctor.who import jodie

  _FOO = flags.DEFINE_string(...)
```

*(assume this file lives in `doctor/who/` where `jodie.py` also exists)*  
*(以下のコードが `doctor/who/` というディレクトリ内にあり，同じディレクトリに `jodie.py` というファイルが存在するとき)*

```python
No:
  # Unclear what module the author wanted and what will be imported.  The actual
  # import behavior depends on external factors controlling sys.path.
  # Which possible jodie module did the author intend to import?
  # コードを書いた人がimportしたいモジュールも実際にimportされるモジュールも不明瞭
  # 実際にimportされるモジュールはsys.pathを制御する外部要因に依存
  # コードを書いた人がimportしたかったjodieはどのjodieでしょうか？
  import jodie
```

The directory the main binary is located in should not be assumed to be in
`sys.path` despite that happening in some environments. This being the case,
code should assume that `import jodie` refers to a third party or top level
package named `jodie`, not a local `jodie.py`.  
`sys.path`の中にコードが保存されていると想定するべきではありません．
もちろん，そのような状況が生じることもありますが，その場合は `import jodie` と書くと，ローカルな `jodie.py`ではなく，3rd partyもしくはトップレベルのパッケージを参照していると想定されます．

<a id="s2.4-exceptions"></a>
<a id="24-exceptions"></a>

<a id="exceptions"></a>
### 2.4 Exception (例外)

Exceptions are allowed but must be used carefully.  
例外は慎重に使用しなければいけません．

<a id="s2.4.1-definition"></a>
<a id="241-definition"></a>

<a id="exceptions-definition"></a>
#### 2.4.1 定義

Exceptions are a means of breaking out of normal control flow to handle errors
or other exceptional conditions.  
Exception(例外)は，エラーやその他の例外的な状況を扱うための通常の制御フローから抜け出す方法です．

<a id="s2.4.2-pros"></a>
<a id="242-pros"></a>

<a id="exceptions-pros"></a>
#### 2.4.2 利点

The control flow of normal operation code is not cluttered by error-handling
code. It also allows the control flow to skip multiple frames when a certain
condition occurs, e.g., returning from N nested functions in one step instead of
having to plumb error codes through.  
通常の制御フローはエラー処理によって乱雑になることはありません．
ある特定の状況下で複数のフレームをスキップできるようにします．
例えば，N個のネストされた関数から抜け出す時に，
複数のエラーコードを実行する代わりに1つの処理で抜け出すといった例が挙げられます．

<a id="s2.4.3-cons"></a>
<a id="243-cons"></a>

<a id="exceptions-cons"></a>
#### 2.4.3 欠点

May cause the control flow to be confusing. Easy to miss error cases when making
library calls.  
制御フローの混乱を招く可能性があります．
ライブラリを呼び出すときに生じるエラーケースを見逃しやすくなってしまいます．

<a id="s2.4.4-decision"></a>
<a id="244-decision"></a>

<a id="exceptions-decision"></a>
#### 2.4.4 決定

Exceptions must follow certain conditions:
例外を導入するときは特定の条件に従うべきです．

-   Make use of built-in exception classes when it makes sense. For example,
    raise a `ValueError` to indicate a programming mistake like a violated
    precondition (such as if you were passed a negative number but required a
    positive one). Do not use `assert` statements for validating argument values
    of a public API. `assert` is used to ensure internal correctness, not to
    enforce correct usage nor to indicate that some unexpected event occurred.
    If an exception is desired in the latter cases, use a raise statement. For
    example:
-   必要に応じてbuilt-inの例外クラスを使ってください．例えば，前提条件に違反(負の数を渡したが正の数が必要)していれば `ValueError` を使います．
    公開APIの引数を検証する目的で `assert` 文を使わないでください．
    `assert`は内部での正しさを保証するときに使うべきで
    正しい使い方を強制したり予期せぬイベントの発生の示唆に使うべきではありません．
    後者のような状況で例外を使いたいのであれば，raise文を使ってください．例えば

    ```python
    Yes:
      def connect_to_next_port(self, minimum: int) -> int:
        """Connects to the next available port.

        Args:
          minimum: A port value greater or equal to 1024.

        Returns:
          The new minimum port.

        Raises:
          ConnectionError: If no available port is found.
        """
        if minimum < 1024:
          # Note that this raising of ValueError is not mentioned in the doc
          # string's "Raises:" section because it is not appropriate to
          # guarantee this specific behavioral reaction to API misuse.
          raise ValueError(f'Min. port must be at least 1024, not {minimum}.')
        port = self._find_next_open_port(minimum)
        if port is None:
          raise ConnectionError(
              f'Could not connect to service on port {minimum} or higher.')
        assert port >= minimum, (
            f'Unexpected port {port} when minimum was {minimum}.')
        return port
    ```

    ```python
    No:
      def connect_to_next_port(self, minimum: int) -> int:
        """Connects to the next available port.

        Args:
          minimum: A port value greater or equal to 1024.

        Returns:
          The new minimum port.
        """
        assert minimum >= 1024, 'Minimum port must be at least 1024.'
        port = self._find_next_open_port(minimum)
        assert port is not None
        return port
    ```


-   Libraries or packages may define their own exceptions. When doing so they
    must inherit from an existing exception class. Exception names should end in
    `Error` and should not introduce repetition (`foo.FooError`).
-   ライブラリやパッケージは独自の例外を定義することがあります．
    その場合は既存の例外クラスから継承する必要があります．
    例外名は接尾語として `Error` をつけ，`foo.FooError`のような繰り返しは避けるべきです.

-   Never use catch-all `except:` statements, or catch `Exception` or
-   以下の状況を除いて，全ての`except:`文をキャッチすることや`Exception` もしくは `StandardError` をキャッチすることはやめてください．
    -   re-raising the exception, or
    -   その例外を再び発生させたいとき
    -   creating an isolation point in the program where exceptions are not
        propagated but are recorded and suppressed instead, such as protecting a
        thread from crashing by guarding its outermost block.
   -    例外が伝搬しないが記録され，代わりに抑制され，プログラム中に孤立点を作るとき
        スレッドをクラッシュから守るために最も齟齬タワのブロックを保護するようなとき

    Python is very tolerant in this regard and `except:` will really catch
    everything including misspelled names, sys.exit() calls, Ctrl+C interrupts,
    unittest failures and all kinds of other exceptions that you simply don't
    want to catch.  
    Pythonはこの観点でとても柔軟な言語であり，
    `except:`文は名前のタイプミスやsys.exit()の呼び出し，
    Ctrl+Cの割り込み，ユニットテストの失敗など，
    キャッチしたくない全ての例外をキャッチします．

-   Minimize the amount of code in a `try`/`except` block. The larger the body
    of the `try`, the more likely that an exception will be raised by a line of
    code that you didn't expect to raise an exception. In those cases, the
    `try`/`except` block hides a real error.
-   `try`/`except`ブロック内に書いてある文章を最小化してください．
     `try`文が巨大になるほど, 例外の発生を期待していない部分で例外が発生してしまいます．
     このようになってしまうと，`try`/`except`ブロックが実際の問題を隠してしまうことになります．

-   Use the `finally` clause to execute code whether or not an exception is
    raised in the `try` block. This is often useful for cleanup, i.e., closing a
    file.
-   `try`ブロック内でのraiseの有無に関わらず，`finally`文を使ってください．
-   クリーンアップのために有効です (例: ファイルを閉じる)．

<a id="s2.5-global-variables"></a>
<a id="25-global-variables"></a>

<a id="global-variables"></a>
### 2.5 Global variables (グローバル変数)

Avoid global variables.  
グローバル変数の使用は避けてください．

<a id="s2.5.1-definition"></a>
<a id="251-definition"></a>

<a id="global-variables-definition"></a>
#### 2.5.1 定義

Variables that are declared at the module level or as class attributes.  
グローバル変数とは，モジュールレベルで宣言した変数やクラス属性として宣言した変数を指します．

<a id="s2.5.2-pros"></a>
<a id="252-pros"></a>

<a id="global-variables-pros"></a>
#### 2.5.2 利点

Occasionally useful.  
有用なこともあります．

<a id="s2.5.3-cons"></a>
<a id="253-cons"></a>

<a id="global-variables-cons"></a>
#### 2.5.3 欠点

Has the potential to change module behavior during the import, because
assignments to global variables are done when the module is first imported.  
importのタイミングでモジュールの挙動を変えてしまう可能性があります．
なぜなら，グローバル変数への割当はモジュールが最初にimportされる時に実行されるからです．

<a id="s2.5.4-decision"></a>
<a id="254-decision"></a>

<a id="global-variables-decision"></a>
#### 2.5.4 決定

Avoid global variables.  
グローバル変数の使用は避けてください．

If needed, global variables should be declared at the module level and made
internal to the module by prepending an `_` to the name. External access to
global variables must be done through public module-level functions. See
[Naming](#s3.16-naming) below.  
必要な場合は，モジュールレベルで宣言し，変数名に `_` をつけてモジュール内でのみ使用することを明らかにするべきです．
モジュール外からグローバル変数にアクセスする方法はpublicなモジュールレベルの関数を介して行わうようにしなければいけません．
変数名の詳細は[Naming](#s3.16-naming)を参照してください．

While module-level constants are technically variables, they are permitted and
encouraged. For example: `MAX_HOLY_HANDGRENADE_COUNT = 3`. Constants must be
named using all caps with underscores. See [Naming](#s3.16-naming) below.
モジュールレベルの定数は変数として宣言することになりますが，この方法は推奨されています．
例えば， `MAX_HOLY_HANDGRENADE_COUNT = 3`などとします．
定数名は大文字とアンダースコアのみで構成します．
変数名の詳細は[Naming](#s3.16-naming)を参照してください．

<a id="s2.6-nested"></a>
<a id="26-nested"></a>

<a id="nested-classes-functions"></a>
### 2.6 Nested/Local/Inner Classes and Functions (ネストされたローカル/内部クラスと関数)

Nested local functions or classes are fine when used to close over a local
variable. Inner classes are fine.  
ネストされたローカル関数やローカルクラスの使用は，ローカル変数に関して閉じているのであれば問題ありません．
内部クラスの使用も問題ありません．

<a id="s2.6.1-definition"></a>
<a id="261-definition"></a>

<a id="nested-classes-functions-definition"></a>
#### 2.6.1 定義

A class can be defined inside of a method, function, or class. A function can be
defined inside a method or function. Nested functions have read-only access to
variables defined in enclosing scopes.  
メソッド，関数，クラスの内部でクラスを定義できます．
メソッド，関数の内部で関数を定義できます．
ネストされた関数は閉じたスコープの中で定義された変数への読み取り権限のみを持ちます．

<a id="s2.6.2-pros"></a>
<a id="262-pros"></a>

<a id="nested-classes-functions-pros"></a>
#### 2.6.2 利点

Allows definition of utility classes and functions that are only used inside of
a very limited scope. Very
[ADT](http://www.google.com/url?sa=D&q=http://en.wikipedia.org/wiki/Abstract_data_type)-y.
Commonly used for implementing decorators.  
とても限定されたスコープ内でのみ使用可能な便利クラス・関数を定義することができます．
とても抽象データ型といえます．
デコレータを実装するときに一般的に使われます．

<a id="s2.6.3-cons"></a>
<a id="263-cons"></a>

<a id="nested-classes-functions-cons"></a>
#### 2.6.3 欠点

Nested functions and classes cannot be directly tested. Nesting can make the
outer function longer and less readable.  
ネストされた関数・クラスは直接テストできません．
ネストすることで，外部の関数の実装が長くなってしまったり，可読性を失ってしまうことになります．

<a id="s2.6.4-decision"></a>
<a id="264-decision"></a>

<a id="nested-classes-functions-decision"></a>
#### 2.6.4 決定

They are fine with some caveats. Avoid nested functions or classes except when
closing over a local value other than `self` or `cls`. Do not nest a function
just to hide it from users of a module. Instead, prefix its name with an \_ at
the module level so that it can still be accessed by tests.  
いくつか注意点があります．
`self` か `cls` が関係するローカル変数で閉じている場合を除いて，ネストされた関数・クラスの使用は避けてください．
モジュールを使用する人から隠すためだけに使用するべきではありません．
その場合は，モジュールレベルで接頭語に \_ を追加してください．
そうすることで，テスト時にアクセスことができます．

<a id="s2.7-comprehensions"></a>
<a id="s2.7-list_comprehensions"></a>
<a id="27-list_comprehensions"></a>
<a id="list_comprehensions"></a>
<a id="list-comprehensions"></a>

<a id="comprehensions"></a>
### 2.7 Comprehensions & Generator Expressions (内包表記とジェネレータ式)

Okay to use for simple cases.

<a id="s2.7.1-definition"></a>
<a id="271-definition"></a>

<a id="comprehensions-definition"></a>
#### 2.7.1 定義

List, Dict, and Set comprehensions as well as generator expressions provide a
concise and efficient way to create container types and iterators without
resorting to the use of traditional loops, `map()`, `filter()`, or `lambda`.

<a id="s2.7.2-pros"></a>
<a id="272-pros"></a>

<a id="comprehensions-pros"></a>
#### 2.7.2 利点

Simple comprehensions can be clearer and simpler than other dict, list, or set
creation techniques. Generator expressions can be very efficient, since they
avoid the creation of a list entirely.

<a id="s2.7.3-cons"></a>
<a id="273-cons"></a>

<a id="comprehensions-cons"></a>
#### 2.7.3 欠点

Complicated comprehensions or generator expressions can be hard to read.

<a id="s2.7.4-decision"></a>
<a id="274-decision"></a>

<a id="comprehensions-decision"></a>
#### 2.7.4 決定

Okay to use for simple cases. Each portion must fit on one line: mapping
expression, `for` clause, filter expression. Multiple `for` clauses or filter
expressions are not permitted. Use loops instead when things get more
complicated.

```python
Yes:
  result = [mapping_expr for value in iterable if filter_expr]

  result = [{'key': value} for value in iterable
            if a_long_filter_expression(value)]

  result = [complicated_transform(x)
            for x in iterable if predicate(x)]

  descriptive_name = [
      transform({'key': key, 'value': value}, color='black')
      for key, value in generate_iterable(some_input)
      if complicated_condition_is_met(key, value)
  ]

  result = []
  for x in range(10):
      for y in range(5):
          if x * y > 10:
              result.append((x, y))

  return {x: complicated_transform(x)
          for x in long_generator_function(parameter)
          if x is not None}

  squares_generator = (x**2 for x in range(10))

  unique_names = {user.name for user in users if user is not None}

  eat(jelly_bean for jelly_bean in jelly_beans
      if jelly_bean.color == 'black')
```

```python
No:
  result = [complicated_transform(
                x, some_argument=x+1)
            for x in iterable if predicate(x)]

  result = [(x, y) for x in range(10) for y in range(5) if x * y > 10]

  return ((x, y, z)
          for x in range(5)
          for y in range(5)
          if x != y
          for z in range(5)
          if y != z)
```

<a id="s2.8-default-iterators-and-operators"></a>

<a id="default-iterators-operators"></a>
### 2.8 Default Iterators and Operators (デフォルトのイテレータとオペレータ)

Use default iterators and operators for types that support them, like lists,
dictionaries, and files.

<a id="s2.8.1-definition"></a>
<a id="281-definition"></a>

<a id="default-iterators-operators-definition"></a>
#### 2.8.1 定義

Container types, like dictionaries and lists, define default iterators and
membership test operators ("in" and "not in").

<a id="s2.8.2-pros"></a>
<a id="282-pros"></a>

<a id="default-iterators-operators-pros"></a>
#### 2.8.2 利点

The default iterators and operators are simple and efficient. They express the
operation directly, without extra method calls. A function that uses default
operators is generic. It can be used with any type that supports the operation.

<a id="s2.8.3-cons"></a>
<a id="283-cons"></a>

<a id="default-iterators-operators-cons"></a>
#### 2.8.3 欠点

You can't tell the type of objects by reading the method names (e.g. `has_key()`
means a dictionary). This is also an advantage.

<a id="s2.8.4-decision"></a>
<a id="284-decision"></a>

<a id="default-iterators-operators-decision"></a>
#### 2.8.4 決定

Use default iterators and operators for types that support them, like lists,
dictionaries, and files. The built-in types define iterator methods, too. Prefer
these methods to methods that return lists, except that you should not mutate a
container while iterating over it.

```python
Yes:  for key in adict: ...
      if key not in adict: ...
      if obj in alist: ...
      for line in afile: ...
      for k, v in adict.items(): ...
      for k, v in six.iteritems(adict): ...
```

```python
No:   for key in adict.keys(): ...
      if not adict.has_key(key): ...
      for line in afile.readlines(): ...
      for k, v in dict.iteritems(): ...
```

<a id="s2.9-generators"></a>
<a id="29-generators"></a>

<a id="generators"></a>
### 2.9 Generators (ジェネレータ)

Use generators as needed.

<a id="s2.9.1-definition"></a>
<a id="291-definition"></a>

<a id="generators-definition"></a>
#### 2.9.1 定義

A generator function returns an iterator that yields a value each time it
executes a yield statement. After it yields a value, the runtime state of the
generator function is suspended until the next value is needed.

<a id="s2.9.2-pros"></a>
<a id="292-pros"></a>

<a id="generators-pros"></a>
#### 2.9.2 利点

Simpler code, because the state of local variables and control flow are
preserved for each call. A generator uses less memory than a function that
creates an entire list of values at once.

<a id="s2.9.3-cons"></a>
<a id="293-cons"></a>

<a id="generators-cons"></a>
#### 2.9.3 欠点

None.

<a id="s2.9.4-decision"></a>
<a id="294-decision"></a>

<a id="generators-decision"></a>
#### 2.9.4 決定

Fine. Use "Yields:" rather than "Returns:" in the docstring for generator
functions.

<a id="s2.10-lambda-functions"></a>
<a id="210-lambda-functions"></a>

<a id="lambdas"></a>
### 2.10 Lambda Functions (ラムダ関数)

Okay for one-liners. Prefer generator expressions over `map()` or `filter()`
with a `lambda`.

<a id="s2.10.1-definition"></a>
<a id="2101-definition"></a>

<a id="lambdas-definition"></a>
#### 2.10.1 定義

Lambdas define anonymous functions in an expression, as opposed to a statement.

<a id="s2.10.2-pros"></a>
<a id="2102-pros"></a>

<a id="lambdas-pros"></a>
#### 2.10.2 利点

Convenient.

<a id="s2.10.3-cons"></a>
<a id="2103-cons"></a>

<a id="lambdas-cons"></a>
#### 2.10.3 欠点

Harder to read and debug than local functions. The lack of names means stack
traces are more difficult to understand. Expressiveness is limited because the
function may only contain an expression.

<a id="s2.10.4-decision"></a>
<a id="2104-decision"></a>

<a id="lambdas-decision"></a>
#### 2.10.4 決定

Okay to use them for one-liners. If the code inside the lambda function is
longer than 60-80 chars, it's probably better to define it as a regular
[nested function](#lexical-scoping).

For common operations like multiplication, use the functions from the `operator`
module instead of lambda functions. For example, prefer `operator.mul` to
`lambda x, y: x * y`.

<a id="s2.11-conditional-expressions"></a>
<a id="211-conditional-expressions"></a>

<a id="conditional-expressions"></a>
### 2.11 Conditional Expressions (条件式)

Okay for simple cases.

<a id="s2.11.1-definition"></a>
<a id="2111-definition"></a>

<a id="conditional-expressions-definition"></a>
#### 2.11.1 定義

Conditional expressions (sometimes called a “ternary operator”) are mechanisms
that provide a shorter syntax for if statements. For example: `x = 1 if cond
else 2`.

<a id="s2.11.2-pros"></a>
<a id="2112-pros"></a>

<a id="conditional-expressions-pros"></a>
#### 2.11.2 利点

Shorter and more convenient than an if statement.

<a id="s2.11.3-cons"></a>
<a id="2113-cons"></a>

<a id="conditional-expressions-cons"></a>
#### 2.11.3 欠点

May be harder to read than an if statement. The condition may be difficult to
locate if the expression is long.

<a id="s2.11.4-decision"></a>
<a id="2114-decision"></a>

<a id="conditional-expressions-decision"></a>
#### 2.11.4 決定

Okay to use for simple cases. Each portion must fit on one line:
true-expression, if-expression, else-expression. Use a complete if statement
when things get more complicated.

```python
Yes:
    one_line = 'yes' if predicate(value) else 'no'
    slightly_split = ('yes' if predicate(value)
                      else 'no, nein, nyet')
    the_longest_ternary_style_that_can_be_done = (
        'yes, true, affirmative, confirmed, correct'
        if predicate(value)
        else 'no, false, negative, nay')
```

```python
No:
    bad_line_breaking = ('yes' if predicate(value) else
                         'no')
    portion_too_long = ('yes'
                        if some_long_module.some_long_predicate_function(
                            really_long_variable_name)
                        else 'no, false, negative, nay')
```

<a id="s2.12-default-argument-values"></a>
<a id="212-default-argument-values"></a>

<a id="default-arguments"></a>
### 2.12 Default Argument Values (引数のデフォルト値)

Okay in most cases.

<a id="s2.12.1-definition"></a>
<a id="2121-definition"></a>

<a id="default-arguments-definition"></a>
#### 2.12.1 定義

You can specify values for variables at the end of a function's parameter list,
e.g., `def foo(a, b=0):`. If `foo` is called with only one argument, `b` is set
to 0. If it is called with two arguments, `b` has the value of the second
argument.

<a id="s2.12.2-pros"></a>
<a id="2122-pros"></a>

<a id="default-arguments-pros"></a>
#### 2.12.2 利点

Often you have a function that uses lots of default values, but on rare
occasions you want to override the defaults. Default argument values provide an
easy way to do this, without having to define lots of functions for the rare
exceptions. As Python does not support overloaded methods/functions, default
arguments are an easy way of "faking" the overloading behavior.

<a id="s2.12.3-cons"></a>
<a id="2123-cons"></a>

<a id="default-arguments-cons"></a>
#### 2.12.3 欠点

Default arguments are evaluated once at module load time. This may cause
problems if the argument is a mutable object such as a list or a dictionary. If
the function modifies the object (e.g., by appending an item to a list), the
default value is modified.

<a id="s2.12.4-decision"></a>
<a id="2124-decision"></a>

<a id="default-arguments-decision"></a>
#### 2.12.4 決定

Okay to use with the following caveat:

Do not use mutable objects as default values in the function or method
definition.

```python
Yes: def foo(a, b=None):
         if b is None:
             b = []
Yes: def foo(a, b: Optional[Sequence] = None):
         if b is None:
             b = []
Yes: def foo(a, b: Sequence = ()):  # Empty tuple OK since tuples are immutable
         ...
```

```python
from absl import flags
_FOO = flags.DEFINE_string(...)

No:  def foo(a, b=[]):
         ...
No:  def foo(a, b=time.time()):  # The time the module was loaded???
         ...
No:  def foo(a, b=_FOO.value):  # sys.argv has not yet been parsed...
         ...
No:  def foo(a, b: Mapping = {}):  # Could still get passed to unchecked code
         ...
```

<a id="s2.13-properties"></a>
<a id="213-properties"></a>

<a id="properties"></a>
### 2.13 Properties (プロパティ)

Properties may be used to control getting or setting attributes that require
trivial computations or logic. Property implementations must match the general
expectations of regular attribute access: that they are cheap, straightforward,
and unsurprising.

<a id="s2.13.1-definition"></a>
<a id="2131-definition"></a>

<a id="properties-definition"></a>
#### 2.13.1 定義

A way to wrap method calls for getting and setting an attribute as a standard
attribute access.

<a id="s2.13.2-pros"></a>
<a id="2132-pros"></a>

<a id="properties-pros"></a>
#### 2.13.2 利点

*   Allows for an attribute access and assignment API rather than
    [getter and setter](#getters-and-setters) method calls.
*   Can be used to make an attribute read-only.
*   Allows calculations to be lazy.
*   Provides a way to maintain the public interface of a class when the
    internals evolve independently of class users.

<a id="s2.13.3-cons"></a>
<a id="2133-cons"></a>

<a id="properties-cons"></a>
#### 2.13.3 欠点

*   Can hide side-effects much like operator overloading.
*   Can be confusing for subclasses.

<a id="s2.13.4-decision"></a>
<a id="2134-decision"></a>

<a id="properties-decision"></a>
#### 2.13.4 決定

Properties are allowed, but, like operator overloading, should only be used when
necessary and match the expectations of typical attribute access; follow the
[getters and setters](#getters-and-setters) rules otherwise.

For example, using a property to simply both get and set an internal attribute
isn't allowed: there is no computation occurring, so the property is unnecessary
([make the attribute public instead](#getters-and-setters)). In comparison,
using a property to control attribute access or to calculate a *trivially*
derived value is allowed: the logic is simple and unsurprising.

Properties should be created with the `@property`
[decorator](#s2.17-function-and-method-decorators). Manually implementing a
property descriptor is considered a [power feature](#power-features).

Inheritance with properties can be non-obvious. Do not use properties to
implement computations a subclass may ever want to override and extend.

<a id="s2.14-truefalse-evaluations"></a>
<a id="214-truefalse-evaluations"></a>

<a id="truefalse-evaluations"></a>
### 2.14 True/False Evaluations (真偽の評価)

Use the "implicit" false if at all possible.

<a id="s2.14.1-definition"></a>
<a id="2141-definition"></a>

<a id="truefalse-evaluations-definition"></a>
#### 2.14.1 定義

Python evaluates certain values as `False` when in a boolean context. A quick
"rule of thumb" is that all "empty" values are considered false, so `0, None,
[], {}, ''` all evaluate as false in a boolean context.

<a id="s2.14.2-pros"></a>
<a id="2142-pros"></a>

<a id="truefalse-evaluations-pros"></a>
#### 2.14.2 利点

Conditions using Python booleans are easier to read and less error-prone. In
most cases, they're also faster.

<a id="s2.14.3-cons"></a>
<a id="2143-cons"></a>

<a id="truefalse-evaluations-cons"></a>
#### 2.14.3 欠点

May look strange to C/C++ developers.

<a id="s2.14.4-decision"></a>
<a id="2144-decision"></a>

<a id="truefalse-evaluations-decision"></a>
#### 2.14.4 決定

Use the "implicit" false if possible, e.g., `if foo:` rather than `if foo !=
[]:`. There are a few caveats that you should keep in mind though:

-   Always use `if foo is None:` (or `is not None`) to check for a `None` value.
    E.g., when testing whether a variable or argument that defaults to `None`
    was set to some other value. The other value might be a value that's false
    in a boolean context!

-   Never compare a boolean variable to `False` using `==`. Use `if not x:`
    instead. If you need to distinguish `False` from `None` then chain the
    expressions, such as `if not x and x is not None:`.

-   For sequences (strings, lists, tuples), use the fact that empty sequences
    are false, so `if seq:` and `if not seq:` are preferable to `if len(seq):`
    and `if not len(seq):` respectively.

-   When handling integers, implicit false may involve more risk than benefit
    (i.e., accidentally handling `None` as 0). You may compare a value which is
    known to be an integer (and is not the result of `len()`) against the
    integer 0.

    ```python
    Yes: if not users:
             print('no users')

         if i % 10 == 0:
             self.handle_multiple_of_ten()

         def f(x=None):
             if x is None:
                 x = []
    ```

    ```python
    No:  if len(users) == 0:
             print('no users')

         if not i % 10:
             self.handle_multiple_of_ten()

         def f(x=None):
             x = x or []
    ```

-   Note that `'0'` (i.e., `0` as string) evaluates to true.

-   Note that Numpy arrays may raise an exception in an implicit boolean
    context. Prefer the `.size` attribute when testing emptiness of a `np.array`
    (e.g. `if not users.size`).

<a id="s2.16-lexical-scoping"></a>
<a id="216-lexical-scoping"></a>

<a id="lexical-scoping"></a>
### 2.16 Lexical Scoping (レキシカルスコープ)

Okay to use.

<a id="s2.16.1-definition"></a>
<a id="2161-definition"></a>

<a id="lexical-scoping-definition"></a>
#### 2.16.1 定義

A nested Python function can refer to variables defined in enclosing functions,
but cannot assign to them. Variable bindings are resolved using lexical scoping,
that is, based on the static program text. Any assignment to a name in a block
will cause Python to treat all references to that name as a local variable, even
if the use precedes the assignment. If a global declaration occurs, the name is
treated as a global variable.

An example of the use of this feature is:

```python
def get_adder(summand1: float) -> Callable[[float], float]:
    """Returns a function that adds numbers to a given number."""
    def adder(summand2: float) -> float:
        return summand1 + summand2

    return adder
```

<a id="s2.16.2-pros"></a>
<a id="2162-pros"></a>

<a id="lexical-scoping-pros"></a>
#### 2.16.2 利点

Often results in clearer, more elegant code. Especially comforting to
experienced Lisp and Scheme (and Haskell and ML and ...) programmers.

<a id="s2.16.3-cons"></a>
<a id="2163-cons"></a>

<a id="lexical-scoping-cons"></a>
#### 2.16.3 欠点

Can lead to confusing bugs. Such as this example based on
[PEP-0227](http://www.google.com/url?sa=D&q=http://www.python.org/dev/peps/pep-0227/):

```python
i = 4
def foo(x: Iterable[int]):
    def bar():
        print(i, end='')
    # ...
    # A bunch of code here
    # ...
    for i in x:  # Ah, i *is* local to foo, so this is what bar sees
        print(i, end='')
    bar()
```

So `foo([1, 2, 3])` will print `1 2 3 3`,
not `1 2 3 4`.

<a id="s2.16.4-decision"></a>
<a id="2164-decision"></a>

<a id="lexical-scoping-decision"></a>
#### 2.16.4 決定

Okay to use.

<a id="s2.17-function-and-method-decorators"></a>
<a id="217-function-and-method-decorators"></a>
<a id="function-and-method-decorators"></a>

<a id="decorators"></a>
### 2.17 Function and Method Decorators (デコレータ)

Use decorators judiciously when there is a clear advantage. Avoid `staticmethod`
and limit use of `classmethod`.

<a id="s2.17.1-definition"></a>
<a id="2171-definition"></a>

<a id="decorators-definition"></a>
#### 2.17.1 定義

[Decorators for Functions and Methods](https://docs.python.org/3/glossary.html#term-decorator)
(a.k.a "the `@` notation"). One common decorator is `@property`, used for
converting ordinary methods into dynamically computed attributes. However, the
decorator syntax allows for user-defined decorators as well. Specifically, for
some function `my_decorator`, this:

```python
class C:
    @my_decorator
    def method(self):
        # method body ...
```

is equivalent to:

```python
class C:
    def method(self):
        # method body ...
    method = my_decorator(method)
```

<a id="s2.17.2-pros"></a>
<a id="2172-pros"></a>

<a id="decorators-pros"></a>
#### 2.17.2 利点

Elegantly specifies some transformation on a method; the transformation might
eliminate some repetitive code, enforce invariants, etc.

<a id="s2.17.3-cons"></a>
<a id="2173-cons"></a>

<a id="decorators-cons"></a>
#### 2.17.3 欠点

Decorators can perform arbitrary operations on a function's arguments or return
values, resulting in surprising implicit behavior. Additionally, decorators
execute at object definition time. For module-level objects (classes, module
functions, ...) this happens at import time. Failures in decorator code are
pretty much impossible to recover from.

<a id="s2.17.4-decision"></a>
<a id="2174-decision"></a>

<a id="decorators-decision"></a>
#### 2.17.4 決定

Use decorators judiciously when there is a clear advantage. Decorators should
follow the same import and naming guidelines as functions. Decorator pydoc
should clearly state that the function is a decorator. Write unit tests for
decorators.

Avoid external dependencies in the decorator itself (e.g. don't rely on files,
sockets, database connections, etc.), since they might not be available when the
decorator runs (at import time, perhaps from `pydoc` or other tools). A
decorator that is called with valid parameters should (as much as possible) be
guaranteed to succeed in all cases.

Decorators are a special case of "top level code" - see [main](#s3.17-main) for
more discussion.

Never use `staticmethod` unless forced to in order to integrate with an API
defined in an existing library. Write a module level function instead.

Use `classmethod` only when writing a named constructor or a class-specific
routine that modifies necessary global state such as a process-wide cache.

<a id="s2.18-threading"></a>
<a id="218-threading"></a>

<a id="threading"></a>
### 2.18 Threading (スレッド)

Do not rely on the atomicity of built-in types.

While Python's built-in data types such as dictionaries appear to have atomic
operations, there are corner cases where they aren't atomic (e.g. if `__hash__`
or `__eq__` are implemented as Python methods) and their atomicity should not be
relied upon. Neither should you rely on atomic variable assignment (since this
in turn depends on dictionaries).

Use the Queue module's `Queue` data type as the preferred way to communicate
data between threads. Otherwise, use the threading module and its locking
primitives. Prefer condition variables and `threading.Condition` instead of
using lower-level locks.

<a id="s2.19-power-features"></a>
<a id="219-power-features"></a>

<a id="power-features"></a>
### 2.19 Power Features 

Avoid these features.

<a id="s2.19.1-definition"></a>
<a id="2191-definition"></a>

<a id="power-features-definition"></a>
#### 2.19.1 定義

Python is an extremely flexible language and gives you many fancy features such
as custom metaclasses, access to bytecode, on-the-fly compilation, dynamic
inheritance, object reparenting, import hacks, reflection (e.g. some uses of
`getattr()`), modification of system internals, `__del__` methods implementing
customized cleanup, etc.

<a id="s2.19.2-pros"></a>
<a id="2192-pros"></a>

<a id="power-features-pros"></a>
#### 2.19.2 利点

These are powerful language features. They can make your code more compact.

<a id="s2.19.3-cons"></a>
<a id="2193-cons"></a>

<a id="power-features-cons"></a>
#### 2.19.3 欠点

It's very tempting to use these "cool" features when they're not absolutely
necessary. It's harder to read, understand, and debug code that's using unusual
features underneath. It doesn't seem that way at first (to the original author),
but when revisiting the code, it tends to be more difficult than code that is
longer but is straightforward.

<a id="s2.19.4-decision"></a>
<a id="2194-decision"></a>

<a id="power-features-decision"></a>
#### 2.19.4 決定

Avoid these features in your code.

Standard library modules and classes that internally use these features are okay
to use (for example, `abc.ABCMeta`, `dataclasses`, and `enum`).

<a id="s2.20-modern-python"></a>
<a id="220-modern-python"></a>

<a id="modern-python"></a>
### 2.20 Modern Python: from \_\_future\_\_ imports (\_\_future\_\_ からimportできるモダンな機能)

New language version semantic changes may be gated behind a special future
import to enable them on a per-file basis within earlier runtimes.

<a id="s2.20.1-definition"></a>
<a id="2201-definition"></a>

<a id="modern-python-definition"></a>
#### 2.20.1 定義

Being able to turn on some of the more modern features via `from __future__
import` statements allows early use of features from expected future Python
versions.

<a id="s2.20.2-pros"></a>
<a id="2202-pros"></a>

<a id="modern-python-pros"></a>
#### 2.20.2 利点

This has proven to make runtime version upgrades smoother as changes can be made
on a per-file basis while declaring compatibility and preventing regressions
within those files. Modern code is more maintainable as it is less likely to
accumulate technical debt that will be problematic during future runtime
upgrades.

<a id="s2.20.3-cons"></a>
<a id="2203-cons"></a>

<a id="modern-python-cons"></a>
#### 2.20.3 欠点

Such code may not work on very old interpreter versions prior to the
introduction of the needed future statement. The need for this is more common in
projects supporting an extremely wide variety of environments.

<a id="s2.20.4-decision"></a>
<a id="2204-decision"></a>

<a id="modern-python-decision"></a>
#### 2.20.4 決定

##### from \_\_future\_\_ imports

Use of `from __future__ import` statements is encouraged. It allows a given
source file to start using more modern Python syntax features today. Once you no
longer need to run on a version where the features are hidden behind a
`__future__` import, feel free to remove those lines.

In code that may execute on versions as old as 3.5 rather than >= 3.7, import:

```python
from __future__ import generator_stop
```

For legacy code with the burden of continuing to support 2.7, import:

```python
from __future__ import absolute_import
from __future__ import division
from __future__ import print_function
```

For more information read the
[Python future statement definitions](https://docs.python.org/3/library/__future__.html)
documentation.

Please don't remove these imports until you are confident the code is only ever
used in a sufficiently modern environment. Even if you do not currently use the
feature a specific future import enables in your code today, keeping it in place
in the file prevents later modifications of the code from inadvertently
depending on the older behavior.

Use other `from __future__` import statements as you see fit. We did not include
`unicode_literals` in our recommendations for 2.7 as it was not a clear win due
to implicit default codec conversion consequences it introduced in many places
within 2.7. Most dual-version 2-and-3 code was better off with explicit use of
`b''` and `u''` bytes and unicode string literals where necessary.

##### The six, future, and past libraries

When your project still needs to support use under both Python 2 and 3, use the
[six](https://pypi.org/project/six/),
[future](https://pypi.org/project/future/), and
[past](https://pypi.org/project/past/) libraries as you see fit. They exist to
make your code cleaner and life easier.

<a id="s2.21-type-annotated-code"></a>
<a id="s2.21-typed-code"></a>
<a id="221-type-annotated-code"></a>
<a id="typed-code"></a>

<a id="typed-code"></a>
### 2.21 Type Annotated Code (型ヒント)

You can annotate Python 3 code with type hints according to
[PEP-484](https://www.python.org/dev/peps/pep-0484/), and type-check the code at
build time with a type checking tool like [pytype](https://github.com/google/pytype).


Type annotations can be in the source or in a
[stub pyi file](https://www.python.org/dev/peps/pep-0484/#stub-files). Whenever
possible, annotations should be in the source. Use pyi files for third-party or
extension modules.


<a id="s2.21.1-definition"></a>
<a id="2211-definition"></a>

<a id="typed-code-definition"></a>
#### 2.21.1 定義

Type annotations (or "type hints") are for function or method arguments and
return values:

```python
def func(a: int) -> list[int]:
```

You can also declare the type of a variable using similar
[PEP-526](https://www.python.org/dev/peps/pep-0526/) syntax:

```python
a: SomeType = some_func()
```

<a id="s2.21.2-pros"></a>
<a id="2212-pros"></a>

<a id="typed-code-pros"></a>
#### 2.21.2 利点

Type annotations improve the readability and maintainability of your code. The
type checker will convert many runtime errors to build-time errors, and reduce
your ability to use [Power Features](#power-features).

<a id="s2.21.3-cons"></a>
<a id="2213-cons"></a>

<a id="typed-code-cons"></a>
#### 2.21.3 欠点

You will have to keep the type declarations up to date.
You might see type errors that you think are
valid code. Use of a
[type checker](https://github.com/google/pytype)
may reduce your ability to use [Power Features](#power-features).

<a id="s2.21.4-decision"></a>
<a id="2214-decision"></a>

<a id="typed-code-decision"></a>
#### 2.21.4 決定

You are strongly encouraged to enable Python type analysis when updating code.
When adding or modifying public APIs, include type annotations and enable
checking via pytype in the build system. As static analysis is relatively new to
Python, we acknowledge that undesired side-effects (such as
wrongly
inferred types) may prevent adoption by some projects. In those situations,
authors are encouraged to add a comment with a TODO or link to a bug describing
the issue(s) currently preventing type annotation adoption in the BUILD file or
in the code itself as appropriate.

<a id="s3-python-style-rules"></a>
<a id="3-python-style-rules"></a>

<a id="python-style-rules"></a>
## 3 書き方に関する規約

<a id="s3.1-semicolons"></a>
<a id="31-semicolons"></a>

<a id="semicolons"></a>
### 3.1 Semicolons (セミコロン)

Do not terminate your lines with semicolons, and do not use semicolons to put
two statements on the same line.

<a id="s3.2-line-length"></a>
<a id="32-line-length"></a>

<a id="line-length"></a>
### 3.2 Line length (1行の長さ)

Maximum line length is *80 characters*.

Explicit exceptions to the 80 character limit:

-   Long import statements.
-   URLs, pathnames, or long flags in comments.
-   Long string module level constants not containing whitespace that would be
    inconvenient to split across lines such as URLs or pathnames.
    -   Pylint disable comments. (e.g.: `# pylint: disable=invalid-name`)

Do not use backslash line continuation except for `with` statements requiring
three or more context managers.

Make use of Python's
[implicit line joining inside parentheses, brackets and braces](http://docs.python.org/reference/lexical_analysis.html#implicit-line-joining).
If necessary, you can add an extra pair of parentheses around an expression.

```python
Yes: foo_bar(self, width, height, color='black', design=None, x='foo',
             emphasis=None, highlight=0)

     if (width == 0 and height == 0 and
         color == 'red' and emphasis == 'strong'):
```

When a literal string won't fit on a single line, use parentheses for implicit
line joining.

```python
x = ('This will build a very long long '
     'long long long long long long string')
```

Within comments, put long URLs on their own line if necessary.

```python
Yes:  # See details at
      # http://www.example.com/us/developer/documentation/api/content/v2.0/csv_file_name_extension_full_specification.html
```

```python
No:  # See details at
     # http://www.example.com/us/developer/documentation/api/content/\
     # v2.0/csv_file_name_extension_full_specification.html
```

It is permissible to use backslash continuation when defining a `with` statement
whose expressions span three or more lines. For two lines of expressions, use a
nested `with` statement:

```python
Yes:  with very_long_first_expression_function() as spam, \
           very_long_second_expression_function() as beans, \
           third_thing() as eggs:
          place_order(eggs, beans, spam, beans)
```

```python
No:  with VeryLongFirstExpressionFunction() as spam, \
          VeryLongSecondExpressionFunction() as beans:
       PlaceOrder(beans, spam)
```

```python
Yes:  with very_long_first_expression_function() as spam:
          with very_long_second_expression_function() as beans:
              place_order(beans, spam)
```

Make note of the indentation of the elements in the line continuation examples
above; see the [indentation](#s3.4-indentation) section for explanation.

In all other cases where a line exceeds 80 characters, and the
[yapf](https://github.com/google/yapf/)
auto-formatter does not help bring the line below the limit, the line is allowed
to exceed this maximum. Authors are encouraged to manually break the line up per
the notes above when it is sensible.

<a id="s3.3-parentheses"></a>
<a id="33-parentheses"></a>

<a id="parentheses"></a>
### 3.3 Parentheses (丸括弧)

Use parentheses sparingly.

It is fine, though not required, to use parentheses around tuples. Do not use
them in return statements or conditional statements unless using parentheses for
implied line continuation or to indicate a tuple.

```python
Yes: if foo:
         bar()
     while x:
         x = bar()
     if x and y:
         bar()
     if not x:
         bar()
     # For a 1 item tuple the ()s are more visually obvious than the comma.
     onesie = (foo,)
     return foo
     return spam, beans
     return (spam, beans)
     for (x, y) in dict.items(): ...
```

```python
No:  if (x):
         bar()
     if not(x):
         bar()
     return (foo)
```

<a id="s3.4-indentation"></a>
<a id="34-indentation"></a>

<a id="indentation"></a>
### 3.4 Indentation (インデント)

Indent your code blocks with *4 spaces*.

Never use tabs or mix tabs and spaces. In cases of implied line continuation,
you should align wrapped elements either vertically, as per the examples in the
[line length](#s3.2-line-length) section; or using a hanging indent of 4 spaces,
in which case there should be nothing after the open parenthesis or bracket on
the first line.

```python
Yes:   # Aligned with opening delimiter
       foo = long_function_name(var_one, var_two,
                                var_three, var_four)
       meal = (spam,
               beans)

       # Aligned with opening delimiter in a dictionary
       foo = {
           'long_dictionary_key': value1 +
                                  value2,
           ...
       }

       # 4-space hanging indent; nothing on first line
       foo = long_function_name(
           var_one, var_two, var_three,
           var_four)
       meal = (
           spam,
           beans)

       # 4-space hanging indent in a dictionary
       foo = {
           'long_dictionary_key':
               long_dictionary_value,
           ...
       }
```

```python
No:    # Stuff on first line forbidden
       foo = long_function_name(var_one, var_two,
           var_three, var_four)
       meal = (spam,
           beans)

       # 2-space hanging indent forbidden
       foo = long_function_name(
         var_one, var_two, var_three,
         var_four)

       # No hanging indent in a dictionary
       foo = {
           'long_dictionary_key':
           long_dictionary_value,
           ...
       }
```

<a id="s3.4.1-trailing-comma"></a>
<a id="s3.4.1-trailing-commas"></a>
<a id="s3.4.1-trailing_comma"></a>
<a id="s3.4.1-trailing_commas"></a>
<a id="341-trailing_comma"></a>
<a id="341-trailing_commas"></a>
<a id="trailing_comma"></a>
<a id="trailing_commas"></a>

<a id="trailing-comma"></a>
#### 3.4.1 Trailing commas in sequences of items? (末尾のカンマ)

Trailing commas in sequences of items are recommended only when the closing
container token `]`, `)`, or `}` does not appear on the same line as the final
element. The presence of a trailing comma is also used as a hint to our Python
code auto-formatter [YAPF](https://pypi.org/project/yapf/) to direct it to auto-format the container
of items to one item per line when the `,` after the final element is present.

```python
Yes:   golomb3 = [0, 1, 3]
Yes:   golomb4 = [
           0,
           1,
           4,
           6,
       ]
```

```python
No:    golomb4 = [
           0,
           1,
           4,
           6
       ]
```

<a id="s3.5-blank-lines"></a>
<a id="35-blank-lines"></a>

<a id="blank-lines"></a>
### 3.5 Blank Lines (空行)

Two blank lines between top-level definitions, be they function or class
definitions. One blank line between method definitions and between the `class`
line and the first method. No blank line following a `def` line. Use single
blank lines as you judge appropriate within functions or methods.

Blank lines need not be anchored to the definition. For example, related
comments immediately preceding function, class, and method definitions can make
sense. Consider if your comment might be more useful as part of the docstring.

<a id="s3.6-whitespace"></a>
<a id="36-whitespace"></a>

<a id="whitespace"></a>
### 3.6 Whitespace (スペース)

Follow standard typographic rules for the use of spaces around punctuation.

No whitespace inside parentheses, brackets or braces.

```python
Yes: spam(ham[1], {'eggs': 2}, [])
```

```python
No:  spam( ham[ 1 ], { 'eggs': 2 }, [ ] )
```

No whitespace before a comma, semicolon, or colon. Do use whitespace after a
comma, semicolon, or colon, except at the end of the line.

```python
Yes: if x == 4:
         print(x, y)
     x, y = y, x
```

```python
No:  if x == 4 :
         print(x , y)
     x , y = y , x
```

No whitespace before the open paren/bracket that starts an argument list,
indexing or slicing.

```python
Yes: spam(1)
```

```python
No:  spam (1)
```

```python
Yes: dict['key'] = list[index]
```

```python
No:  dict ['key'] = list [index]
```

No trailing whitespace.

Surround binary operators with a single space on either side for assignment
(`=`), comparisons (`==, <, >, !=, <>, <=, >=, in, not in, is, is not`), and
Booleans (`and, or, not`). Use your better judgment for the insertion of spaces
around arithmetic operators (`+`, `-`, `*`, `/`, `//`, `%`, `**`, `@`).

```python
Yes: x == 1
```

```python
No:  x<1
```

Never use spaces around `=` when passing keyword arguments or defining a default
parameter value, with one exception:
[when a type annotation is present](#typing-default-values), *do* use spaces
around the `=` for the default parameter value.

```python
Yes: def complex(real, imag=0.0): return Magic(r=real, i=imag)
Yes: def complex(real, imag: float = 0.0): return Magic(r=real, i=imag)
```

```python
No:  def complex(real, imag = 0.0): return Magic(r = real, i = imag)
No:  def complex(real, imag: float=0.0): return Magic(r = real, i = imag)
```

Don't use spaces to vertically align tokens on consecutive lines, since it
becomes a maintenance burden (applies to `:`, `#`, `=`, etc.):

```python
Yes:
  foo = 1000  # comment
  long_name = 2  # comment that should not be aligned

  dictionary = {
      'foo': 1,
      'long_name': 2,
  }
```

```python
No:
  foo       = 1000  # comment
  long_name = 2     # comment that should not be aligned

  dictionary = {
      'foo'      : 1,
      'long_name': 2,
  }
```


<a id="Python_Interpreter"></a>
<a id="s3.7-shebang-line"></a>
<a id="37-shebang-line"></a>

<a id="shebang-line"></a>
### 3.7 Shebang Line (先頭行のシバン)

Most `.py` files do not need to start with a `#!` line. Start the main file of a
program with
`#!/usr/bin/env python3` (to support virtualenvs) or `#!/usr/bin/python3` per
[PEP-394](https://www.python.org/dev/peps/pep-0394/).

This line is used by the kernel to find the Python interpreter, but is ignored by Python when importing modules. It is only necessary on a file intended to be executed directly.

<a id="s3.8-comments-and-docstrings"></a>
<a id="s3.8-comments"></a>
<a id="38-comments-and-docstrings"></a>

<a id="documentation"></a>
### 3.8 Comments and Docstrings (コメントとDocstring)

Be sure to use the right style for module, function, method docstrings and
inline comments.

<a id="s3.8.1-comments-in-doc-strings"></a>
<a id="381-docstrings"></a>
<a id="comments-in-doc-strings"></a>

<a id="docstrings"></a>
#### 3.8.1 Docstrings

Python uses *docstrings* to document code. A docstring is a string that is the
first statement in a package, module, class or function. These strings can be
extracted automatically through the `__doc__` member of the object and are used
by `pydoc`.
(Try running `pydoc` on your module to see how it looks.) Always use the three
double-quote `"""` format for docstrings (per
[PEP 257](https://www.google.com/url?sa=D&q=http://www.python.org/dev/peps/pep-0257/)).
A docstring should be organized as a summary line (one physical line not
exceeding 80 characters) terminated by a period, question mark, or exclamation
point. When writing more (encouraged), this must be followed by a blank line,
followed by the rest of the docstring starting at the same cursor position as
the first quote of the first line. There are more formatting guidelines for
docstrings below.

<a id="s3.8.2-comments-in-modules"></a>
<a id="382-modules"></a>
<a id="comments-in-modules"></a>

<a id="module-docs"></a>
#### 3.8.2 Modules (モジュール)

Every file should contain license boilerplate. Choose the appropriate boilerplate for the license used by the project (for example, Apache 2.0, BSD, LGPL, GPL)

Files should start with a docstring describing the contents and usage of the
module.
```python
"""A one line summary of the module or program, terminated by a period.

Leave one blank line.  The rest of this docstring should contain an
overall description of the module or program.  Optionally, it may also
contain a brief description of exported classes and functions and/or usage
examples.

  Typical usage example:

  foo = ClassFoo()
  bar = foo.FunctionBar()
"""
```


<a id="s3.8.3-functions-and-methods"></a>
<a id="383-functions-and-methods"></a>
<a id="functions-and-methods"></a>

<a id="function-docs"></a>
#### 3.8.3 Functions and Methods (関数とメソッド)

In this section, "function" means a method, function, or generator.

A function must have a docstring, unless it meets all of the following criteria:

-   not externally visible
-   very short
-   obvious

A docstring should give enough information to write a call to the function
without reading the function's code. The docstring should describe the
function's calling syntax and its semantics, but generally not its
implementation details, unless those details are relevant to how the function is
to be used. For example, a function that mutates one of its arguments as a side
effect should note that in its docstring. Otherwise, subtle but important
details of a function's implementation that are not relevant to the caller are
better expressed as comments alongside the code than within the function's
docstring.

The docstring should be descriptive-style (`"""Fetches rows from a
Bigtable."""`) rather than imperative-style (`"""Fetch rows from a
Bigtable."""`). The docstring for a `@property` data descriptor should use the
same style as the docstring for an attribute or a
<a href="#doc-function-args">function argument</a> (`"""The Bigtable path."""`,
rather than `"""Returns the Bigtable path."""`).

A method that overrides a method from a base class may have a simple docstring
sending the reader to its overridden method's docstring, such as `"""See base
class."""`. The rationale is that there is no need to repeat in many places
documentation that is already present in the base method's docstring. However,
if the overriding method's behavior is substantially different from the
overridden method, or details need to be provided (e.g., documenting additional
side effects), a docstring with at least those differences is required on the
overriding method.

Certain aspects of a function should be documented in special sections, listed
below. Each section begins with a heading line, which ends with a colon. All
sections other than the heading should maintain a hanging indent of two or four
spaces (be consistent within a file). These sections can be omitted in cases
where the function's name and signature are informative enough that it can be
aptly described using a one-line docstring.

<a id="doc-function-args"></a>
[*Args:*](#doc-function-args)
:   List each parameter by name. A description should follow the name, and be
    separated by a colon followed by either a space or newline. If the
    description is too long to fit on a single 80-character line, use a hanging
    indent of 2 or 4 spaces more than the parameter name (be consistent with the
    rest of the docstrings in the file). The description should include required
    type(s) if the code does not contain a corresponding type annotation. If a
    function accepts `*foo` (variable length argument lists) and/or `**bar`
    (arbitrary keyword arguments), they should be listed as `*foo` and `**bar`.

<a id="doc-function-returns"></a>
[*Returns:* (or *Yields:* for generators)](#doc-function-returns)
:   Describe the type and semantics of the return value. If the function only
    returns None, this section is not required. It may also be omitted if the
    docstring starts with Returns or Yields (e.g. `"""Returns row from Bigtable
    as a tuple of strings."""`) and the opening sentence is sufficient to
    describe the return value. Do not imitate 'NumPy style'
    ([example](http://numpy.org/doc/stable/reference/generated/numpy.linalg.qr.html)),
    which frequently documents a tuple return value as if it were multiple
    return values with individual names (never mentioning the tuple). Instead,
    describe such a return value as: "Returns: A tuple (mat_a, mat_b), where
    mat_a is ..., and ...". The auxiliary names in the docstring need not
    necessarily correspond to any internal names used in the function body (as
    those are not part of the API).

<a id="doc-function-raises"></a>
[*Raises:*](#doc-function-raises)
:   List all exceptions that are relevant to the interface followed by a
    description. Use a similar exception name + colon + space or newline and
    hanging indent style as described in *Args:*. You should not document
    exceptions that get raised if the API specified in the docstring is violated
    (because this would paradoxically make behavior under violation of the API
    part of the API).

```python
def fetch_smalltable_rows(table_handle: smalltable.Table,
                          keys: Sequence[Union[bytes, str]],
                          require_all_keys: bool = False,
) -> Mapping[bytes, tuple[str, ...]]:
    """Fetches rows from a Smalltable.

    Retrieves rows pertaining to the given keys from the Table instance
    represented by table_handle.  String keys will be UTF-8 encoded.

    Args:
        table_handle: An open smalltable.Table instance.
        keys: A sequence of strings representing the key of each table
          row to fetch.  String keys will be UTF-8 encoded.
        require_all_keys: If True only rows with values set for all keys will be
          returned.

    Returns:
        A dict mapping keys to the corresponding table row data
        fetched. Each row is represented as a tuple of strings. For
        example:

        {b'Serak': ('Rigel VII', 'Preparer'),
         b'Zim': ('Irk', 'Invader'),
         b'Lrrr': ('Omicron Persei 8', 'Emperor')}

        Returned keys are always bytes.  If a key from the keys argument is
        missing from the dictionary, then that row was not found in the
        table (and require_all_keys must have been False).

    Raises:
        IOError: An error occurred accessing the smalltable.
    """
```

Similarly, this variation on `Args:` with a line break is also allowed:

```python
def fetch_smalltable_rows(table_handle: smalltable.Table,
                          keys: Sequence[Union[bytes, str]],
                          require_all_keys: bool = False,
) -> Mapping[bytes, tuple[str, ...]]:
    """Fetches rows from a Smalltable.

    Retrieves rows pertaining to the given keys from the Table instance
    represented by table_handle.  String keys will be UTF-8 encoded.

    Args:
      table_handle:
        An open smalltable.Table instance.
      keys:
        A sequence of strings representing the key of each table row to
        fetch.  String keys will be UTF-8 encoded.
      require_all_keys:
        If True only rows with values set for all keys will be returned.

    Returns:
      A dict mapping keys to the corresponding table row data
      fetched. Each row is represented as a tuple of strings. For
      example:

      {b'Serak': ('Rigel VII', 'Preparer'),
       b'Zim': ('Irk', 'Invader'),
       b'Lrrr': ('Omicron Persei 8', 'Emperor')}

      Returned keys are always bytes.  If a key from the keys argument is
      missing from the dictionary, then that row was not found in the
      table (and require_all_keys must have been False).

    Raises:
      IOError: An error occurred accessing the smalltable.
    """
```

<a id="s3.8.4-comments-in-classes"></a>
<a id="384-classes"></a>
<a id="comments-in-classes"></a>

<a id="class-docs"></a>
#### 3.8.4 Classes (クラス)

Classes should have a docstring below the class definition describing the class.
If your class has public attributes, they should be documented here in an
`Attributes` section and follow the same formatting as a
[function's `Args`](#doc-function-args) section.

```python
class SampleClass:
    """Summary of class here.

    Longer class information....
    Longer class information....

    Attributes:
        likes_spam: A boolean indicating if we like SPAM or not.
        eggs: An integer count of the eggs we have laid.
    """

    def __init__(self, likes_spam: bool = False):
        """Inits SampleClass with blah."""
        self.likes_spam = likes_spam
        self.eggs = 0

    def public_method(self):
        """Performs operation blah."""
```

<a id="s3.8.5-block-and-inline-comments"></a>
<a id="comments-in-block-and-inline"></a>
<a id="s3.8.5-comments-in-block-and-inline"></a>
<a id="385-block-and-inline-comments"></a>

<a id="comments"></a>
#### 3.8.5 Block and Inline Comments (ブロックとインラインのコメント)

The final place to have comments is in tricky parts of the code. If you're going
to have to explain it at the next [code review](http://en.wikipedia.org/wiki/Code_review),
you should comment it now. Complicated operations get a few lines of comments
before the operations commence. Non-obvious ones get comments at the end of the
line.

```python
# We use a weighted dictionary search to find out where i is in
# the array.  We extrapolate position based on the largest num
# in the array and the array size and then do binary search to
# get the exact number.

if i & (i-1) == 0:  # True if i is 0 or a power of 2.
```

To improve legibility, these comments should start at least 2 spaces away from
the code with the comment character `#`, followed by at least one space before
the text of the comment itself.

On the other hand, never describe the code. Assume the person reading the code
knows Python (though not what you're trying to do) better than you do.

```python
# BAD COMMENT: Now go through the b array and make sure whenever i occurs
# the next element is i+1
```

<!-- The next section is copied from the C++ style guide. -->

<a id="s3.8.6-punctuation-spelling-and-grammar"></a>
<a id="386-punctuation-spelling-and-grammar"></a>
<a id="spelling"></a>
<a id="punctuation"></a>
<a id="grammar"></a>

<a id="punctuation-spelling-grammar"></a>
#### 3.8.6 Punctuation, Spelling, and Grammar (カンマ，ピリオド，スペル，文法)

Pay attention to punctuation, spelling, and grammar; it is easier to read
well-written comments than badly written ones.

Comments should be as readable as narrative text, with proper capitalization and
punctuation. In many cases, complete sentences are more readable than sentence
fragments. Shorter comments, such as comments at the end of a line of code, can
sometimes be less formal, but you should be consistent with your style.

Although it can be frustrating to have a code reviewer point out that you are
using a comma when you should be using a semicolon, it is very important that
source code maintain a high level of clarity and readability. Proper
punctuation, spelling, and grammar help with that goal.

<a id="s3.10-strings"></a>
<a id="310-strings"></a>

<a id="strings"></a>
### 3.10 Strings (文字列)

Use an
[f-string](https://docs.python.org/3/reference/lexical_analysis.html#f-strings),
the `%` operator, or the `format` method for formatting strings, even when the
parameters are all strings. Use your best judgment to decide between `+` and
string formatting.

```python
Yes: x = f'name: {name}; score: {n}'
     x = '%s, %s!' % (imperative, expletive)
     x = '{}, {}'.format(first, second)
     x = 'name: %s; score: %d' % (name, n)
     x = 'name: {}; score: {}'.format(name, n)
     x = a + b
```

```python
No: x = first + ', ' + second
    x = 'name: ' + name + '; score: ' + str(n)
```

Avoid using the `+` and `+=` operators to accumulate a string within a loop. In
some conditions, accumulating a string with addition can lead to quadratic
rather than linear running time. Although common accumulations of this sort may
be optimized on CPython, that is an implementation detail. The conditions under
which an optimization applies are not easy to predict and may change. Instead,
add each substring to a list and `''.join` the list after the loop terminates,
or write each substring to an `io.StringIO` buffer. These techniques
consistently have amortized-linear run time complexity.

```python
Yes: items = ['<table>']
     for last_name, first_name in employee_list:
         items.append('<tr><td>%s, %s</td></tr>' % (last_name, first_name))
     items.append('</table>')
     employee_table = ''.join(items)
```

```python
No: employee_table = '<table>'
    for last_name, first_name in employee_list:
        employee_table += '<tr><td>%s, %s</td></tr>' % (last_name, first_name)
    employee_table += '</table>'
```

Be consistent with your choice of string quote character within a file. Pick `'`
or `"` and stick with it. It is okay to use the other quote character on a
string to avoid the need to backslash-escape quote characters within the string.

```python
Yes:
  Python('Why are you hiding your eyes?')
  Gollum("I'm scared of lint errors.")
  Narrator('"Good!" thought a happy Python reviewer.')
```

```python
No:
  Python("Why are you hiding your eyes?")
  Gollum('The lint. It burns. It burns us.')
  Gollum("Always the great lint. Watching. Watching.")
```

Prefer `"""` for multi-line strings rather than `'''`. Projects may choose to
use `'''` for all non-docstring multi-line strings if and only if they also use
`'` for regular strings. Docstrings must use `"""` regardless.

Multi-line strings do not flow with the indentation of the rest of the program.
If you need to avoid embedding extra space in the string, use either
concatenated single-line strings or a multi-line string with
[`textwrap.dedent()`](https://docs.python.org/3/library/textwrap.html#textwrap.dedent)
to remove the initial space on each line:

```python
  No:
  long_string = """This is pretty ugly.
Don't do this.
"""
```

```python
  Yes:
  long_string = """This is fine if your use case can accept
      extraneous leading spaces."""
```

```python
  Yes:
  long_string = ("And this is fine if you cannot accept\n" +
                 "extraneous leading spaces.")
```

```python
  Yes:
  long_string = ("And this too is fine if you cannot accept\n"
                 "extraneous leading spaces.")
```

```python
  Yes:
  import textwrap

  long_string = textwrap.dedent("""\
      This is also fine, because textwrap.dedent()
      will collapse common leading spaces in each line.""")
```

<a id="s3.10.1-logging"></a>
<a id="3101-logging"></a>
<a id="logging"></a>

<a id="logging"></a>
#### 3.10.1 Logging (ログ)

For logging functions that expect a pattern-string (with %-placeholders) as
their first argument: Always call them with a string literal (not an f-string!)
as their first argument with pattern-parameters as subsequent arguments. Some
logging implementations collect the unexpanded pattern-string as a queryable
field. It also prevents spending time rendering a message that no logger is
configured to output.

```python
  Yes:
  import tensorflow as tf
  logger = tf.get_logger()
  logger.info('TensorFlow Version is: %s', tf.__version__)
```

```python
  Yes:
  import os
  from absl import logging

  logging.info('Current $PAGER is: %s', os.getenv('PAGER', default=''))

  homedir = os.getenv('HOME')
  if homedir is None or not os.access(homedir, os.W_OK):
    logging.error('Cannot write to home directory, $HOME=%r', homedir)
```

```python
  No:
  import os
  from absl import logging

  logging.info('Current $PAGER is:')
  logging.info(os.getenv('PAGER', default=''))

  homedir = os.getenv('HOME')
  if homedir is None or not os.access(homedir, os.W_OK):
    logging.error(f'Cannot write to home directory, $HOME={homedir!r}')
```

<a id="s3.10.2-error-messages"></a>
<a id="3102-error-messages"></a>
<a id="error-messages"></a>

<a id="error-messages"></a>
#### 3.10.2 Error Messages (エラーメッセージ)

Error messages (such as: message strings on exceptions like `ValueError`, or
messages shown to the user) should follow three guidelines:

1.  The message needs to precisely match the actual error condition.

2.  Interpolated pieces need to always be clearly identifiable as such.

3.  They should allow simple automated processing (e.g. grepping).

```python
  Yes:
  if not 0 <= p <= 1:
    raise ValueError(f'Not a probability: {p!r}')

  try:
    os.rmdir(workdir)
  except OSError as error:
    logging.warning('Could not remove directory (reason: %r): %r',
                    error, workdir)
```

```python
  No:
  if p < 0 or p > 1:  # PROBLEM: also false for float('nan')!
    raise ValueError(f'Not a probability: {p!r}')

  try:
    os.rmdir(workdir)
  except OSError:
    # PROBLEM: Message makes an assumption that might not be true:
    # Deletion might have failed for some other reason, misleading
    # whoever has to debug this.
    logging.warning('Directory already was deleted: %s', workdir)

  try:
    os.rmdir(workdir)
  except OSError:
    # PROBLEM: The message is harder to grep for than necessary, and
    # not universally non-confusing for all possible values of `workdir`.
    # Imagine someone calling a library function with such code
    # using a name such as workdir = 'deleted'. The warning would read:
    # "The deleted directory could not be deleted."
    logging.warning('The %s directory could not be deleted.', workdir)
```

<a id="s3.11-files-sockets-closeables"></a>
<a id="s3.11-files-and-sockets"></a>
<a id="311-files-and-sockets"></a>
<a id="files-and-sockets"></a>

<a id="files"></a>
### 3.11 Files, Sockets, and similar Stateful Resources (ファイル，ソケット等のステートフルなリソース)

Explicitly close files and sockets when done with them. This rule naturally
extends to closeable resources that internally use sockets, such as database
connections, and also other resources that need to be closed down in a similar
fashion. To name only a few examples, this also includes
[mmap](https://docs.python.org/3/library/mmap.html) mappings,
[h5py File objects](https://docs.h5py.org/en/stable/high/file.html), and
[matplotlib.pyplot figure windows](https://matplotlib.org/2.1.0/api/_as_gen/matplotlib.pyplot.close.html).

Leaving files, sockets or other such stateful objects open unnecessarily has
many downsides:

-   They may consume limited system resources, such as file descriptors. Code
    that deals with many such objects may exhaust those resources unnecessarily
    if they're not returned to the system promptly after use.
-   Holding files open may prevent other actions such as moving or deleting
    them, or unmounting a filesystem.
-   Files and sockets that are shared throughout a program may inadvertently be
    read from or written to after logically being closed. If they are actually
    closed, attempts to read or write from them will raise exceptions, making
    the problem known sooner.

Furthermore, while files and sockets (and some similarly behaving resources) are
automatically closed when the object is destructed, coupling the lifetime of the
object to the state of the resource is poor practice:

-   There are no guarantees as to when the runtime will actually invoke the
    `__del__` method. Different Python implementations use different memory
    management techniques, such as delayed garbage collection, which may
    increase the object's lifetime arbitrarily and indefinitely.
-   Unexpected references to the file, e.g. in globals or exception tracebacks,
    may keep it around longer than intended.

Relying on finalizers to do automatic cleanup that has observable side effects
has been rediscovered over and over again to lead to major problems, across many
decades and multiple languages (see e.g.
[this article](https://wiki.sei.cmu.edu/confluence/display/java/MET12-J.+Do+not+use+finalizers)
for Java).

The preferred way to manage files and similar resources is using the
[`with` statement](http://docs.python.org/reference/compound_stmts.html#the-with-statement):

```python
with open("hello.txt") as hello_file:
    for line in hello_file:
        print(line)
```

For file-like objects that do not support the `with` statement, use
`contextlib.closing()`:

```python
import contextlib

with contextlib.closing(urllib.urlopen("http://www.python.org/")) as front_page:
    for line in front_page:
        print(line)
```

In rare cases where context-based resource management is infeasible, code
documentation must explain clearly how resource lifetime is managed.

<a id="s3.12-todo-comments"></a>
<a id="312-todo-comments"></a>

<a id="todo"></a>
### 3.12 TODO Comments (TODOコメント)

Use `TODO` comments for code that is temporary, a short-term solution, or
good-enough but not perfect.

A `TODO` comment begins with the string `TODO` in all caps and a parenthesized
name, e-mail address, or other identifier
of the person or issue with the best context about the problem. This is followed
by an explanation of what there is to do.

The purpose is to have a consistent `TODO` format that can be searched to find
out how to get more details. A `TODO` is not a commitment that the person
referenced will fix the problem. Thus when you create a
`TODO`, it is almost always your name
that is given.

```python
# TODO(kl@gmail.com): Use a "*" here for string repetition.
# TODO(Zeke) Change this to use relations.
```

If your `TODO` is of the form "At a future date do something" make sure that you
either include a very specific date ("Fix by November 2009") or a very specific
event ("Remove this code when all clients can handle XML responses.").

<a id="s3.13-imports-formatting"></a>
<a id="313-imports-formatting"></a>

<a id="imports-formatting"></a>
### 3.13 Imports formatting (import文の書き方)

Imports should be on separate lines; there are
[exceptions for `typing` and `collections.abc` imports](#typing-imports).

E.g.:

```python
Yes: import os
     import sys
     from typing import Mapping, Sequence
```

```python
No:  import os, sys
```


Imports are always put at the top of the file, just after any module comments
and docstrings and before module globals and constants. Imports should be
grouped from most generic to least generic:

1.  Python future import statements. For example:

    ```python
    from __future__ import absolute_import
    from __future__ import division
    from __future__ import print_function
    ```

    See [above](#from-future-imports) for more information about those.

2.  Python standard library imports. For example:

    ```python
    import sys
    ```

3.  [third-party](https://pypi.org/) module
    or package imports. For example:

    
    ```python
    import tensorflow as tf
    ```

4.  Code repository
    sub-package imports. For example:

    
    ```python
    from otherproject.ai import mind
    ```

5.  **Deprecated:** application-specific imports that are part of the same
    top level
    sub-package as this file. For example:

    
    ```python
    from myproject.backend.hgwells import time_machine
    ```

    You may find older Google Python Style code doing this, but it is no longer
    required. **New code is encouraged not to bother with this.** Simply treat
    application-specific sub-package imports the same as other sub-package
    imports.

    
Within each grouping, imports should be sorted lexicographically, ignoring case,
according to each module's full package path (the `path` in `from path import
...`). Code may optionally place a blank line between import sections.

```python
import collections
import queue
import sys

from absl import app
from absl import flags
import bs4
import cryptography
import tensorflow as tf

from book.genres import scifi
from myproject.backend import huxley
from myproject.backend.hgwells import time_machine
from myproject.backend.state_machine import main_loop
from otherproject.ai import body
from otherproject.ai import mind
from otherproject.ai import soul

# Older style code may have these imports down here instead:
#from myproject.backend.hgwells import time_machine
#from myproject.backend.state_machine import main_loop
```


<a id="s3.14-statements"></a>
<a id="314-statements"></a>

<a id="statements"></a>
### 3.14 Statements (ブロックを構成する最小単位)

Generally only one statement per line.

However, you may put the result of a test on the same line as the test only if
the entire statement fits on one line. In particular, you can never do so with
`try`/`except` since the `try` and `except` can't both fit on the same line, and
you can only do so with an `if` if there is no `else`.

```python
Yes:

  if foo: bar(foo)
```

```python
No:

  if foo: bar(foo)
  else:   baz(foo)

  try:               bar(foo)
  except ValueError: baz(foo)

  try:
      bar(foo)
  except ValueError: baz(foo)
```

<a id="s3.15-accessors"></a>
<a id="s3.15-access-control"></a>
<a id="315-access-control"></a>
<a id="access-control"></a>
<a id="accessors"></a>

<a id="getters-and-setters"></a>
### 3.15 Getters and Setters (getterとsetter)

Getter and setter functions (also called accessors and mutators) should be used
when they provide a meaningful role or behavior for getting or setting a
variable's value.

In particular, they should be used when getting or setting the variable is
complex or the cost is significant, either currently or in a reasonable future.

If, for example, a pair of getters/setters simply read and write an internal
attribute, the internal attribute should be made public instead. By comparison,
if setting a variable means some state is invalidated or rebuilt, it should be a
setter function. The function invocation hints that a potentially non-trivial
operation is occurring. Alternatively, [properties](#properties) may be an
option when simple logic is needed, or refactoring to no longer need getters and
setters.

Getters and setters should follow the [Naming](#s3.16-naming) guidelines, such
as `get_foo()` and `set_foo()`.

If the past behavior allowed access through a property, do not bind the new
getter/setter functions to the property. Any code still attempting to access the
variable by the old method should break visibly so they are made aware of the
change in complexity.

<a id="s3.16-naming"></a>
<a id="316-naming"></a>

<a id="naming"></a>
### 3.16 Naming (命名規則)

`module_name`, `package_name`, `ClassName`, `method_name`, `ExceptionName`,
`function_name`, `GLOBAL_CONSTANT_NAME`, `global_var_name`, `instance_var_name`,
`function_parameter_name`, `local_var_name`, `query_proper_noun_for_thing`,
`send_acronym_via_https`.


Function names, variable names, and filenames should be descriptive; eschew
abbreviation. In particular, do not use abbreviations that are ambiguous or
unfamiliar to readers outside your project, and do not abbreviate by deleting
letters within a word.

Always use a `.py` filename extension. Never use dashes.

<a id="s3.16.1-names-to-avoid"></a>
<a id="3161-names-to-avoid"></a>

<a id="names-to-avoid"></a>
#### 3.16.1 Names to Avoid (割けるべき名前)

-   single character names, except for specifically allowed cases:

    -   counters or iterators (e.g. `i`, `j`, `k`, `v`, et al.)
    -   `e` as an exception identifier in `try/except` statements.
    -   `f` as a file handle in `with` statements
    -   private [`TypeVar`s](#typing-type-var) with no constraints (e.g. `_T`,
        `_U`, `_V`)

    Please be mindful not to abuse single-character naming. Generally speaking,
    descriptiveness should be proportional to the name's scope of visibility.
    For example, `i` might be a fine name for 5-line code block but within
    multiple nested scopes, it is likely too vague.

-   dashes (`-`) in any package/module name

-   `__double_leading_and_trailing_underscore__` names (reserved by Python)

-   offensive terms

-   names that needlessly include the type of the variable (for example:
    `id_to_name_dict`)

<a id="s3.16.2-naming-conventions"></a>
<a id="3162-naming-convention"></a>

<a id="naming-conventions"></a>
#### 3.16.2 Naming Conventions

-   "Internal" means internal to a module, or protected or private within a
    class.

-   Prepending a single underscore (`_`) has some support for protecting module
    variables and functions (linters will flag protected member access).

-   Prepending a double underscore (`__` aka "dunder") to an instance variable
    or method effectively makes the variable or method private to its class
    (using name mangling); we discourage its use as it impacts readability and
    testability, and isn't *really* private. Prefer a single underscore.

-   Place related classes and top-level functions together in a
    module.
    Unlike Java, there is no need to limit yourself to one class per module.

-   Use CapWords for class names, but lower\_with\_under.py for module names.
    Although there are some old modules named CapWords.py, this is now
    discouraged because it's confusing when the module happens to be named after
    a class. ("wait -- did I write `import StringIO` or `from StringIO import
    StringIO`?")

-   Underscores may appear in *unittest* method names starting with `test` to
    separate logical components of the name, even if those components use
    CapWords. One possible pattern is `test<MethodUnderTest>_<state>`; for
    example `testPop_EmptyStack` is okay. There is no One Correct Way to name
    test methods.

<a id="s3.16.3-file-naming"></a>
<a id="3163-file-naming"></a>

<a id="file-naming"></a>
#### 3.16.3 File Naming (ファイル名)

Python filenames must have a `.py` extension and must not contain dashes (`-`).
This allows them to be imported and unittested. If you want an executable to be
accessible without the extension, use a symbolic link or a simple bash wrapper
containing `exec "$0.py" "$@"`.

<a id="s3.16.4-guidelines-derived-from-guidos-recommendations"></a>
<a id="3164-guidelines-derived-from-guidos-recommendations"></a>

<a id="guidelines-derived-from-guidos-recommendations"></a>
#### 3.16.4 Guidelines derived from [Guido](https://en.wikipedia.org/wiki/Guido_van_Rossum)'s Recommendations ([Guido](https://en.wikipedia.org/wiki/Guido_van_Rossum)の推奨を基にしたガイドライン)

<table rules="all" border="1" summary="Guidelines from Guido's Recommendations"
       cellspacing="2" cellpadding="2">

  <tr>
    <th>Type</th>
    <th>Public</th>
    <th>Internal</th>
  </tr>

  <tr>
    <td>Packages</td>
    <td><code>lower_with_under</code></td>
    <td></td>
  </tr>

  <tr>
    <td>Modules</td>
    <td><code>lower_with_under</code></td>
    <td><code>_lower_with_under</code></td>
  </tr>

  <tr>
    <td>Classes</td>
    <td><code>CapWords</code></td>
    <td><code>_CapWords</code></td>
  </tr>

  <tr>
    <td>Exceptions</td>
    <td><code>CapWords</code></td>
    <td></td>
  </tr>

  <tr>
    <td>Functions</td>
    <td><code>lower_with_under()</code></td>
    <td><code>_lower_with_under()</code></td>
  </tr>

  <tr>
    <td>Global/Class Constants</td>
    <td><code>CAPS_WITH_UNDER</code></td>
    <td><code>_CAPS_WITH_UNDER</code></td>
  </tr>

  <tr>
    <td>Global/Class Variables</td>
    <td><code>lower_with_under</code></td>
    <td><code>_lower_with_under</code></td>
  </tr>

  <tr>
    <td>Instance Variables</td>
    <td><code>lower_with_under</code></td>
    <td><code>_lower_with_under</code> (protected)</td>
  </tr>

  <tr>
    <td>Method Names</td>
    <td><code>lower_with_under()</code></td>
    <td><code>_lower_with_under()</code> (protected)</td>
  </tr>

  <tr>
    <td>Function/Method Parameters</td>
    <td><code>lower_with_under</code></td>
    <td></td>
  </tr>

  <tr>
    <td>Local Variables</td>
    <td><code>lower_with_under</code></td>
    <td></td>
  </tr>

</table>


<a id="s3.17-main"></a>
<a id="317-main"></a>

<a id="math-notation"></a>
#### 3.16.5 Mathematical Notation (数学表記)

For mathematically heavy code, short variable names that would otherwise violate
the style guide are preferred when they match established notation in a
reference paper or algorithm. When doing so, reference the source of all naming
conventions in a comment or docstring or, if the source is not accessible,
clearly document the naming conventions. Prefer PEP8-compliant
`descriptive_names` for public APIs, which are much more likely to be
encountered out of context.

<a id="main"></a>
### 3.17 Main (main文)

In Python, `pydoc` as well as unit tests require modules to be importable. If a
file is meant to be used as an executable, its main functionality should be in a
`main()` function, and your code should always check `if __name__ == '__main__'`
before executing your main program, so that it is not executed when the module
is imported.

When using [absl](https://github.com/abseil/abseil-py), use `app.run`:

```python
from absl import app
...

def main(argv: Sequence[str]):
    # process non-flag arguments
    ...

if __name__ == '__main__':
    app.run(main)
```

Otherwise, use:

```python
def main():
    ...

if __name__ == '__main__':
    main()
```

All code at the top level will be executed when the module is imported. Be
careful not to call functions, create objects, or perform other operations that
should not be executed when the file is being `pydoc`ed.

<a id="s3.18-function-length"></a>
<a id="318-function-length"></a>

<a id="function-length"></a>
### 3.18 Function length (関数の長さ)

Prefer small and focused functions.

We recognize that long functions are sometimes appropriate, so no hard limit is
placed on function length. If a function exceeds about 40 lines, think about
whether it can be broken up without harming the structure of the program.

Even if your long function works perfectly now, someone modifying it in a few
months may add new behavior. This could result in bugs that are hard to find.
Keeping your functions short and simple makes it easier for other people to read
and modify your code.

You could find long and complicated functions when working with
some
code. Do not be intimidated by modifying existing code: if working with such a
function proves to be difficult, you find that errors are hard to debug, or you
want to use a piece of it in several different contexts, consider breaking up
the function into smaller and more manageable pieces.

<a id="s3.19-type-annotations"></a>
<a id="319-type-annotations"></a>

<a id="type-annotations"></a>
### 3.19 Type Annotations (型ヒント)

<a id="s3.19.1-general-rules"></a>
<a id="s3.19.1-general"></a>
<a id="3191-general-rules"></a>

<a id="typing-general"></a>
#### 3.19.1 General Rules (一般的なルール)

*   Familiarize yourself with
    [PEP-484](https://www.python.org/dev/peps/pep-0484/).
*   In methods, only annotate `self`, or `cls` if it is necessary for proper
    type information. e.g., `@classmethod def create(cls: Type[T]) -> T: return
    cls()`
*   Similarly, don't feel compelled to annotate the return value of `__init__`
    (where `None` is the only valid option).
*   If any other variable or a returned type should not be expressed, use `Any`.
*   You are not required to annotate all the functions in a module.
    -   At least annotate your public APIs.
    -   Use judgment to get to a good balance between safety and clarity on the
        one hand, and flexibility on the other.
    -   Annotate code that is prone to type-related errors (previous bugs or
        complexity).
    -   Annotate code that is hard to understand.
    -   Annotate code as it becomes stable from a types perspective. In many
        cases, you can annotate all the functions in mature code without losing
        too much flexibility.

<a id="s3.19.2-line-breaking"></a>
<a id="3192-line-breaking"></a>

<a id="typing-line-breaking"></a>
#### 3.19.2 Line Breaking (改行)

Try to follow the existing [indentation](#indentation) rules.

After annotating, many function signatures will become "one parameter per line".

```python
def my_method(self,
              first_var: int,
              second_var: Foo,
              third_var: Optional[Bar]) -> int:
  ...
```

Always prefer breaking between variables, and not, for example, between variable
names and type annotations. However, if everything fits on the same line, go for
it.

```python
def my_method(self, first_var: int) -> int:
  ...
```

If the combination of the function name, the last parameter, and the return type
is too long, indent by 4 in a new line.

```python
def my_method(
    self, first_var: int) -> tuple[MyLongType1, MyLongType1]:
  ...
```

When the return type does not fit on the same line as the last parameter, the
preferred way is to indent the parameters by 4 on a new line and align the
closing parenthesis with the `def`.

```python
Yes:
def my_method(
    self, other_arg: Optional[MyLongType]
) -> dict[OtherLongType, MyLongType]:
  ...
```

`pylint`
allows you to move the closing parenthesis to a new line and align with the
opening one, but this is less readable.

```python
No:
def my_method(self,
              other_arg: Optional[MyLongType]
             ) -> dict[OtherLongType, MyLongType]:
  ...
```

As in the examples above, prefer not to break types. However, sometimes they are
too long to be on a single line (try to keep sub-types unbroken).

```python
def my_method(
    self,
    first_var: tuple[list[MyLongType1],
                     list[MyLongType2]],
    second_var: list[dict[
        MyLongType3, MyLongType4]]) -> None:
  ...
```

If a single name and type is too long, consider using an
[alias](#typing-aliases) for the type. The last resort is to break after the
colon and indent by 4.

```python
Yes:
def my_function(
    long_variable_name:
        long_module_name.LongTypeName,
) -> None:
  ...
```

```python
No:
def my_function(
    long_variable_name: long_module_name.
        LongTypeName,
) -> None:
  ...
```

<a id="s3.19.3-forward-declarations"></a>
<a id="3193-forward-declarations"></a>

<a id="forward-declarations"></a>
#### 3.19.3 Forward Declarations (前方宣言)

If you need to use a class name from the same module that is not yet defined --
for example, if you need the class inside the class declaration, or if you use a
class that is defined below -- either use `from __future__ import annotations`
for simple cases or use a string for the class name.

```python
from __future__ import annotations

class MyClass:

  def __init__(self, stack: Sequence[MyClass]) -> None:
```

<a id="s3.19.4-default-values"></a>
<a id="3194-default-values"></a>

<a id="typing-default-values"></a>
#### 3.19.4 Default Values (デフォルト値)

As per
[PEP-008](https://www.python.org/dev/peps/pep-0008/#other-recommendations), use
spaces around the `=` *only* for arguments that have both a type annotation and
a default value.

```python
Yes:
def func(a: int = 0) -> int:
  ...
```

```python
No:
def func(a:int=0) -> int:
  ...
```

<a id="s3.19.5-nonetype"></a>
<a id="s3.19.5-none-type"></a>
<a id="3195-nonetype"></a>

<a id="none-type"></a>
#### 3.19.5 NoneType (`NoneType`)

In the Python type system, `NoneType` is a "first class" type, and for typing
purposes, `None` is an alias for `NoneType`. If an argument can be `None`, it
has to be declared! You can use `Union`, but if there is only one other type,
use `Optional`.

Use explicit `Optional` instead of implicit `Optional`. Earlier versions of PEP
484 allowed `a: str = None` to be interpreted as `a: Optional[str] = None`, but
that is no longer the preferred behavior.

```python
Yes:
def func(a: Optional[str], b: Optional[str] = None) -> str:
  ...
def multiple_nullable_union(a: Union[None, str, int]) -> str:
  ...
```

```python
No:
def nullable_union(a: Union[None, str]) -> str:
  ...
def implicit_optional(a: str = None) -> str:
  ...
```

<a id="s3.19.6-type-aliases"></a>
<a id="s3.19.6-aliases"></a>
<a id="3196-type-aliases"></a>
<a id="typing-aliases"></a>

<a id="type-aliases"></a>
#### 3.19.6 Type Aliases (型エイリアス)

You can declare aliases of complex types. The name of an alias should be
CapWorded. If the alias is used only in this module, it should be \_Private.

For example, if the name of the module together with the name of the type is too
long:

```python
_ShortName = module_with_long_name.TypeWithLongName
ComplexMap = Mapping[str, list[tuple[int, int]]]
```

Other examples are complex nested types and multiple return variables from a
function (as a tuple).

<a id="s3.19.7-ignoring-types"></a>
<a id="s3.19.7-ignore"></a>
<a id="3197-ignoring-types"></a>

<a id="typing-ignore"></a>
#### 3.19.7 Ignoring Types (型の無視)

You can disable type checking on a line with the special comment `# type:
ignore`.

`pytype` has a disable option for specific errors (similar to lint):

```python
# pytype: disable=attribute-error
```

<a id="s3.19.8-typing-variables"></a>
<a id="s3.19.8-comments"></a>
<a id="3198-typing-internal-variables"></a>

<a id="typing-variables"></a>
#### 3.19.8 Typing Variables (変数の型付け)

<a id="annotated-assignments"></a>
[*Annotated Assignments*](#annotated-assignments)
:   If an internal variable has a type that is hard or impossible to infer,
    specify its type with an annotated assignment - use a colon and type between
    the variable name and value (the same as is done with function arguments
    that have a default value):

    ```python
    a: Foo = SomeUndecoratedFunction()
    ```

<a id="type-comments"></a>
[*Type Comments*](#type-comments)
:   Though you may see them remaining in the codebase (they were necessary
    before Python 3.6), do not add any more uses of a `# type: <type name>`
    comment on the end of the line:

    ```python
    a = SomeUndecoratedFunction()  # type: Foo
    ```

<a id="s3.19.9-tuples-vs-lists"></a>
<a id="s3.19.9-tuples"></a>
<a id="3199-tuples-vs-lists"></a>

<a id="typing-tuples"></a>
#### 3.19.9 Tuples vs Lists (tupleとlist)

Typed lists can only contain objects of a single type. Typed tuples can either
have a single repeated type or a set number of elements with different types.
The latter is commonly used as the return type from a function.

```python
a: list[int] = [1, 2, 3]
b: tuple[int, ...] = (1, 2, 3)
c: tuple[int, str, float] = (1, "2", 3.5)
```

<a id="s3.19.10-typevars"></a>
<a id="s3.19.10-type-var"></a>
<a id="31910-typevar"></a>
<a id="typing-type-var"></a>

<a id="typevars"></a>
#### 3.19.10 TypeVars (`TypeVar`)

The Python type system has
[generics](https://www.python.org/dev/peps/pep-0484/#generics). The factory
function `TypeVar` is a common way to use them.

Example:

```python
from typing import TypeVar
_T = TypeVar("_T")
...
def next(l: list[_T]) -> _T:
  return l.pop()
```

A TypeVar can be constrained:

```python
AddableType = TypeVar("AddableType", int, float, str)
def add(a: AddableType, b: AddableType) -> AddableType:
  return a + b
```

A common predefined type variable in the `typing` module is `AnyStr`. Use it for
multiple annotations that can be `bytes` or `unicode` and must all be the same
type.

```python
from typing import AnyStr
def check_length(x: AnyStr) -> AnyStr:
  if len(x) <= 42:
    return x
  raise ValueError()
```

A TypeVar must have a descriptive name, unless it meets all of the following
criteria:

*   not externally visible
*   not constrained

```python
Yes:
  _T = TypeVar("_T")
  AddableType = TypeVar("AddableType", int, float, str)
  AnyFunction = TypeVar("AnyFunction", bound=Callable)
```

```python
No:
  T = TypeVar("T")
  _T = TypeVar("_T", int, float, str)
  _F = TypeVar("_F", bound=Callable)
```

<a id="s3.19.11-string-types"></a>
<a id="s3.19.11-strings"></a>
<a id="31911-string-types"></a>

<a id="typing-strings"></a>
#### 3.19.11 String types (文字列型)

The proper type for annotating strings depends on what versions of Python the
code is intended for.

Prefer to use `str`, though `Text` is also acceptable. Be consistent in using
one or the other. For code that deals with binary data, use `bytes`. For Python
2 compatible code that processes text data (`str` or `unicode` in Python 2,
`str` in Python 3), use `Text`.

```python
def deals_with_text_data_in_py3(x: str) -> str:
  ...
def deals_with_binary_data(x: bytes) -> bytes:
  ...
def py2_compatible_text_data_processor(x: Text) -> Text:
  ...
```

In some uncommon Python 2 compatibility cases, `str` may make sense instead of
`Text`, typically to aid compatibility when the return types aren't the same
between Python 2 and Python 3. Never use `unicode` as it doesn't exist in Python
3. The reason this discrepancy exists is because `str` means something different
in Python 2 than in Python 3.

No:

```python
def py2_code(x: str) -> unicode:
  ...
```

If the type can be either bytes or text, use `Union`, with the appropriate text
type.

```python
from typing import Text, Union
...
def py3_only(x: Union[bytes, str]) -> Union[bytes, str]:
  ...
def py2_compatible(x: Union[bytes, Text]) -> Union[bytes, Text]:
  ...
```

If all the string types of a function are always the same, for example if the
return type is the same as the argument type in the code above, use
[AnyStr](#typing-type-var).

<a id="s3.19.12-imports-for-typing"></a>
<a id="s3.19.12-imports"></a>
<a id="31912-imports-for-typing"></a>

<a id="typing-imports"></a>
#### 3.19.12 Imports For Typing (型付けのためのimport)

For classes from the `typing` and `collections.abc` modules for use in
annotations, always import the class itself. This keeps common annotations more
concise and matches typing practices used around the world. You are explicitly
allowed to import multiple specific classes on one line from the `typing` and
`collections.abc` modules. Ex:

```python
from collections.abc import Mapping, Sequence
from typing import Any, Union
```

Given that this way of importing adds items to the local namespace, names in
`typing` or `collections.abc` should be treated similarly to keywords, and not
be defined in your Python code, typed or not. If there is a collision between a
type and an existing name in a module, import it using `import x as y`.

```python
from typing import Any as AnyType
```

<a id="s3.19.13-conditional-imports"></a>
<a id="31913-conditional-imports"></a>

<a id="typing-conditional-imports"></a>
#### 3.19.13 Conditional Imports (条件付きimport)

Use conditional imports only in exceptional cases where the additional imports
needed for type checking must be avoided at runtime. This pattern is
discouraged; alternatives such as refactoring the code to allow top level
imports should be preferred.

Imports that are needed only for type annotations can be placed within an `if
TYPE_CHECKING:` block.

-   Conditionally imported types need to be referenced as strings, to be forward
    compatible with Python 3.6 where the annotation expressions are actually
    evaluated.
-   Only entities that are used solely for typing should be defined here; this
    includes aliases. Otherwise it will be a runtime error, as the module will
    not be imported at runtime.
-   The block should be right after all the normal imports.
-   There should be no empty lines in the typing imports list.
-   Sort this list as if it were a regular imports list.
```python
import typing
if typing.TYPE_CHECKING:
  import sketch
def f(x: "sketch.Sketch"): ...
```

<a id="s3.19.14-circular-dependencies"></a>
<a id="s3.19.14-circular-deps"></a>
<a id="31914-circular-dependencies"></a>

<a id="typing-circular-deps"></a>
#### 3.19.14 Circular Dependencies (循環import依存)

Circular dependencies that are caused by typing are code smells. Such code is a
good candidate for refactoring. Although technically it is possible to keep
circular dependencies, various build systems will not let you do so
because each module has to depend on the other.

Replace modules that create circular dependency imports with `Any`. Set an
[alias](#typing-aliases) with a meaningful name, and use the real type name from
this module (any attribute of Any is Any). Alias definitions should be separated
from the last import by one line.

```python
from typing import Any

some_mod = Any  # some_mod.py imports this module.
...

def my_method(self, var: "some_mod.SomeType") -> None:
  ...
```

<a id="typing-generics"></a>
<a id="s3.19.15-generics"></a>
<a id="31915-generics"></a>

<a id="generics"></a>
#### 3.19.15 Generics (ジェネリクス？)

When annotating, prefer to specify type parameters for generic types; otherwise,
[the generics' parameters will be assumed to be `Any`](https://www.python.org/dev/peps/pep-0484/#the-any-type).

```python
def get_names(employee_ids: list[int]) -> dict[int, Any]:
  ...
```

```python
# These are both interpreted as get_names(employee_ids: list[Any]) -> dict[Any, Any]
def get_names(employee_ids: list) -> Dict:
  ...

def get_names(employee_ids: List) -> Dict:
  ...
```

If the best type parameter for a generic is `Any`, make it explicit, but
remember that in many cases [`TypeVar`](#typing-type-var) might be more
appropriate:

```python
def get_names(employee_ids: list[Any]) -> dict[Any, str]:
  """Returns a mapping from employee ID to employee name for given IDs."""
```

```python
_T = TypeVar('_T')
def get_names(employee_ids: list[_T]) -> dict[_T, str]:
  """Returns a mapping from employee ID to employee name for given IDs."""
```


<a id="4-parting-words"></a>

<a id="consistency"></a>
## 4 おわりに

*BE CONSISTENT*.

If you're editing code, take a few minutes to look at the code around you and
determine its style. If they use spaces around all their arithmetic operators,
you should too. If their comments have little boxes of hash marks around them,
make your comments have little boxes of hash marks around them too.

The point of having style guidelines is to have a common vocabulary of coding so
people can concentrate on what you're saying rather than on how you're saying
it. We present global style rules here so people know the vocabulary, but local
style is also important. If code you add to a file looks drastically different
from the existing code around it, it throws readers out of their rhythm when
they go to read it. Avoid this.
