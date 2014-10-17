---
title: puts secrets
date: 2014-10-16 08:34 UTC
tags: programming, ruby, puts
---

[RubyTapas](http://www.rubytapas.com/) (Ruby プログラミングを扱った有料
スクリーンキャスト) のエピソード 171 'puts' を観てヘェーと思ったのでメ
モです。

* puts は正しくは「プットエス」と読む
  `puts` は C 関数の `puts(3)` と同じく "put string" の略なので、「プッツ」
  ではなく「プットエス」と読む。意味的にもこっちのほうが誤解がなくてよろしい。

* 改行の自動追加は別の write として扱われる
  複数スレッドでそれぞれ `puts` すると、スレッド実行がインターリーブし
  て次のように出力が混ざることがある。

```ruby
t1 = Thread.new do
  10.times { puts 'apple' }
end

t2 = Thread.new do
  10.times { puts 'orange' }
end

t2.join
t1.join
```

実行結果:

```
apple
orange
orangeapple

apple
...
```

原因は引数文字列の出力と `puts` が最後に自動的に追加する改行の出力が、
それぞれ別の `write` として処理されるため。

解決方法は、ワザと最後に改行を入れてやる。こうすると `puts` が最後の改
行を取り除き、出力を一つの `write` として処理するので混じらない。

```ruby
t1 = Thread.new do
  10.times { puts "apple\n" }
end

t2 = Thread.new do
  10.times { puts "orange\n" }
end
```
