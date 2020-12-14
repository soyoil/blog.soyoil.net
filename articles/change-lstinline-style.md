---
title: "lstlistingとlstinlineで違うスタイルを適用する"
date: "2020-12-14"
layout: article.njk
---

LaTeX の`listings`パッケージでは`\lstset`を使うことによりスタイルを調整することができます。

例えば、フォントのサイズを小さくしようと思った場合は以下のように設定することができます。

```tex
\documentclass{jsarticle}
\usepachage{color}
\usepackage{listings}

\lstset {
  \basicstyle=%
    \ttfamily%
    \scriptsize
}

\begin{document}
関数\lstinline{foo}の定義は以下の通りである。
\begin{lstlisting}
void foo(char *foo, int bar);
\end{lstlisting}
\end{document}
```

しかしこのままコンパイルすると、`\lstinline{foo}`まで文字が小さくなってしまいます。

`lstinline`のスタイルはそのままで、`lstlisting`のスタイルだけ変えるには、以下のように設定すると良いようです。

```tex
\lstset {
  \basicstyle=%
    \ttfamily%
    \lst@ifdisplaystyle\scriptsize\fi
}
```

このようにすれば、`\lstlisting`の文字のみを小さくすることができます。

### 参考文献

https://tex.stackexchange.com/questions/161549/scaling-inline-code-to-the-current-font-size
