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
