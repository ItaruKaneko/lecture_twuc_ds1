## 1 相関係数

あるクラスで 数学の試験と 英語の試験の成績のデータを集めたとします。 このデータをプロットするとどのように分泌するでしょうか。

数学の成績が良い人は英語の成績もいいという傾向があるかもしれませんね。 あるいは数学が得意な人は 英語が得意な人は数学が不得意であるならば 数学の点が高いほど英語の10は低い という傾向があるかもしれませんね。 あるいは数学の成績と英語の成績には全く関係がないかもしれません。
これを数値的に表現するのが相関係数ですね。

数学の点数と英語の点数が完全な比例関係にあるならば 相関係数は1になります。 反比例の関係にあるならば-1になります。 無関係であればゼロになります。
そして R 言語では相関係数はデータを与えるば簡単に求めることができます。

いくつかのデータで実際に相関係数を計算してみましょう。

## 2 回帰分析

さて相関係数はどのように求めればいいのでしょうか 。関係数の求め方は知らなくても R 言語のライブラリを使えば簡単に求めることができます。 数学的な計算方法は必ずしも知っている必要はありません。


しかし、原理を理解しておくことでより 適切にデータを処理することができます。 どのように相関係数を求める顔を簡単に説明しましょう。

相関係数は データを近似する一次関数から 求めることができます。 一次関数というのは直線ですから 適当に直線を引いてみてどのような直線が一番データを表す直線であるかを求めればいいことになります。
この時 どの直線が一番データを出すかということは直線との誤差が少なければ良いと言えるでしょう。

すると全てのデータと直線の距離を求めて その距離の二乗和が 最も小さい直線が最も うまくデータを近似する 一次関数ということになりますね。

このような一次関数を求めるの簡単で まず全てのデータと一次関数との誤差を計算し その誤差を一次関数の係数の 関数とするような関数を考えます。 一次関数の係数を与えるとデータとの誤差を計算するというような関数がえられるわけです。

この関数を係数によって微分します 。 するとその微分された関数は 係数を変化させたときにどれだけ誤差が増減するかということを表しているわけです。

誤差が最小になるところではこの微分値はゼロになるはずですね。 ですからこの微分値をゼロにするという方程式を解くことによって 誤差を最小にするような 一次関数の係数を求めることができます。
計算を振り返ってみると 一次関数の係数を決め そこから近似誤差を求め その近似誤差から 筋肉さんの微分お求め 微分値をゼロにすることによって元に戻って一次関数の係数を求めるので、 元に戻るという意味で回帰分析と呼びます。

回帰分析の計算方法がわかっていれば どのようなことが分かるでしょうか。 回帰分析では 一次関数とデータの誤差を最小化するだけですから データの順番は全く影響を与えません。 



共分散
回帰分析の中でも変数の関係が線形である場合は特別にごく簡単に変数の関係を求めることができます。このような場合は変数の関係は比例関係でも泊まるわけですが、その係数が相関係数となり相関係数を求めるには共分散という統計値を求めれば簡単に求まります。
共分散は二つの変数の値をまず平均からの誤差で表しその積を足し合わせたものになります。

式に表すとこのような式になります

この計算はライブラリを使えばやってくれるので相関係数を算出するために自分で共分散を求めたりすることは必要ありませんが、相関係数が共分散から求まるということを知っていればデータを見ただけで大体の相関係数を想像できるので便利ですね。
共分散では変位の積がマイナスであると負の相関になるわけですが、これは要するに一方が増えて行った時に一報が減るという場合に相関が降る2分になるということを表しているだけですね。一方相関が急いである核であるかというの事に大きく影響するのは体が大きい時だって、平均値に近いデータに関しては相関係数にも相関係数が正である核であるということにもあまり寄与しません。


目的変数
回帰分析をするとある変数を別の変数で説明できるということになります。例えば所得と大学時代の成績に相関があった場合俺は大学時代の成績によって所得がある程度説明できるということになるので、これを因果関係と考えれば所成績で所得をどの程度説明できるかということを相関係数が表してることになります。そのような場合には所得を目的変数成績を説明変数とするわけです,


