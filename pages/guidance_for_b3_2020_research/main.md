# 2020年度3年生配属ガイダンス（研究紹介）

（書いている途中）

* その他上田研情報については: https://lab.ueda.tech/?page=guidance_for_b3_2020

## 確率ロボティクス関係

　「自分の位置が分からない」「自分の位置すら考えていない」ロボットをどう賢く動かすか、というテーマです。


### 自分の位置が分からないときにどうゴールに向かうか

<blockquote class="twitter-tweet" data-partner="tweetdeck"><p lang="ja" dir="ltr">自己位置に自信がなく何度も振り返ってしまうロボット <a href="https://t.co/VwfyRuIsbN">pic.twitter.com/VwfyRuIsbN</a></p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/1248420328176377859?ref_src=twsrc%5Etfw">April 10, 2020</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


### コントローラで教えた動きを再現

ロボットが壁にぶつかったり床ですべったりする環境や、センサで見ると同じように見える場所で互いに異なる行動を選択しなければならない場合に、教えた動きをどうやってロボットに安定的に再現させるか、という研究です。


次の3つのビデオは、いずれもゲームコントローラで動きを教えて、その後ロボットを自律で走らせるという構成になっています。

<iframe width="560" height="315" src="https://www.youtube.com/embed/oyWM3GlXHbs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/89IsMeIhzug" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/DSXjhRypLc4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## マニピュレーションの共同研究

3件の共同研究を実施中です。何をしているのかは秘密ですが、いずれもロボットハンドでなにかを掴む研究で、画像や深度画像処理、ロボットの制御がテーマとなります。

ここでは世間に公表されている2つの事例について紹介します。

### 物体のどこを掴めばよいかを決定するアルゴリズム

RGB-Dカメラを使って物体を観測して、ロボットハンドでつかみやすい部分を検出する研究です。使用する技術としては、3次元点群処理と、機械学習、その他幾何計算です。東芝さんとの共同研究です。


<blockquote class="twitter-tweet" data-partner="tweetdeck"><p lang="ja" dir="ltr">物体の3次元点群から、ロボットハンドでどこをつかめばよいか計算するアルゴリズムの出力例（シミュレーション結果。赤いところを中心に掴む）<br><br>昨年のロボット学会で発表した、東芝さんとの共同研究です。 <a href="https://t.co/3eoBCSsQvg">pic.twitter.com/3eoBCSsQvg</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/1260010226478010369?ref_src=twsrc%5Etfw">May 12, 2020</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" data-conversation="none"><p lang="ja" dir="ltr">これはヤカンの例 <a href="https://t.co/UoFL5CtzKI">pic.twitter.com/UoFL5CtzKI</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/1260011470319833089?ref_src=twsrc%5Etfw">May 12, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

### 唐揚げをつかむ

これは一区切りついた研究ですが、山盛りのからあげを上から見ても、どれが個々のからあげかを識別するのは難しいのですが、それを可能とした研究です。アールティさんとの共同研究です（学生さん一人が出向して実装。上田の寄与度は研究の進め方のアドバイス程度です）。

<iframe width="560" height="315" src="https://www.youtube.com/embed/Epu7o9_-sGo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### おまけ（3年生の課題）

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZMpj_mBggjw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## VR、ARによる移動ロボットのためのツール作成

タブレットを覗くとロボットのセンシングの様子が覗けるツールを作成しています。単にツールを作るだけではなく、タブレット内の演算結果を利用してロボットの動きをキャリブレーションする手法の研究をしています。

こちらはARツールを使って、ロボットの推定移動量と実際の移動量を計算し、移動量の推定パラメータをキャリブレーションする研究のデモムービーです。

<iframe width="560" height="315" src="https://www.youtube.com/embed/52zwd1RE2wM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

こちらはビジュアルに凝ったロボットの頭の中のモニタリングシステムです。

<iframe width="560" height="315" src="https://www.youtube.com/embed/10RygjfTLuw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## つくばチャレンジ（林原研のお手伝い）

上田研からもつくばチャレンジに参加できます。上田研では長期的なテーマを研究課題としています。

