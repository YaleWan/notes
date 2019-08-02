---
title: js 优雅写法总结
categories:
- javascript
tags:
- javascript
---

# js优雅写法

- 封装多个函数

  传统写法

  ``` js
  function checkName(){}
  function checkEmail(){}
  function checkPassword(){}
  .....
  ```

  优雅写法

  ``` js
  let checkType = function(){
    this.addCheck = (type ,fn) =>{
      this[type] = fn;
      return this;
    }
  }
  let check = new checkType()

  check.addCheck('checkName',()=>{
      console.log('this is checkName')
  	return this;
  }).addCheck('checkPsw',()=>{
      console.log('this is checkPsw')
  	return this;
  })
  a.checkName().checkPsw()
  ```

