---
title: "Fishで、ファイルに保存した内容をechoする"
date: "2021-05-01"
layout: article.njk
---

ANSI エスケープシーケンスを含む複雑なアスキーアートをファイルに保存し、`echo`で表示させたかった。

bash などであれば

```bash
echo -e "$(<asciiart.txt)"
```

とすれば良いようだが、fish の場合は`<`がうまく使えなかったので、代わりに`cat`を使って

```bash
echo -e (cat asciiart.txt)
```

とすればよい。

もしかしたらもっと単純な方法があるかもしれない。
