<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第9回</h2>
上田 隆一

2016年11月30日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>フリーソフト、オープンソース、著作権、ライセンス
<ul>
 	<li>背景</li>
 	<li>適当に人のものを使っていませんか？</li>
 	<li>怖がって使わずに効率の悪い開発をしていませんか？</li>
 	<li>我々はどう付き合うべきか？</li>
 	<li>コピペは善なのか悪なのか？</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>大学生と著作</h2>
<ul>
 	<li>ブログやGitHub等で誰でも自身の著作物を公開する機会
<ul>
 	<li>作文、コード、ロボットのデモムービー等</li>
 	<li>コミュニティーや同人活動への参加
<ul>
 	<li>こういうところでは、むしろ作品を公開しないと存在しない人扱いを受けるという勢い（いいか悪いかは別）</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>インターネット上での活動</h2>
<ul>
 	<li>インターネットはアバウトな部分と容赦ない部分が同居
<ul>
 	<li>著作権やライセンスへの理解がないと生きていけない</li>
 	<li>あからさまに違反して反省もしないと大炎上</li>
 	<li>悪徳ハッカソンに著作権を取られる等、被害にも遭う</li>
 	<li>自身を売り出すためにはさらに深く理解が必要</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>インターネット上の著作物の流用</h2>
<ul>
 	<li>ロボットを扱うときに使うオープンソース
<ul>
 	<li>ROSやOpenCV等、それらの上で動くもの</li>
</ul>
</li>
 	<li>オープンソースを使った自身の著作物やコードは公開していいの？売っていいの？</li>
 	<li>そもそも何でオープンソースは公開されている？
<ul>
 	<li>Unixの話の時にした通り</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>コードの公開</h2>
<ul>
 	<li>コードを公開することによる恩恵（例:  Unix）
<ul>
 	<li>普及する</li>
 	<li>バグを第三者が見つけてくれる</li>
 	<li>改良法を第三者が考えてくれる</li>
</ul>
</li>
 	<li>コードを公開する場合の困った点
<ul>
 	<li>商売難しい</li>
 	<li>誰のもの？</li>
 	<li>プログラマーの世界の外で理解が得られない</li>
</ul>
</li>
 	<li>コード公開の判断
<ul>
 	<li><span style="color: #ff0000;">工・法・商・歴史様々な視点が入り乱れる</span></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>リチャード・ストールマン（RMS）</h2>
<ul>
 	<li>コードは公開されるべきという立場の急先鋒</li>
 	<li>Emacs, GCC等の作者
<ul>
 	<li>1971年〜MITのハッカー</li>
 	<li>逸話
<ul>
 	<li>パスワードに反対して破る→メンバーにパスワードを空白にするように促す</li>
 	<li>コピーライトへの批判</li>
 	<li>アンチ携帯電話</li>
 	<li>講演で座禅を組んで「フリーダム」と一言だけ</li>
 	<li>ASCIIに招かれた時に廊下に座ってプログラミング</li>
 	<li>他、膨大な逸話</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ハッカー</h2>
<ul>
 	<li>（技術的な定義は別として、文化的には）ヒッピー的な考え方を継承した腕のあるプログラマ
<ul>
 	<li><a href="https://ja.wikipedia.org/wiki/%E3%83%92%E3%83%83%E3%83%94%E3%83%BC" target="_blank">ヒッピー</a>（1960年代〜）
<ul>
 	<li>love and peaceな人たち
<ul>
 	<li style="font-size: 70%;">・・・と書くと平和そうだが、反戦、反体制、フリーダム、フリーセックス、マリファナ、LSD、ビートルズ、東洋思想、嫌儲厨な人たち
<span style="color: #ff0000;">（注意: いろいろ非合法）</span></li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
 	<li>今も「ハッカー気質」の人は多い
<ul>
 	<li><a href="https://ja.wikipedia.org/wiki/%E3%83%8F%E3%83%83%E3%82%AB%E3%83%BC%E6%96%87%E5%8C%96" target="_blank">「技術を独占するよりも広く共有して、皆で大いに楽しみたいとする奔放さ」</a></li>
</ul>
</li>
 	<li>ライセンス: ヒッピー的な考えとビジネス的な考えの妥協点</li>
</ul>
<!--nextpage-->
<h2>コピーレフト</h2>
<ul>
 	<li>著作物は利用・再配布・改変できなければならない
（つまりフリーダムであるべき）<img class=" wp-image-2235 alignright" src="https://lab.ueda.asia/wp-content/uploads/2016/11/Copyleft-300x300.png" alt="copyleft" width="229" height="229" />
<ul>
 	<li>Copyleft: all rights <span style="text-decoration: underline;">reversed</span></li>
</ul>
</li>
 	<li><span style="color: #ff0000;">ただし、著作権は放棄しない</span>
<ul>
 	<li>放棄すると他者がそれを拾って著作権を主張するようになる</li>
 	<li>ストールマン自身が被害に遭った経験から</li>
</ul>
</li>
 	<li>左図: コピーレフトのマーク
（パブリックドメイン）</li>
</ul>
<!--nextpage-->
<h2>GPL<span style="font-size: 80%;">（GNU General Public license）</span></h2>
<ul>
 	<li>コピーレフトの考え方を
