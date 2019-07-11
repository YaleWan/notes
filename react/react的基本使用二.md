---
title:react的基本使用二
categories:
- react
tags:
- react
---

# react 的基本使用

## 1. 基本构造

react 最基本的构造如下

``` js
<!DOCTYPE html>
  <html>
  <head>
  <script src="../build/react.js"></script>
  <script src="../build/react-dom.js"></script>
  <script src="../build/browser.min.js"></script>
  </head>
  <body>
    <div id="example"></div>
    <script type="text/babel">
      ReactDOM.render(
      <h1>Hello, world!</h1>,
      document.getElementById('example')
    );
</script>
</body>
</html>
```

 我们所引进来的三个库，其中`react.js`是React的核心库，`react-dom.js`是提供与DOM 相关的功能，`browser.js`的作用是将JSX语法转为JavaScript语法。 其中`text/babel`这是因为React独有的JSX语法，跟JavaScript不兼容。

## 2. JSX语法

``` js
var animals = ['cat', 'dog', 'mouse'];
ReactDOM.render(
  <div>
  {
    animals.map(function (animal) {
      return <div>Hello, {animal}!</div>
    })
  }
  </div>,
  document.getElementById('example')
);
```

上面这行例子，提现了 JSX的基本规则，遇到`<`标签开头，就已HTML规则解析，遇到`{`标签开头，就用JavaScript规则解析。如果变量是一个数据，JSX会默认将所有数据成员展开。

## 3. 组件

React可以将代码封装成组件，然后像插入HTML标签一样，在网页中插入这个组件

``` js
class NotesList extends React.Component {
  render() {
    return (
      <ol>
      {
        React.Children.map(this.props.children, function (child) {
        return <li>{child}</li>;
      })
  }
  </ol>
  );
}
}

ReactDOM.render(
  <NotesList name='john'>
  <span>hello</span>
  <span>world</span>
  </NotesList>,
  document.getElementById('example')
);
```

**注意**：组件类名必须大写，组件类只能包含一个顶层标签，否则会报错，所有的组件类必须有自己的render方法，用于输出组件。

组件标签和HTML标签一致，可以添加属性，比如`NotesList`组件添加了一个`name`属性。该属性可以在属性类上通过`this.props`对象上获取,比如`name`通过`this.props.name`获取。

`this.props.children`属性表示组件所有的子节点，比如上方`NotesList`组件有两个span子节点，他们可以在组件类中通过`this.props. children`获取。

**注意**`this.props.children`的值有三种可能，