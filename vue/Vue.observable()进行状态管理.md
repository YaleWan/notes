---
title:使用Vue.observable()进行状态管理
categories:
- vue
tags:
- vue
---

# 使用Vue.observable()进行状态管理

`Vue.observable(object)`是vue.js 2.6新增加的一个api，通过这个api我们可以应对一些简单的跨组件数据状态共享的情况。

来看一下实际应用：

+ **首先先创建一个store.js，包含一个store 和一个 mutations，分别用来指向数据和处理方法**

  ``` js
  //store.js
  import Vue from 'vue';

  export let store =Vue.observable({count:0,name:'李四'});
  export let mutations={
      setCount(count){
          store.count=count;
      },
      changeName(name){
          store.name=name;
      }
  }
  ```

+ **然后在组件Home.vue中引用，在组件里使用数据和方法：**

  ``` js
  //Home.vue
  <template>  
    <div class="container">  
      <home-header></home-header>  
    <button @click="setCount(count+1)">+1</button>
    <button @click="setCount(count-1)">-1</button>
    <div>store中count：{{count}}</div>
    <button @click="changeName(name1)">父页面修改name</button>
    <div>store中name：{{name}}</div>
    <router-link to="/detail" ><h5>跳转到详情页</h5>   </router-link>
      </div>  
  </template>  
  <script>  
  import HomeHeader from '../components/HomeHeader'   
  import {store,mutations} from '@/store'
  export default {  
     data () {  
        return {  
          name1:'主页的name'
         }  
      },  
      components: {  
        HomeHeader 
      },  
      computed:{
            count(){
              return store.count
            },
            name(){
              return store.name
            }
          },
          methods:{
            setCount:mutations.setCount,
            changeName:mutations.changeName    
          }
        }  
  </script>  
  ```

  ​