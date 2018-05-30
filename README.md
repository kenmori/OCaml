## OCaml初心者が入門する

*随時更新*

最新更新日 2018/5/30


## install

```
brew install ocaml
brew install opam (パッケージマネージャー)
brew install rlwrap (Ocmalインタプリタで履歴が打てる)
```
## rlwrapを使用してocamlを立ち上げる

```
rlwrap ocaml
```
rlwrap ・・・OCamlインタプリタシェルで 最後のコマンドを繰り返したい場合に使うもの。履歴を辿れる。ocamlはそれ自体これらをサポートしていないためinstallすると良い。


## コメント

```
(* something *)

(* This is a
 * multi-line
 * comment.
 *)
```

## 行の終わり

```
;;
```

## 終了
```
exit 0;;
//or
#quit;;
```

## コンパイル

```
$ mkdir my_project
$ cd my_project
$ echo 'let () = print_endline "Hello, World!"' > my_prog.ml
```

_To compile an OCaml program named my_prog.ml to a native executable, use ocamlbuild my_prog.native_

```my_prog.ml``` というOCamlプログラムをネイティブ実行可能にコンパイルするには ```ocamlbuild my_prog.native``` と打ちます


## OCamlのgitignore

```
*.annot
*.cmo
*.cma
*.cmi
*.a
*.o
*.cmx
*.cmxs
*.cmxa

# ocamlbuild working directory
_build/

# ocamlbuild targets
*.byte
*.native

# oasis generated files
setup.data
setup.log

# Merlin configuring file for Vim and Emacs
.merlin
```



## module

あるファイルの関数をmoduleとして使う

```
//amodule.ml
let hello () = print_endline "Hello, World!"

//main.ml
Amodule.hello ()

```
amodule.mlのhelloを使うの意味。最初の文字がincludeするファイル名の大文字であることに注意

## 型変換

```
(* 型変換*)
let i = 1;;
let f = 2.0;;
float i +. f;;

//or

(float_of_int i) +. f;;
//float_of_intは int型をfloatにして返す関数
```

## 再起

```let rec``` とすることで自身から呼ぶことができる。
recをつけないとrangeが呼ばれたとき前もって定義されているものとしてrangを探しに行ってしまう

```
# let rec range a b =
  if a > b then []
  else a :: range (a+1) b;;
val range : int -> int -> int list = <fun>
```


## 理解を助けるリンク

・[Errorメッセージ集](http://www.willforge.fr/wikisys/index.php?title=OCaml/Error_messages)

## Question

### ```ocamlc``` と ```ocamlopt```てなあに??

```
ocamlc・・・バイトコードにコンパイルする
ocamlopt・・・ネイティブコードにコンパイルする
どちらを使っていいかわからない場合ocamloptでok
```

### ```ocamlopt -o progprog module1.ml module2.ml``` は何をしている？

```
-o exec-file ・・・ 出力するファイル名を明示して実行ファイルを生成するオプション。 -c ならコンパイルのみ
progprog ・・・ ファイル名
module1.ml module2.ml ・・・依存する順番を指定して渡している。渡す順番を間違えてはいけない(module1はmodule2に依存してはいけない)
```

### ```ocamlbuild my_prog.native```したらこれらが生成されましたけど？これらはなあに？？

```
_digests
_log
my_prog.cmi
my_prog.cmo
my_prog.cmx
my_prog.ml
my_prog.ml.depends
my_prog.native*
my_prog.o

```





# WIP

```
WIP
```


## 参照
[OCaml.gitignore](https://github.com/github/gitignore/blob/master/OCaml.gitignore)

[コンパイルオプション](https://caml.inria.fr/pub/docs/manual-ocaml/native.html)

[https://ocaml.org/learn/tutorials/modules.ja.html](https://ocaml.org/learn/tutorials/modules.ja.html) OCaml
