---
title:写一个sleep(暂停)函数
categories:
- alg
tags:
- alg
---

# 写一个sleep(暂停)函数

- 不要写同步的暂停函数。它会让你的程序卡死。
- 写一个异步的暂停函数，这样可以在任何 `async function` 中暂停，且只暂停这一部分代码。

``` js
function sleep(milliseconds: number) {
    return new Promise<void>(resolve =>
        setTimeout(resolve, milliseconds))
}
void async function main() {
    // … do something …
    await sleep(5000)
    // … do something else …
}()
```

