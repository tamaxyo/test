---
title: middleman-blogのセットアップ
date: 2014-01-06 08:30 JST
tags: middleman
---

middlemna-blogのセットアップメモ。

### middlemanのインストール

何も難しくはない。

```
gem install middleman
```

### middlemanの初期化
middlemanを使うためのテンプレートファイル(jsとかcssとか)が生成される。
多分、別にやらなくてもいい気がする。

```
middleman init [dir]
```

### middleman-blogの初期化
blog特化のテンプレートファイル(calendarとかtagとかfeedとか)が生成される。
config.rbに設定のテンプレートが配備されるので、コメントを眺めながらカスタマイズ。

```
middleman init [dir] --template=blog
```

### middleman-deployの導入
今回はGitHub Pagesのユーザサイトを構築しているので、masterブランチにpushするように設定。

```ruby
activate :deploy do |deploy|
  deploy.method = :git
  deploy.branch = 'master' #=> ユーザページなのでmasterにpush
  deploy.build_before = true #=> deploy前にbuild実行
end
```

## はまったこと
[middlemanの公式情報](http://middlemanapp.com/basics/blogging/)を眺めてて、``blog.prefix``という設定を見かけたので、なんとなく使ってみたのだけれどこれが上手く動かず、記事を年月のディレクトリ階層に分かれなかったりしたので、それを諦めたら結構簡単に設定は終わった。

あとはデザインとかコンテンツとかとかとかとか・・・


## 参考にした情報
多謝 m(_ _)m

- [ブログをJekyllからmiddlemanに移行してTravis CIでGitHub Pagesにデプロイするようにした](http://webtech-walker.com/archive/2013/08/jekyll_to_middleman.html)

- [middleman-blogをgithubでホストする](http://blog.coiney.com/2013/06/21/host-middleman-blog-on-github/)

