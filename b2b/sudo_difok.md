<<`solved!`>>

### Question
パスワードポリシーについて質問です。hoge というユーザーを作った際, HugaHuga123 というパスワードを sudo passwd hoge を使って設定した後に，再度 HugaHuga1234 というパスワードを設定するとした時，このパスワードは元のパスワードと異なる 文字を 1 つしか含んでいないため，" The password must have at least 7 characters that are not part of the former password " という条件を満たしていないと思うのですが， sudo passwd hoge で， 設定できてしまいました。私の設定ファイルに問題があると思うのですが， どこが悪いでしょうか？

以下，現在の /etc/pam.d/common-password ファイルの中身です。

![](../imgs/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202022-11-23%2021.41.04.png)

### Answer (takira)
今手元にpcが無く未検証なので嘘回答かもしれませんが、sudo権限だとdifokは無視されたはずです。sudoでパスワード変更するとcurrent passが求められない=diffが取れないため、だと思います。
ユーザーhogeでログインして、passwd hoge で変更すればdifokが効くとおもいますので確認してみてください！！

### Question (knitta)
あー、やはりそうでしたか。。おそらく、sudo を使ったら password が “最低2日間変更できない”という条件も無視できると思っているのですが、これはどうでしょうかね？僕の手元ではそういう挙動をするのですが…

### Answer (takira)
それは、rootに最短変更2日が適用されていない為かもしれません。
chage -l rootで確認してみてください〜 
課題的に、rootにもdifok以外のパスワードポリシーが適応された状態が正ですね