ライセンス化したもの<a title="By Free Software Foundation (gnu.org/graphics/license-logos.html) [Public domain], via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File%3AGPLv3_Logo.svg"><img class="alignright" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/GPLv3_Logo.svg/512px-GPLv3_Logo.svg.png" alt="GPLv3 Logo" width="249" height="130" /></a></li>
 	<li>ストールマンの立ち上げたFSF
（Free Software Foundation）が策定</li>
 	<li> 基本的なルール
<ul>
 	<li>GPLで頒布されたプログラム
（コードやバイナリ）について、ユーザは実行、再配布、改変、調査できる権利を保持</li>
 	<li>ただし、再頒布の際は再度GPLで頒布する義務</li>
 	<li>バイナリのユーザが要求した場合にコードの公開義務</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>GPLの効果</h2>
<ul>
 	<li>人のコードを持ってきた人（企業・団体）が改変部分を隠してコピーを売ることを抑制できる。</li>
 	<li> ソフトウェアの特性を損なわない
<ul>
 	<li>1人が作ればみんな使える。そこから改良できる。</li>
</ul>
</li>
 	<li>具体的な例
<ul>
 	<li>Linuxのデバイスドライバのコードが隠れない
<ul>
 	<li>カーネルのデバッグ時に有益</li>
</ul>
</li>
 	<li>LinuxがGPL→動的リンクするドライバも基本はGPL
<ul>
 	<li>GPL（と何かのデュアルライセンス）でないと警告</li>
</ul>
</li>
</ul>
</li>
</ul>
&nbsp;

<!--nextpage-->
<h2>LinuxとGPL</h2>
<ul>
 	<li>Linuxカーネルに付属するコマンド等ソフトウェアの多くは「GNU」由来</li>
 	<li><a href="https://ja.wikipedia.org/wiki/GNU" target="_blank">GNU</a>（GNU’s not UNIX）
<ul>
 	<li>FSFで開発されているOS</li>
 	<li>LinuxはGNUの付属ソフトウェア（coreutils等）を使っている
→GPLになる</li>
</ul>
</li>
 	<li>FSFは、LinuxはGNU/Linuxと名乗るべきと主張</li>
</ul>
<!--nextpage-->
<h2>GPLの効果（？）の例</h2>
<ul>
 	<li>知らないうちにGPLのコードをちょっと使ってバイナリを配布してしまった→コード全部にGPL適用</li>
 	<li>GPLのライセンスは連鎖していく
<ul>
 	<li>「感染」とも</li>
</ul>
</li>
 	<li>動的・静的にリンクしたライブラリも対象
<ul>
 	<li>GPLのコードにはGPL互換でないライブラリが使えない</li>
 	<li>GPLでないコードにGPLのライブラリが使えない</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>LGPL<span style="font-size: 70%;">（GNU lesser general public license）</span></h2>
<ul>
 	<li>GPLでないプログラムにリンクして良いライセンス
<ul>
 	<li>他のプログラムがGPL化しない</li>
</ul>
</li>
 	<li>当初はGNU library general public licenseだった<a title="By Free Software Foundation (gnu.org/graphics/license-logos.html) [Public domain], via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File%3ALGPLv3_Logo.svg"><img class="alignright" src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/LGPLv3_Logo.svg/512px-LGPLv3_Logo.svg.png" alt="LGPLv3 Logo" width="250" height="109" /></a>
<ul>
 	<li>ライブラリGPL → 劣GPL</li>
</ul>
</li>
 	<li>主な利用例
<ul>
 	<li>GNU Cライブラリ, OpenOffice.org, …</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>GPLを適用する方法</h2>
<ul>
 	<li><a href="https://www.gnu.org/licenses/gpl-howto.ja.html" target="_blank">正確な情報はこの文章から</a></li>
 	<li>ソフトウェアにCOPYING or LICENSEというファイル名でライセンス全文を同梱
<ul>
 	<li>Gitならリポジトリのトップディレクトリに置く</li>
</ul>
</li>
 	<li>各ソースファイルの頭にも書くのが望ましい
<ul>
 	<li>というより書く</li>
 	<li>copyrightとGPL/LGPLである旨。COPYINGの場所</li>
</ul>
</li>
 	<li>例: <a href="https://github.com/torvalds/linux" target="_blank">https://github.com/torvalds/linux</a></li>
</ul>
<!--nextpage-->
<h2>考えてみましょう</h2>
<ul>
 	<li>ロボカップで使ったコードをGPLで配布するとどうなる？
<ul>
 	<li>他のチームに与える影響は？</li>
</ul>
</li>
 	<li>企業でコードが使われるだろうか？
<ul>
 	<li>企業と共同研究できる？</li>
</ul>
</li>
 	<li>ROSやOpenCVの何かと一緒に配布できる？</li>
 	<li>LGPLだったら？</li>
</ul>
<!--nextpage-->
<h2>BSD/BSDライセンス</h2>
<ul>
 	<li>BSD（Barkeley software distribution）
<ul>
 	<li>UCBで開発されたUNIXの一種（1977年〜）</li>
 	<li>AT&amp;T由来のコードを含む</li>
 	<li>ライセンスに関する様々な問題を回避しながら開発</li>
 	<li style="font-size:50%">最寄りのBSDオジサンに聞いてみよう！</li>
</ul>
</li>
 	<li>BSDライセンス
<ul>
 	<li>その名の通りBSDのためのライセンス</li>
 	<li>もともとGPL以前の話なので別のライセンス体系</li>
 	<li>企業との悲喜こもごもの中で生まれた</li>
</ul>
</li>
</ul>
