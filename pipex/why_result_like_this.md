*Solved!*

## Question(knitta) 
どのようなことがどのような順序で起きて，`< input.txt cat` というコマンドライン で input.txt の中身が表示されるのでしょうか？

![](./imgs/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202022-11-22%2017.49.38.png)


## Answer(ykondo) 
1. redirect in を処理する際にinput.txt をopenする。
2. 得られたfdをdup2を用いて標準入力と結びつける。
3. 今回はcatに引数がないのでcatが標準入力からの受け取りを出力する
4. 結果としてinput.txtの中身が出力される.
