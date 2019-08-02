---
title:JavaScript中打乱数组排序
categories:
- alg
tags:
- alg
---

 # JavaScript中打乱数组排序

+ 利用sort()函数

  ``` js
  arr.sort(()=>Math.random() - 0.5)
  ```

  但是这种排序由于v8引擎中针对短数组和长数组使用了不同的排序方法。并且sort方法中对于同一组a,b值需要总是返回相同的值。

+ Fisher-Yates shuffle(洗牌算法)

  ``` js
  function shuffle(arr) {
    let i = arr.length;
    while (i) {
      let j = Math.floor(Math.random() * i--);
      [arr[j], arr[i]] = [arr[i], arr[j]];
    }
  }
  ```

  ``` js
  function shuffle(arr) {
      arr.forEach((_, idx) => {
          const targetIdx = Math.floor(Math.random() * arr.length)
          ;[arr[idx], arr[targetIdx]] = [arr[targetIdx], arr[idx]]
      })
      return arr
  }
  ```

  如果要将数组随机排序，目前而言，Fisher–Yates shuffle 算法应该是最好的选择。

  ​