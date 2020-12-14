---
title: "CMakeでC++のバージョンを指定する"
date: "2020-07-18"
layout: article.njk
---

CMake と C++ を使った開発をしていたのですが、ユニークポインタ(`std::unique_ptr`)を構築する関数である`std::make_unique`を使おうとしたところ、以下のようなエラーが出てしまいました。

```text
/(省略)/gb.cpp:5:16: error: no member named 'make_unique' in namespace 'std'
    cpu = std::make_unique<CPU>();
          ~~~~~^
```

ちゃんと`#include <memory>`しているはずなのにおかしいな〜と思って調べたところ、そもそも`std::make_unique`が C++14 で追加された機能だということが分かりました。

正しくビルドするには、CMake に C++ のバージョンを教えてあげなければいけないようです。

結論として、`CmakeLists.txt`に以下の項目を追加したら、正しくビルドできるようになりました。

```cmake
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
```

はじめの行で C++ のバージョンを指定し、次の行でそれを有効化しています。

### 参考文献

https://stackoverflow.com/questions/24609271/errormake-unique-is-not-a-member-of-std
