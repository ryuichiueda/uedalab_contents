<h2></h2>
<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第10回</h2>
上田 隆一

2016年12月7日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>先に課題1
<ul>
 	<li>GitとかGitHubとか普段から使っている人は課題をやりましょう</li>
</ul>
</li>
 	<li>Git, GitHub</li>
</ul>
<!--nextpage-->
<h2>課題1（12/31まで）</h2>
<ul>
 	<li>講義で作ったデバイスドライバをカスタマイズして
<ol>
 	<li>GitHubにプッシュ
<ul>
 	<li>ライセンス、何をやったか分かるREADMEを書く</li>
</ul>
</li>
 	<li>Youtube等、パブリックで見られるところにデモをアップ
<ul>
 	<li>これも何をやっているか説明を書く</li>
</ul>
</li>
 	<li>私まで電子メール
<ul>
 	<li>件名: ロボットシステム学 課題1 名前 学籍番号</li>
 	<li>内容、普通に他人に出すような電子メールで、上記GitHubとビデオのURLを貼る
<ul>
 	<li>「普通」は任せますが、あんまり失礼だと匿名を保った上でTwitterで嘆きます</li>
</ul>
</li>
</ul>
</li>
</ol>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>自分で書いたプログラムの管理</h2>
<ul>
 	<li>自分で作ったプログラムの管理をどうするか？
<ul>
 	<li>別にファイルやディレクトリのコピーでも良い</li>
 	<li>ファイルをhoge.c, hoge.c.org, hoge.c.orgorg...とコピーして保存</li>
 	<li>あるいはディレクトリに日付をつけて管理</li>
</ul>
</li>
 	<li>ラズパイやマイコンのコードの管理は結構面倒</li>
 	<li>さらに便利にならないか？
<ul>
 	<li>変更の日付等を自動で管理したい</li>
 	<li>別のPCで使う。別の人が使えるようにしておく。</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>Git</h2>
<ul>
 	<li>版管理（バージョン管理）システム
<ul>
 	<li>ファイルの変更履歴を管理するためのシステム</li>
</ul>
</li>
 	<li>Linus Torvalds が作成
<ul>
 	<li>Linux の共同開発のため</li>
</ul>
</li>
 	<li>単にバージョン管理のためだけでなく、コード公開のプラットフォームになっている
<ul>
 	<li>リポジトリの公開</li>
 	<li>GitHub, BitBucket</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>Gitのインストール</h2>
<ul>
 	<li>sudo apt install git 等
<ul>
 	<li>最近はデフォルトで使える環境が多い</li>
</ul>
</li>
 	<li>使うときは次の2つの登録を
<ul>
 	<li>自身の名前（ハンドルネーム）</li>
 	<li>メールアドレス</li>
</ul>
</li>
 	<li>使用するエディタも登録しておくと混乱しない</li>
</ul>
<pre><span style="color: #ffffff;">$ sudo apt-get install git
###自身の名前とe-mail アドレスを記録しておく###
$ git config --global user.name "Ryuichi Ueda"
$ git config --global user.email "ueda\@hogehoge.com"
$ git config --global core.editor vim
###確認###
$ cat .gitconfig
[user]
name = Ryuichi Ueda
email = ueda\@hogehoge.com
[core]
editor = vim
</span></pre>
<!--nextpage-->
<h2>リポジトリを作る</h2>
<ul>
 	<li>リポジトリ（repository）
<ul>
 	<li>貯蔵庫、倉庫、納骨堂、埋葬所</li>
 	<li>要はバージョン管理するディレクトリ</li>
</ul>
</li>
 	<li>2種類
<ul>
 	<li>リモートリポジトリ、ローカルリポジトリ</li>
</ul>
</li>
 	<li>Git の基本的な使い方（あくまで基本）
<ul>
 	<li>リモートリポジトリをどこかに置き、そこから自分のマシンにそれをクローンしてローカルリポジトリを作成</li>
 	<li>ローカルリポジトリで何かファイルを更新したらリモートリポジトリに反映</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>GitHub</h2>
<ul>
 	<li>Gitを利用したサービス
<ul>
 	<li>リポジトリのホスティングと公開</li>
 	<li>公開しないリポジトリも作成可能（有料）</li>
 	<li>学校のメールアドレスだと無料で作れるかもしれません</li>
</ul>
</li>
 	<li>利用方法
<ul>
 	<li>ウェブサイト</li>
 	<li>コマンドライン</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>アカウント作成</h2>
<ul>
 	<li>GitHubにアクセス
<ul>
 	<li>https://github.com/</li>
</ul>
</li>
 	<li>ユーザ名、email アドレス、パスワードを決めて"Sign up for GitHub"
<ul>
 	<li>ユーザ名は恥ずかしくないものを！</li>
</ul>
</li>
 	<li>・・・</li>
 	<li>プランを選ぶときに"Free"が選択されているのを確認して"Finish sign up"</li>
 	<li>登録したメールアドレスに確認メールが届くのでインストラクションに従う</li>
 	<li>できる人は公開鍵の登録</li>
</ul>
<!--nextpage-->
<h2>リポジトリの作成</h2>
<ul>
 	<li>GitHubにリモートのものを一つ作ってみましょう</li>
 	<li>GitHubのサイトでの操作
<ul>
 	<li>右下あたりにある"New repository"をクリック</li>
 	<li>必要事項を記入
<ul>
 	<li>後の操作の例のために以下をお願いします
