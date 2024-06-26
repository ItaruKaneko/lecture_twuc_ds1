# GoogleColab の準備

- [GoogleColab の準備](#googlecolab-の準備)
  - [1. あらかじめ用意するもの](#1-あらかじめ用意するもの)
  - [2. ログイン](#2-ログイン)
  - [3. R言語に設定](#3-r言語に設定)
    - [3.1. ノートブックを作成する](#31-ノートブックを作成する)
    - [3.2. ランタイムのタイプを変える](#32-ランタイムのタイプを変える)
  - [3.3 動作の確認](#33-動作の確認)
  - [4. サンプルコードの実行](#4-サンプルコードの実行)
  - [5. Google Colabが起動しない場合](#5-google-colabが起動しない場合)
    - [5.1.方法1: Google Colabで直接開く](#51方法1-google-colabで直接開く)
    - [5.2. 方法2: Google Driveから開く設定を変更](#52-方法2-google-driveから開く設定を変更)

## 1. あらかじめ用意するもの

1. Google account
2. Web ブラウザ (キーボードが使えるものが望ましいがタブレットでも可能)
3. Windowsとword (でなくてもよいのですが、ファイルをダウンロードしてエディタで編集する必要があります)
4. インターネット接続

## 2. ログイン

以下のリンクをクリッして、
Gogle Colabolatory を別ウインドウで開く

<a href=
"https://colab.research.google.com/" 
target="_blank">
https://colab.research.google.com/ 
</a>

このような webpage が開きます。

(2022/9/16 現在、サービスの内容は時期によって変わることがあります)

右上の「ログイン」をクリックし、google account でログインします。

![GoogleColab の画面](../../images/colab_010.jpg)

## 3. R言語に設定

Google colab では通常 Pythion 言語が選択されているもで、これを R 言語に変更します。

### 3.1. ノートブックを作成する

右上のこの部分で Web ページ上部のメニューを開きます。

![GoogleColab の画面](../../images/colab_020.jpg)

ファイル/ノートブックを新規作成

を選びます。

![GoogleColab の画面](../../images/colab_030.jpg)

Untitled0.ipynb というファイルがつくられます。(もしかするとUntitled?.ipynb と?の部分の数字はかわるかも)

ここで、コード、を入力します。

![GoogleColab の画面](../../images/colab_035.jpg)


~~~
x <- 3
print(x)
~~~

と入力します。
ここでセルの左にある「▷」は実行ボタンで、これをクリックするとプログムを実行します。
しかしここで「▷」実行ボタンをクリックすると、以下のようにエラーが出るはずです。

これは Google colab は通常 Python 言語を処理するようになっていて、このプログラムは Python 言語としては
誤っているからです。

![GoogleColab の画面](../../images/colab_130.jpg)

そこで、この後ノートブックを Python を実行する設定から、R 言語を実行する設定に変更します。
まちがえないようよく注意し操作してください。

### 3.2. ランタイムのタイプを変える

ランタイム

メニューを開き

ランタイムのタイプを変える

を選びます。

![GoogleColab の画面](../../images/colab_112.jpg)

ランタイムのタイプを変更

のポップアップが表示されるので、

ランタイムのタイプ

をクリックして、選択枝の中から

R

を選んで

保存

をクリックします。

![GoogleColab の画面](../../images/colab_114.jpg)



## 3.3 動作の確認

動作を確認しましょう。

コード

をクリックすると新しいセル(入力できる枠)ができますからここに R 言語の命令を入力します。

て以下のコードを入力しましょう。

~~~
x <- 3
print(x)
~~~

コードを入力したらセルの左側の実行ボタン(右 ▷ ) をクリックすると R 言語として入力した命令が実行されて、結果がセルの下にあらわれます。

もし画面のようにセルの下の「3」が表示されれば、R言語が正常に動作しています。

![GoogleColab の画面](../../images/colab_120.jpg)

もしも以下のようにエラーが出たら、Python 言語のままになっていますので、この操作をやりなおしてください。

![GoogleColab の画面](../../images/colab_130.jpg)

## 4. サンプルコードの実行

google drive にサンプルファイルをアップロードしておきます。
practice1.ipynb をダブルクリックすると、google colab を起動できます。
R言語の設定はすでにされています。

以下のように、左上の目次のアイコンをクリックすると、目次が開きます。
![目次の表示](../../images/colab_210.jpg)


目次が表示されたところ

![目次が表示された画面](../../images/colab_220.jpg)

## 5. Google Colabが起動しない場合

Google Drive 中の myprogram.ipynb をダブルクリックしても
Google Colabで開かない。
またアプリケーションにもGoogle Colabがない。

### 5.1.方法1: Google Colabで直接開く

ブラウザでGoogle Colabにアクセスします。

ファイルを開く: 画面左上の「ファイル」メニューを開き、
「ノートブックを開く」を選択する。

Google Driveを選択: 「ノートブックを開く」ダイアログで「Google Drive」タブを選択する。

ファイルを探す: myprogram.ipynbを探し、開きます。Drive内で直接見つからない場合は、検索バーを使用してファイル名を検索することができます。

### 5.2. 方法2: Google Driveから開く設定を変更

設定を開く: 右上の歯車アイコンをクリックし、「設定」を選択します。

「管理アプリ」を選択: 設定画面で「管理アプリ」を選択します。

Google Colabを探す: ページ内で「Google Colab」を探し、
それが.ipynbファイルの既定のアプリケーションであることを確認します。
もし設定されていない場合は、.ipynbファイルの種類を見つけ、
それに対してGoogle Colabを既定のアプリケーションとして
関連付けるオプションを探します。



