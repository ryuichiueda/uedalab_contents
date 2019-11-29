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
 	<li style="font-size: 50%;">最寄りのBSDオジサンに聞いてみよう！</li>
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
<!--nextpage-->
<h2>旧BSDライセンス
<span style="font-size: 70%;">（4条項、廃止）</span></h2>
<ul>
 	<li><a href="https://ja.wikipedia.org/wiki/BSD%E3%83%A9%E3%82%A4%E3%82%BB%E3%83%B3%E3%82%B9#.E6.97.A7BSD.E3.83.A9.E3.82.A4.E3.82.BB.E3.83.B3.E3.82.B9.E3.83.BB.E5.9B.9B.E6.9D.A1.E9.A0.85BSD.E3.83.A9.E3.82.A4.E3.82.BB.E3.83.B3.E3.82.B9" target="_blank">正式なもの</a>
<ul>
 	<li>要約
<ul>
 	<li>コピーライト、ライセンス全文、免責事項の明記</li>
 	<li><span style="color: #ff0000;">コードを公開せず</span>バイナリ配布する時も1を遵守</li>
 	<li>貢献者・支援した団体等のリストを明記<span style="color: #ff0000;">（宣伝条項）</span></li>
 	<li>貢献者の名前をソフトウェアの宣伝に勝手に使わない</li>
</ul>
</li>
</ul>
</li>
 	<li>宣伝条項がいろいろと問題
<ul>
 	<li>リスト巨大化</li>
 	<li>GPLのコードへBSDライセンスのコードを混ぜられない（非互換）</li>
 	<li>（注意: 書いた人については著作権者なので明記）</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>その後の修正</h2>
<ul>
 	<li>宣伝条項の廃止
<ul>
 	<li>修正BSDライセンス（<a href="https://ja.wikipedia.org/wiki/BSD%E3%83%A9%E3%82%A4%E3%82%BB%E3%83%B3%E3%82%B9#.E4.BF.AE.E6.AD.A3BSD.E3.83.A9.E3.82.A4.E3.82.BB.E3.83.B3.E3.82.B9.E3.83.BB.E4.B8.89.E6.9D.A1.E9.A0.85BSD.E3.83.A9.E3.82.A4.E3.82.BB.E3.83.B3.E3.82.B9" target="_blank">3条項BSDライセンス</a>）
<ul>
 	<li><span style="color: #ff0000;">OpenCV, ROS等で採用されている</span></li>
</ul>
</li>
 	<li>GPLと互換に
<ul>
 	<li>GPLのプロジェクトにROSのコードを混ぜてGPLで配布可能</li>
</ul>
</li>
</ul>
</li>
 	<li>4番目の条項のないものも整備
<ul>
 	<li><a href="https://ja.wikipedia.org/wiki/BSD%E3%83%A9%E3%82%A4%E3%82%BB%E3%83%B3%E3%82%B9#.E4.BA.8C.E6.9D.A1.E9.A0.85BSD.E3.83.A9.E3.82.A4.E3.82.BB.E3.83.B3.E3.82.B9" target="_blank">2条項BSDライセンス</a>
<ul>
 	<li>FreeBSD等で採用</li>
</ul>
</li>
</ul>
</li>
 	<li>現在の*BSDとLinuxの競争はライセンスの話が深く関係</li>
</ul>
<!--nextpage-->
<h2>「BSDライク」な
ライセンス</h2>
<ul>
 	<li>BSDライセンスに似たライセンスが多く存在
<ul>
 	<li>似ているだけなので注意</li>
</ul>
</li>
 	<li>例: MITライセンス
<ul>
 	<li>個人的によく使う</li>
 	<li><a href="https://opensource.org/licenses/mit-license.php" target="_blank">全文</a>
<ul>
 	<li>著作権とライセンスの表示の義務づけ</li>
 	<li>免責</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>MITライセンスの適用</h2>
<ul>
 	<li>ソフトウェアにライセンスの全文を同梱
<ul>
 	<li>LICENSEというファイル名が一般的</li>
</ul>
</li>
 	<li>ソースファイルの頭に
<ul>
 	<li>著作権表示</li>
 	<li>MITライセンス全文あるいはMITライセンスである旨とLICENSEへのリンク</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>{フリー,オープンソース}
ソフトウェア</h2>
<ul>
 	<li>使い分けは慎重に
<ul>
 	<li>フリーソフトウェア
<ul>
 	<li> FSFの主張する文脈で使う用語
<ul>
 	<li>GPL周辺</li>
</ul>
</li>
</ul>
</li>
 	<li>オープンソースソフトウェア
<ul>
 	<li>open source initiativeの主張する文脈で使う用語
<ul>
 	<li>ビジネス寄り</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>プロプライエタリソフトウェア/商用ライセンス</h2>
<ul>
 	<li>プロプライエタリソフトウェア
<ul>
 	<li>知的所有権が保持されて使用者が制限を受けるソフト</li>
 	<li>LinuxやMacの上で動かすのは問題ない
<ul>
 	<li>ライブラリやドライバレベルだとGPL等で問題になる</li>
</ul>
</li>
</ul>
</li>
 	<li>商用ライセンス
<ul>
 	<li>所有権者が決めるので様々</li>
 	<li>通常は使用者がコードを見られないようになっている</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ライセンスの選択について補足</h2>
<ul>
 	<li>何かにフリーなライセンスを選択しても著作権は守られているので著作権者はライセンスを選べる
