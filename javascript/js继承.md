---
title: js继承
categories:
- javascript
tags:
- javascript
---

# js继承

  **类式继承**

``` js
  function Father(){
    this.hobby = ['swim','smoke']
  }
  function Son(){
    this.sonName = 'wang'
  }
  Son.prototype = new Father()
  let son = new Son()
  console.log(son.sonName)
  console.log(son.hobby)
```

  类式继承有个致命的缺点，当其中一个实例被修改时候，另一个实例也跟着对应的修改了,

``` js
  let son2 = new Son()
  son2.hobby.push('sleep')
  son.hobby // ['swim','smoke','sleep']
```

  **构造函数继承**

``` js
  function SuperClass(id){
    this.books = ['javascript','html','css']
    this.id = id;  
  }
  SuperClass.prototype.showBooks = function(){
    console.log(this.books)
  }
  function SubClass(id){
    SuperClass.call(this,id)
  }
  var instatncel = new SubClass(10) ;
  var instance2=new SubClass(11)
  instancel.books.push('vue')//['javascript','html','css','vue']
  instance2.books //[javascript,html,css]
  instancel.showBooks() //typeError
```

  由于call方法可以更改函数的作用环境，因此在子类中，对superclass调用这个方法就是将子类中的变量在父类中执行一遍，但是这种类型的继承没有设计原型prototype，所有父类的原型方法自然不会被子类继承。

  **组合继承**

``` js
  function SuperClass(){
    this.name = 'zhangsan'
    this.books = [
      'css',
      'javascript',
      'html'
    ]
  }
  SuperClass.prototype.getName = function(){
    console.log(this.name)
  }
  function SubClass(id){
    SuperClass.call(this)
    this.id = id
  }
  SubClass.prototype = new SuperClass()
  let instance1 = new SubClass(1)
  let instance2 = new SubClass(2)
  instance1.books.push('vue')
  console.log(instance1.books)//['css','javascript','html','vue']
  console.log(instance2.books)//['css','javascript','html']
  instance1.getName()//'zhangsan'
```

  组合模式就是将这两点的优势结合起来。

  **原型式继承**

  ​