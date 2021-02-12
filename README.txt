「jelyllで0からサイトを作る(fefault theme)」

・Githubでレポジトリを作る。
・Ruby, jekyllのインストール
http://jekyllrb-ja.github.io/docs/installation/windows/
	「以上で、Jekyllを使用する準備ができました！」までやる。


・コマンドプロンプトでデスクトップ～フォルダまで移動
	$ cd ～desktop
	$ jekyll new フォルダ（jelyllの構成ファイルが作成される）
	$ cd フォルダ


・作成したフォルダの中にあるの_config.ymlの変更(VS codeで開くことができる)
	baseurl: "/レポジトリ名" 
	url: "https://ユーザー名.github.io"


$ jekyll server --watch		＃prwview 兼 build(_siteフォルダ内にhtmlが出力される)

$ jekyll build --d docs		＃docs内にhtmlなどが出力（デフォルトでは_siteだが、github pagesのためにdocsに出力）


・githubへのpush
$ git init 
$ git remote add origin URL
$ git add .
$ git commit -m "コメント"
$ git push origin master

Githubでsettingをdocsに


<jekyllで作ったサイトの更新作業>
	https://e-joint.jp/346/






「alembicのテンプレートを利用してサイトを作る」
alembicのkitをダウンロード

$ cd ダウンロードしたフォルダ

$ bundle install	＃gemファイルに書かれている必要なgemをダウンロードしてくれる。初回のみでよいはず
($ bundle update)	＃bundlerが必要なgemを依存関係を整理しながらアップデートしてくれる。定期的に行う。

_config.ymlのURL/base URLの調整

$ bundle exec jekyll server	#previewできる（_siteに出力もされる）

$ bundle exec jekyll build --d docs（buildする前にdocsを消す。毎回必要な作業になると思う。いつかこのバグ?が解消されますように）






「just the docの使い方」
https://sh-2.github.io/just/
このサイトを参照。Githubリポジトリも右上から飛べる


$ jekyll new フォルダ
_post消して、config, gemfile,マークダウン等編集

<cofig.yml>
baseurl: "/リポジトリ名" 
url: "https://ユーザ名.github.io" 

theme: "just-the-docs"	#に上書き


<gemfile>
gem "minima", "~> 2.5"	#消す
# gem "github-pages", group: :jekyll_plugins	#ここはコメントアウトしたままでいいかも。
gem "just-the-docs"	#config.ymlにremote themeを書く必要はないかも。themeのどちらかで良い？

<マークダウンファイル>
nav barがちゃんとしていればどこにおいてもよさそう。

$ cd ~フォルダ
$ bundle install
$ bundle update
($ bundle exec jekyll s)	#たまに更新されない。githubにupしたときに正常になる場合も。
$ bundle exec jekyll buidl -d docs	#docs多重問題健在
$ git init
$ git add .
$ git commit -m "コメント"
$ git remote add origin リポジトリURL
$ git push origin master
githubのsettingをdocsに

<諸注意>
gemfile（やconfig,yml）をいじると色々なエラーが起こるときがある。
jekyll serverは更新されないときがあるので、ファイルやターミナルを閉じてから再度やる。or無視してgit push



「不明点、今後の作業」
Jekyll, gem, Bundlerの存在・意義・関連がよくわからない。
gem file（やconfig.yml）を上手く扱えない。エラーの主要因。live demoでいわれてないことはしない方がいいかも。

どのgemfile、configがアウトか探す。
just-the-docsの編集練習