説明変数

## 線形回帰
線形のモデルを仮定した、回帰分析です。
つまり、説明変数と目的変数の関係を線形の関係としたモデルによる
回帰分析です。

## 単回帰
説明変数が1つの場合の線形回帰です。

## 重回帰
説明変数が複数の場合の線形回帰です。

## 可視化
相関係数は数値で求まりますが相関係数が表す直線の方程式をデータとともにグラフで表示することによって可視化することができ.回帰分析の結果がどのデータをどの程度良くならをしているかを視覚的に確認することができます。

散布図
またデータだけをサンプルとして表すこともできます

### 正の相関
二つの変数が一方が増えるともう一方も増える傾向を持つ相関を正の相関といいます。相関係数も共分散も正の値になります。


### 負の相関
二つの変数が一方が増えるともう一方が減少する傾向を持つ相関を負の相関といいます。相関係数も共分散も負の値になります。

### 強い相関
二つの変数が比例関係に近く、比例関係からの差がごく小さいような場合が強い相関です。一方の値から他方の値が高い精度で推定できます。正の相関でも負の相関でも、一方から他方が高い精度で推定できれば、それは強い相関です。

### 弱い相関
二つの変数が無関係に近く、一方から他方がほとんど推測できない場合が弱い相関です。弱い相関では、二つの変数は無関係に近く、相関係数も、共分散も小さな値になります。

### Min
最小値

### Max
最大値

### Median

中央値。中央値は平均値ではなく、サンプルを大きさの順にならべたときに、ちょうど順序で中央, 9サンプルなら5番目にあたるサンプルです。サンプルが偶数の場合は、中央の2サンプルの平均が中央値になります。

### Mean
平均値

### 回帰式
回帰分析の結果をあらわす式です。
一般には回帰分析は複雑な数値計算が必要ですが、線形回帰では簡単な回帰式であらわせます。

## 予測

データが時系列の場合は回帰分析の結果を時間の関数として解釈して未来の時点における値を推測することに使うことができます。
一方で予測に使う場合には、通常は回帰直線を推定するのではなく未来の予測値の方を汚水てく推定するようにモデルを作って回忌計算をするのが普通です,

## 過剰適合

オーバーフィッティング
回帰分析ではオーバーフィッティングという問題にも注意しなければなりません。オーバーフィッティングというのは文字通り過剰に適合してしまうという意味です。どういうことでしょう。例えば体重と身長の関係を分析するとします。10人の体重と身長を分析すると傾向が見えてきますね。しかし身長から推測される体重には若干の誤差があります。
これに誕生日や血液型を説明変数として増やすと予測精度がはるかに上がるという現象が生じます。しかしこれは、たまたまそのデータにおいて誕生日や血液型と見かけの相関によるものであることは明らかですね。

一般に説明変数を多く摂りすぎるとこのようにたまたま現れた相関を使って本来の伊豆であるものまで説明してしまうので過剰に結果を精度よく表す回帰分析の結果が得られてしまいますこれをオーバーフィッティングと呼ぶのですね。

オーバーフィッティングを避けるためにはデータの説明変数は合理的な範囲にとどめておく必要があります。また多くの変数をを記録しておくとその変数のいくつかを選ぶことによってたまたま得られた良い結果を本当の相関と誤認してしまう可能性もありますから、実験や調査を計画する時にはあまりに過剰な説明変数を無計画に用意するということは避けるべきです。

## 新たなデータによる検証

得られた結果をの報告を見ただけでは、多くの異なる説明変数の組み合わせから、たまたま良いものを選んだり、オーバーフィッティングしたものであるかは、区別がつきません。

回帰分析の結果が疑わしい場合、全く新たに取得した実験結果やデータで、再度検証してみるとどうなるでしょうか？

オーバーフィッティングや、過剰な説明変数によって得られた、過度に良い結果は、このような追加で行った実験では消失します。

ですから、疑わしい結果を検証するためには、新たなデータを追加するということが有力な検証方法になります。