---
title: js工厂模式
categories:
- javascript
tags:
- javascript
---

# js设计模式（工厂模式）

将许多类封装在一个函数里，然后通过这个函数可以创建我需要的对象。这种函数通常被称为工厂函数，这种模式通常被称作工厂模式

``` js
function Basketball() {
  this.intro = '我是一个篮球'
}
Basketball.prototype = {
  getMember() {
    console.log('每个队伍需要5名队员')
  },
  getBallSize() {
    console.log('篮球很大')
  }
}

function Football() {
  this.intro = '我是一个足球'
}
Football.prototype = {
  getMember() {
    console.log('每个队伍需要11名队员')
  },
  getBallSize() {
    console.log('足球很大')
  }
}
function Tennis() {
  this.intro = '我是一个窝囊求'
}
Tennis.prototype = {
  getMember() {
    console.log('每个队伍需要1名队员')
  },
  getBallSize() {
    console.log('网球很小')
  }

}
function SportsFaactory(name) {
  switch (name) {
    case 'basketball':
      return new Basketball()
      case 'football':
      return new Football()
      case 'tennis':
      return new Tennis()
  }
}
var basketball = SportsFaactory('basketball')
var football = SportsFaactory('football')
var tennis = SportsFaactory('tennis')
basketball.getBallSize()
football.getBallSize()
tennis.getBallSize()
```

