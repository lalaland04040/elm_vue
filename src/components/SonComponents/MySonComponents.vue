<script setup>

import {ref} from "vue";
const msg1="消息1"
const msg2="消息2"
defineProps({
  msg:{
    type:String,
    required:true,
    default:"我是个默认值"
  },
  news:{
    type:Array,
    required:false,
    default:[
        {id:1001, title:"今日头条",},
        {id:1002, title:"娱乐板块",},
        {id:1003, title:"军事新闻",},
        {id:1004, title:"体育赛事",},
        {id:1005, title:"美食频道",}
    ]
  },
  user:{
    type:Object
  }
})
const number=ref("hello")

function sendMsg(){

}

</script>


<template>
<p>{{msg}}</p>
<p>{{number}}</p>
<p>{{ user }}</p>

  <input type="text" v-model="number">

  <ul >
    <li  v-for="(item, index) in news" :key="item.id">
        <span >{{ index + 1 }}.</span> <label>{{ item.title }}</label>
    </li>
  </ul>
  <input type="text" v-model="msg1">
  <input type="text" v-model="msg2">
  <button @click="sendMsg">点击</button>
</template>


<style scoped>

</style>