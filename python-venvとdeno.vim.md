# minicondaからvenvに乗り換えた
python2.7時代からcondaを使ってきていたけど、インストールできないパッケージなどもありvenvに乗り換えた。  
その際のPATHの競合がありメモ。

# 環境
* ターミナル
    GNOMEターミナル
* vim
    パッケージ管理にdeno.vimを使用  
    .bashrcに~/.denoがdenoのホームディレクトリと定義(DENO\_INSTALL=~/.deno)

# 起こったこと
てきとうな仮想環境をvenvで作ってactivateしたらvim起動時にdeno.vimのpathが無いと警告された

# 解消
結論からいうと.bashrcにdenoのホームディレクトリ定義を記載したのがダメだったらしい  
venvで作られるactivateを見るとインタラクティブシェルの環境変数を上書きする形になっていた  
deno.vimのホームディレクトリpathが消えてもらっちゃ困るので  

* .bash\_profileの中にdeno.vimのpathを記載
* gnomeターミナルをインタラクティブシェル起動(bashrcを読む)でなくログインシェル起動(bash\_profileを読む)に変更

で解消