<blockquote class="twitter-tweet" data-partner="tweetdeck"><p lang="ja" dir="ltr">写真のように障害物があったときに、直接それをセンシングするのではなく、「通るのがいやだ度」を深層学習の学習結果から得て、ロボットに迂回させるという研究 <a href="https://t.co/nnrD47RolG">pic.twitter.com/nnrD47RolG</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/1260024565654118402?ref_src=twsrc%5Etfw">May 12, 2020</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


## 教育活動や教育ツール、その他活動

研究と呼べるものと呼べないものがありますが、教材を作るという課題に取り組んでもらうこともあります。また、遊んでいると研究になることがあります。


### 実機とJupyter Notebookをつなげた教材の作成

ビデオはカルマンフィルタのサンプルを作成したものです。

<iframe width="560" height="315" src="https://www.youtube.com/embed/0IRqv7ILLj8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 講義ビデオの作成

これは私のビデオですが、学生が講義しても別に罰は当たらないと思いますのでぜひ。

<iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?list=PLbUh9y6MXvjfOLwmuuBbXKUX45rZsM8iH" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen>
</iframe>

### 自由な工作活動

あんまりやってると論文書けと言われます。（注意: 中には3年のポスター発表ネタもあります。）

<iframe width="560" height="315" src="https://www.youtube.com/embed/M2WgAUXNwz8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/NnxcNu3dGdU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">ちゃんと実機でも宴会芸できた <a href="https://t.co/V0UGo89Y01">pic.twitter.com/V0UGo89Y01</a></p>&mdash; ハバタ (@habatafuture) <a href="https://twitter.com/habatafuture/status/1188007485807849473?ref_src=twsrc%5Etfw">October 26, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">猿回し <a href="https://t.co/xMs6uqjsiB">pic.twitter.com/xMs6uqjsiB</a></p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/1149139355996344320?ref_src=twsrc%5Etfw">July 11, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script><blockquote class="twitter-tweet"><p lang="ja" dir="ltr">猿回し <a href="https://t.co/xMs6uqjsiB">pic.twitter.com/xMs6uqjsiB</a></p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/1149139355996344320?ref_src=twsrc%5Etfw">July 11, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">数値が地獄なんですが。 <a href="https://t.co/DFrTL3fqQ5">pic.twitter.com/DFrTL3fqQ5</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/1147048428460883968?ref_src=twsrc%5Etfw">July 5, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="und" dir="ltr"><a href="https://twitter.com/hashtag/%E4%B8%8A%E7%94%B0%E7%A0%94%E3%81%AE%E5%A0%B4%E5%90%88?src=hash&amp;ref_src=twsrc%5Etfw">#上田研の場合</a> <a href="https://t.co/a0YZncQFBe">pic.twitter.com/a0YZncQFBe</a></p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/1031497790562566145?ref_src=twsrc%5Etfw">August 20, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">誰だこんなもん作ったの💢 <a href="https://t.co/9VaPduakhL">pic.twitter.com/9VaPduakhL</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/1082503780736749569?ref_src=twsrc%5Etfw">January 8, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">お腹痛いwwwwwwwwwwwwww <a href="https://t.co/cPS0gEZR8O">pic.twitter.com/cPS0gEZR8O</a></p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/1088673293421273089?ref_src=twsrc%5Etfw">January 25, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">未ロボ新B3の方々 &gt; こんな感じの研究室ですのでご自由に見学どうぞ。（何やってるのか全く伝わらない・・・）<a href="https://t.co/FZIZYzIzLt">https://t.co/FZIZYzIzLt</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/1111622098647044096?ref_src=twsrc%5Etfw">March 29, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">昨日ハッパをかけられた4年生の精神が壊れ始めて変な遊びが流行り始めたのでもうダメかもしれません。 <a href="https://t.co/eNlZLbZ3Au">pic.twitter.com/eNlZLbZ3Au</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/1092660475236511744?ref_src=twsrc%5Etfw">February 5, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">上田研発謎宗教の道具 <a href="https://twitter.com/hashtag/%E6%8D%A8%E3%81%A6%E3%81%BE%E3%81%99?src=hash&amp;ref_src=twsrc%5Etfw">#捨てます</a> <a href="https://twitter.com/hashtag/%E9%99%90%E7%95%8C%E7%A0%94%E7%A9%B6%E5%AE%A4?src=hash&amp;ref_src=twsrc%5Etfw">#限界研究室</a> <a href="https://t.co/QPVat7hzrO">pic.twitter.com/QPVat7hzrO</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/1011806899094708224?ref_src=twsrc%5Etfw">June 27, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">上田「んなことやってないで論文書いてー💢」<br>H氏「単位が・・・欲しい・・・」 <a href="https://t.co/qo9zgWp6SB">pic.twitter.com/qo9zgWp6SB</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/1074829143185940480?ref_src=twsrc%5Etfw">December 18, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">これひどすぎるやろwwwwwwwww <a href="https://t.co/q7z5UTOTTz">pic.twitter.com/q7z5UTOTTz</a></p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/983967709149868032?ref_src=twsrc%5Etfw">April 11, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">わ～い。スプレッドシートでロボット動いた～ <a href="https://twitter.com/hashtag/%E6%99%82%E9%96%93%E3%81%AE%E7%84%A1%E9%A7%84?src=hash&amp;ref_src=twsrc%5Etfw">#時間の無駄</a> <a href="https://twitter.com/hashtag/%E7%84%A1%E9%A7%84%E3%81%AE%E6%A5%B5%E3%81%BF?src=hash&amp;ref_src=twsrc%5Etfw">#無駄の極み</a> <a href="https://twitter.com/hashtag/%E6%AC%A1%E5%9B%9E%E3%81%AF%E3%82%B9%E3%83%97%E3%83%AC%E3%83%83%E3%83%89%E3%82%B7%E3%83%BC%E3%83%88%E3%81%A7%E8%BF%B7%E8%B7%AF%E8%B5%B0%E8%A1%8C?src=hash&amp;ref_src=twsrc%5Etfw">#次回はスプレッドシートで迷路走行</a> <a href="https://t.co/tatsUBYUHg">pic.twitter.com/tatsUBYUHg</a></p>&mdash; おーかわ (@masamasa9841) <a href="https://twitter.com/masamasa9841/status/879931680286429184?ref_src=twsrc%5Etfw">June 28, 2017</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="und" dir="ltr"><a href="https://t.co/6am8ySZVF3">pic.twitter.com/6am8ySZVF3</a></p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/879601202790453248?ref_src=twsrc%5Etfw">June 27, 2017</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">学生部屋に行ったら自分の私物が分解されててこの研究室には治安が悪いんじゃなくて治安という概念がないことを再認識した。 <a href="https://twitter.com/hashtag/%E3%83%89%E3%82%A4%E3%83%92%E3%83%BC?src=hash&amp;ref_src=twsrc%5Etfw">#ドイヒー</a> <a href="https://t.co/4eCbUrujSf">pic.twitter.com/4eCbUrujSf</a></p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/879266943462588416?ref_src=twsrc%5Etfw">June 26, 2017</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">「うんこを載せることができた」 <a href="https://twitter.com/hashtag/%E3%82%BC%E3%83%9F?src=hash&amp;ref_src=twsrc%5Etfw">#ゼミ</a> <a href="https://twitter.com/hashtag/%E3%81%8A%E3%81%84?src=hash&amp;ref_src=twsrc%5Etfw">#おい</a> <a href="https://t.co/gnnrzhjtRn">pic.twitter.com/gnnrzhjtRn</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/861440027540115456?ref_src=twsrc%5Etfw">May 8, 2017</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">自動で孵化 <a href="https://t.co/9ORCTuOGH2">pic.twitter.com/9ORCTuOGH2</a></p>&mdash; ハバタ (@habatafuture) <a href="https://twitter.com/habatafuture/status/759757757150965761?ref_src=twsrc%5Etfw">July 31, 2016</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">やめろおおおおおお！！！ <a href="https://t.co/FQ9LlUPAxp">https://t.co/FQ9LlUPAxp</a></p>&mdash; CIT未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/752387565127208960?ref_src=twsrc%5Etfw">July 11, 2016</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" data-partner="tweetdeck"><p lang="ja" dir="ltr">「学生部屋で豚キムチ食べてたら臭いと言われたので先生の部屋で食ってました」<br><br>💢💢💢💢💢💢💢💢💢💢💢</p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/1055702374084304896?ref_src=twsrc%5Etfw">October 26, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