<ul>
 	<li>"Initialize this repository with a README"にチェック</li>
 	<li>ライセンスのプルダウンからMITライセンスを選択</li>
</ul>
</li>
</ul>
</li>
 	<li>"Create repository"ボタンを押す</li>
</ul>
</li>
 	<li>ウェブ画面にリポジトリの画面
<ul>
 	<li>READMEとLISENCEができている</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>リモートのリポジトリを
ローカルに</h2>
<ul>
 	<li>リポジトリの画面の"clone or download"をクリック</li>
 	<li>「HTTPS」を選択してURLをコピー
<ul>
 	<li>クリップボードのアイコンをクリックするとコピーできる</li>
</ul>
</li>
 	<li>リポジトリを作りたいディレクトリで次の操作
<pre><span style="color: #ffffff;">$ git clone &lt;さっきクリップボードにコピーした文字列をペースト&gt;
Cloning into 'test'...
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (4/4), done.
Checking connectivity... done.
$ cd test/</span>
<span style="color: #ffffff;">$ ls -a
.  ..  .git  LICENSE  README.md</span></pre>
</li>
</ul>
<!--nextpage-->
<h2>リポジトリにコードを追加</h2>
<ul>
 	<li>なんでもいいからプログラムを一つ置く
<ul>
 	<li>特にこだわりがなければ次のようなシェルスクリプトを
<pre><span style="color: #ffffff;">$ cat hoge.bash</span>
<span style="color: #ffffff;">#!/bin/bash</span>

<span style="color: #ffffff;">echo hoge</span></pre>
</li>
</ul>
</li>
 	<li>「addしてstatus見てcommit」
<ul>
 	<li>リポジトリへのファイルの登録
<ul>
 	<li>まず、登録対象のファイルを選択（git add）</li>
 	<li>選択されたファイルは「ステージ」に載せられる
<ul>
 	<li>「ステージング」 と表現</li>
 	<li>git statusで確認</li>
</ul>
</li>
</ul>
</li>
 	<li>ステージに置いたファイルを登録（git commit）
<ul>
 	<li>「<span style="color: #ff0000;">コミット</span>する」と表現</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>コミットの操作</h2>
<pre><span style="color: #ffffff;"><span style="color: #ffff00;">$ git add hoge.bash</span>
<span style="color: #ffff00;">$ git status</span>
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD &lt;file&gt;..." to unstage)
new file:   hoge.bash
<span style="color: #ffff00;">$ git commit -m "Add a file"</span>
[master 9da0223] Add a file
 1 file changed, 3 insertions(+)
 create mode 100644 hoge.bash</span></pre>
<!--nextpage-->
<h2>リモートへの「push」</h2>
<ul>
 	<li>ローカルのコミットをリモートへ反映
<ul>
 	<li>origin: リモートのリポジトリのこと</li>
 	<li>master: master<span style="color: #ff0000;">ブランチ</span></li>
</ul>
</li>
</ul>
<pre><span style="color: #ffff00;">$ git push origin master</span>
<span style="color: #ffffff;">Counting objects: 3, done.</span>
<span style="color: #ffffff;">Delta compression using up to 4 threads.</span>
<span style="color: #ffffff;">Compressing objects: 100% (2/2), done.</span>
<span style="color: #ffffff;">Writing objects: 100% (3/3), 333 bytes | 0 bytes/s, done.</span>
<span style="color: #ffffff;">Total 3 (delta 0), reused 0 (delta 0)</span>
<span style="color: #ffffff;">To https://github.com/ryuichiueda/test.git</span>
<span style="color: #ffffff;">   b09eefb..9da0223  master -&gt; master</span></pre>
<!--nextpage-->
<h2>ブランチ</h2>
<ul>
 	<li>ディレクトリの中の状態を分岐したもの
<ul>
 	<li>ブランチ = 枝</li>
</ul>
</li>
 	<li>今のところブランチは「master」だけ</li>
 	<li>
<pre class="p1"><span style="color: #ffffff;"><span class="s1"><span style="color: #ffff00;">$ git branch</span>
</span><span class="s2">* </span><span class="s1">master</span></span></pre>
</li>
 	<li>開発用ブランチを作りましょう</li>
 	<li>
<pre><span style="color: #ffff00;">$ git checkout -b dev</span>
<span style="color: #ffffff;">Switched to a new branch 'dev'</span>
<span style="color: #ffff00;">$ git branch</span>
<span style="color: #ffffff;">* dev</span>
<span style="color: #ffffff;">  master</span></pre>
</li>
</ul>
<!--nextpage-->
<h2>ブランチの切り替え</h2>
<ul>
 	<li>開発をdevブランチで進めてコミット
<ul>
 	<li>hogeを2個にする</li>
</ul>
</li>
 	<li>
<pre class="p1"><span style="color: #ffffff;"><span class="s1"><span style="color: #ffff00;">$ cat hoge.bash</span> （hoge.bashを書き換えた後にcatしたところ）
</span><span class="s1">#!/bin/bash
</span><span class="s1">echo hoge
</span><span class="s1">echo hoge
<span style="color: #ffff00;">$ git add hoge.bash</span> 
<span style="color: #ffff00;">$ git commit -m "Add another hoge"</span>
<span style="color: #ff0000;">[dev ce996b6]</span> Add another hoge
 1 file changed, 1 insertion(+), 1 deletion(-)
</span></span></pre>
</li>
 	<li></li>
</ul>