<ul>
 	<li>他のライセンスで守られているコードがなければ</li>
</ul>
</li>
 	<li>同じものをGPLで配布したり商用ライセンスで配布したり
<ul>
 	<li><a href="http://www.softagency.co.jp/products/mysql/license/" target="_blank">MySQLの例</a></li>
 	<li>デュアルライセンス</li>
</ul>
</li>
 	<li>何かをゼロから作ったら自身にとって一番良い方法を選択</li>
</ul>
<!--nextpage-->
<h2><a href="http://creativecommons.jp/" target="_blank">クリエイティブ・コモンズ</a></h2>
<ul>
 	<li>ウィキペディアでよく見かけるとおもいます</li>
 	<li>以下を目的とした国際プロジェクト・非営利団体
<ul>
 	<li>著作物を著作権を守りながら人に使ってもらえないか？</li>
 	<li>「all rights reserved」以外の方法を模索</li>
 	<li>コードではないので公開・非公開という話とは少し違う</li>
</ul>
</li>
 	<li>「クリエイティブ・コモンズ・ライセンス」を策定・管理
<ul>
 	<li>マーク、コモンズ証、リーガルコード、メタデータ等を提供</li>
 	<li>ライセンスではないが、パブリックドメインについてもCC0の策定</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2><a href="http://creativecommons.jp/licenses/" target="_blank">クリエイティブ・
コモンズ・ライセンス</a></h2>
<ul>
 	<li>略してCCライセンス</li>
 	<li> 以下の条件の組み合わせで著作者が発行
<ul>
 	<li>表示（BY）
<ul>
 	<li>著作権者の表示、ライセンスへのリンク、変更がある場合の説明</li>
</ul>
</li>
 	<li>継承（SA） or 改変禁止（ND） or 条件なし
<ul>
 	<li>継承: 改変時、貢献部分に同じライセンスを適用</li>
 	<li>改変禁止: 改変したものの頒布禁止</li>
</ul>
</li>
 	<li>非営利（NC） or 条件なし
<ul>
 	<li>非営利: 営利目的利用の禁止</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>有り得る組み合わせ</h2>
<ul>
 	<li>表示（BY）、継承（SA） or 改変禁止（ND）、
非営利（NC）が互いに矛盾しないのは以下の6通り
<ul>
 	<li>CC BY</li>
 	<li>CC BY-SA, CC BY-ND,</li>
 	<li>CC BY-NC, CC BY-NC-SA, CC BY-NC-ND</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>CCライセンスの発行</h2>
<ul>
 	<li>手続き
<ul>
 	<li> 著作物にマークをつける</li>
 	<li>「コモンズ証」へのリンク</li>
</ul>
</li>
 	<li>クラウドサービスではプルダウンメニューで選べるようになっているものも
<ul>
 	<li>slideshare, GitHub等</li>
 	<li>GitHubはソフトウェアのライセンスも選べる</li>
 	<li>ソフトウェアの場合は免責事項の関係でソフトウェアのライセンスを</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>既存の著作物の利用</h2>
<ul>
 	<li>あくまで私見ですが・・・</li>
 	<li> ライセンスの仕組みを理解して責任を持って積極的に
<ul>
 	<li>勉強以外の目的ではなるべく自分で作らないこと
<ul>
 	<li>コードを書くなということではないのは注意</li>
</ul>
</li>
 	<li>目的を最短時間で終わらせること</li>
 	<li><span style="color: #ff0000;">車輪の再発明をしない。</span>
<ul>
 	<li>褒めてもらえると思った人がブチ切れられるという事例が上田研で・・・</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>自分でコードを書くときの基準</h2>
<ul>
 	<li>車輪の再発明でない場合
<ul>
 	<li>まだ世の中にない</li>
</ul>
</li>
 	<li>既存のものにライセンスの問題、入手困難</li>
 	<li>既存のコードに手を入れるのが難しい
<ul>
 	<li>だいたい難しいのでコードを読む力をつける</li>
</ul>
</li>
 	<li>衝動・勉強・同人活動
<ul>
 	<li>良いが、<span style="color: #ff0000;">付加価値が無く終わることがないよう</span>実験的に</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>レポート等での流用・コピー</h2>
<ul>
 	<li>どういう解釈になるんでしょうか？
<ul>
 	<li>だた「先生がダメって言うから」という解釈から卒業を</li>
</ul>
</li>
 	<li>人の文章等を流用した場合
<ul>
 	<li>何の引用もなくコピペすると著作権の侵害・訴えられたら有罪</li>
 	<li>著作権の問題をクリアしていても詐欺になる可能性</li>
 	<li>講義での課題の場合はそもそも学習効果がないと0点</li>
</ul>
</li>
 	<li>人の文章は基本、引用で済ます
<ul>
 	<li>このスライドのようにリンクを多用</li>
 	<li>論文なら引用の作法を守る</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>まとめ</h2>
<ul>
 	<li>オープンソースのライセンス、CCライセンスの仕組み
<ul>
 	<li>作った人が著作権を保ったまま他の人が作った物を使う仕組み</li>
</ul>
</li>
 	<li>積極的に使いこなす重要性はますます増している
<ul>
 	<li>不可避と思いましょう</li>
 	<li>車輪の再開発は趣味</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>課題1（12/31まで）</h2>
<ul>
 	<li>講義で作ったデバイスドライバをカスタマイズして
<ul>
 	<li>GitHubに上げる
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
 	<li>「普通」は任せますが、あんまり失礼だとガッカリします</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
