# ロジスティック回帰

## 1 線形回帰との違い
ロジスティック回帰は2群判別を行うための回帰分析です。

同じ回帰分析には、線形回帰分析という手法があります。ロジスティック回帰は同じ回帰という名前がついていますが、線形ではなくロジスティックというところが違ういます。どこが違うのでしょうか。

与えられたデータから、それらの関係を分析して、説明変数から目的変数を推測する。これは両方とも同じです。
名前から推測できるように、一言で言えばロジスティック回帰では数値ではなく2群判別を行うという違いがあります。

まず、線形回帰では、説明変数と目的変数がともに数値です。
一方ロジスティック回帰では結果として得られるのは2群の判別です。

次に線形回帰では、推定をする数値は説明変数から線形の回帰式であらわします。別の言い方をすれば、もしいくつかの事項から別の事項が比例の関係であらわします。こんなような式ですね。

$Y = a X + b$

$Y$ や $X$ はデータとして与えられ、
$a$ と $b$ を回帰的に求め、
$Y$ をもっともうまく表す回帰式をもとめたわけです。

ロジスティック回帰は2群判別です。

これをたとえば、 $\{0,1\}$ という2値の数値として回帰分析をするのとはどう違うでしょうか。

目的変数を $\{ 0,1 \}$ という２値の数値として、線形回帰を行うこともできますね。しかしそのような方法はよい方法ではない。

第1に、うまく予測ができません。なぜかというと $\{ 0,1 \}$という結果は、いきなり得られるものではなく、なにかしらの数値が結果として得られた後で、2値に置き換えられているというメカニズムでよりうまく表せることが多い。

たとえば、試験に合格するかしないか、というデータを回帰分析しようとします。試験の点数であれば線形回帰で求めることが適切でしょう。いろいろな要素と試験の点数の相関関係を求めることができます。

しかし、試験の合否はそうして得られた得点が合格点を超えたかどうか、ということで判別されます。つまり合否という結果には、それが100点満点であったか、ぎりぎり60点で合格であったか、という情報は隠れていて見えていない。したがって、結果として得られた $\{ 0,1 \}$ を数値として回帰したのではうまくいかないわけです。

当然ロジスティック回帰では線形回帰よりもはるかに多くのデータを必要とする場合が多いです。誤りも多くなります。

次に、ロジスティック回帰では $\{ 0,1 \}$ の2群判別なので回帰式でその2群を与えたとすると、正答か誤答かになるだけで「誤差」は意味を持ちません。そこで目的変数として「推測値」としての
$\{ 0,1 \}$ ではなくそれぞれの確率を求めます。

それではロジスティック回帰の方法と実例を見てみましょう。

## 2 ロジスティック回帰の手法

例によってロジスティック回帰もRのライブラリ関数の中に実現されているので分析方法を全く知らなくても関数を呼べば簡単に求めることができます。

しかし簡単にその手法を見ておきましょう。
回帰分析では目的変数を線形の式で表しました。

$Y = a X + b$

ロジスティック回帰では目的変数をこのような式であらわします。

$p = \frac{1}{1 + e ^ {- (aX + b)}}$

こうするとうまい具合に最適なパラメーターを求める方法が見つかるのですね。

別の言い方をすれば線形回帰では、目的変数と予想値の誤差を最小にするように回帰直線を選んだわけですが、ロジスティック回帰では確率を求めているので2群判別の正解率を上げるようにパラメータを調整するのだ、と考えることができます。

そこの違いだけで、後は数学的にはそのような最適解を求める、という点は同じです。

## 3 ロジスティック回帰における注意

ロジスティック回帰でも分析において注意すべき点があります。

まずいくつかの変数のうち一つの変数で完全に予測ができてしまうという場合があります。この場合分析結果が適切でなくなる場合があるので警告が出ます。

この現象は線形分析で目的変数が説明変数の一部で完全に予想できてしまう場合と仕組み上は同じですね。つまり一つの変数で結果が予想できてしまうと他の変数が結果にどう影響するかという計算のところで計算上の問題が生じるわけです。

この現象は、線形回帰の場合と同様に、実際にこういうことがおきることは多い。
何かの値をなるべくうまく回帰式で表したいと試行錯誤をしていると、
新しい説明変数をつかえば多少は結果が改良されるので、
ついついいろいろな説明変数を導入してしまします。
そして、多くの説明変数を導入すれば、それによって完全に結果を説明できてしまいます。

ですから、ロジスティック回帰においても、データ数にたいして、説明変数をむやみに多くしすぎない、基準が必要となるわけです。

もちろん実はたくさんの説明変数を試した結果、よいものだけを選ぶ、ということによっても意味がない結果を出してしまう危険はありますね。

## 4 説明変数の個数の目安

あるデータ数があった場合にどの程度の説明変数があると問題がおきるか。だいたいのあたりをつけられるようにしておくとよいでしょう。

まず、あたりまえの場合を考えてみます。

8 個のデータについて2群判別の結果は256通りのパターンがあるわけです。
ですから256の説明変数がそれぞれ異なるパターンであれば、どれか一つはマッチしますね。
または16の説明変数の組み合わせは256通りあるから、16の説明変数の2つの組み合わせでほぼ表される可能性は高いと想像できますね。
一方で、もちろんこれは様々な説明変数があれば、という場合であって、どの説明変数も2群判別の結果にマッチしないなら、
そのような説明変数を何個用意しても、適合度は向上しません。

つまり、説明変数の個数の見積もりは、一概にこの数より多いと不適切、というものではなく、データの性質によって状況は大きくことなります。

しかし、データ数に対し説明変数の数が多いほど、その結果は信頼できないことになります。
また、説明変数を後から増やす場合には、その説明変数を加える合理性があるか、より慎重な検討が必要だということになります。

## 5 とはいってもね

公開された論文をみていると、これはおかしくない? というような研究は多々あります。

論文を出す側はなんとしても、「なんらかの効果があった」と主張しないと論文として成立しない、ということがあり、審査の側もとりあえず「適合率が下がった」は受け入れられないとしても、「適合率はあがっているが、説明変数が不適切」というのはリジェクト理由として主張しにくいから、こうしたことはある程度やむを得ないのです。

しかし、実質的な性能を評価しなければならない場合は、こうした「上げ底」は上げ底として認識する必要がある。とりあえず説明変数を増やせば結果がよくなるのはあたりまえ、ということを知っているだけで、こうした「底上げ」を見抜く力になりますから、そうしたことを覚えておくだけでもこうしたことを理解していることが役立ちます。