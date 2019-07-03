## 事件总线bus解决兄弟组件之间的传值

实际运用：

封装一个`Bus.js`

```js
import Vue from 'vue'
const Bus = new Vue()
export default Bus 
```

在组件调用时引入

组件一：

```js
import Bus from './Bus'

  export default {
    data() {
      return {
        .........
      }
    },
    methods: {
      ....
      Bus.$emit('log', 120)
    },

  }
```

组件二：

```js
import Bus from './Bus'

  export default {
    data() {
      return {
        .........
      }
    },
    mounted () {
      Bus.$on('log', content => { 
        console.log(content)
      });    
    }    
  }
```

