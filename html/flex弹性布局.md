---
titile: flex弹性布局
categories:
- html
tags:
- html
---

# flex弹性布局

flex 弹性盒子模型声明 `display:flex`，那么这个元素就成为了弹性容器，具有flex弹性布局的特性。

1. 每个弹性容器都有两根轴：**主轴和交叉轴**，两轴之间成90度关系。注意：**水平的不一定就是主轴。**
2. 每根轴都有**起点和终点**，这对于元素的对齐非常重要。
3. 弹性容器中的所有子元素称为<弹性元素>，**弹性元素永远沿主轴排列**。
4. 弹性元素也可以通过`display:flex`设置为另一个弹性容器，形成嵌套关系。因此**一个元素既可以是弹性容器也可以是弹性元素**。

**容器属性**

- flex-flow
- flex-direction
- flex-wrap
- justify-content
- align-items
- algin-content

**元素属性**

- order
- flex-grow
- flex-shrink
- flex-basis
- flex
- align-self