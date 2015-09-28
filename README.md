# luatex-mini
LuaTeX minimum package for plain TeX 

## INSTALL

Suppose you want to install luatex-mini to $HOME/luatex-mini. Of course you can use other directories instead of  $HOME.

```bash
$ cd $HOME
$ git clone https://github.com/liyanrui/luatex-mini.git
```

Then compile luatex:

```bash
$ cd $HOME
$ svn checkout --username anonsvn https://foundry.supelec.fr/svn/luatex/trunk  #passwordd is anonsvn
$ cd luatex
$ ./build.sh  # you can do some other works until compile process finished.
```

After finished the compiling of luatex, you need copy some executable files to `$HOME/luatex-mini/bin`

```bash
$ cp $HOME/luatex/source/texk/web2c/luatex $HOME/luatex-mini/texmf-linux/bin
$ cp $HOME/luatex/source/texk/kpathsea/mktexlsr $HOME/luatex-mini/texmf-linux/bin
$ chmod +x $HOME/luatex-mini/bin/mktexlsr
$ cp $HOME/luatex/build/texk/kpathsea/kpseaccess $HOME/luatex-mini/texmf-linux/bin
$ cp $HOME/luatex/build/texk/kpathsea/kpsestat $HOME/luatex-mini/texmf-linux/bin
$ cp $HOME/luatex/build/texk/kpathsea/kpsewhich $HOME/luatex-mini/texmf-linux/bin
```

## Generate luatex.fmt

```bash
$ source $HOME/luatex-mini/setuptex
$ mktexlsr
$ cd $HOME/luatex-mini/texmf/tex/generic/luatex
$ luatex --ini --jobname=luatex --progname=luatex luatex-plain
$ mv luatex.fmt $HOME/luatex-mini/texmf-var/web2c/luatex/

## Test

hello.tex:

```tex
Hello Lua\TeX!

$$v=v_0 + \int_0^ti\,dt + Ri$$

\bye
```

Use `luatex` to compile `hello.tex` for generating `hello.pdf`:

```bash
$ luatex hello
```

If the process of cimpiling hangs up, you can press `Ctrl + d` to continue it.