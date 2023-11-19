<script setup>
import {ref} from "vue";
import MySonComponents from "@/components/SonComponents/MySonComponents.vue";
const message = ref("hello");
const message1 ="Hello World";
const contentHtml =ref("<a href='https://www.google.com.hk/webhp?hl=zh-CN&sourceid=cnhp'>百度</a>");
const theme=ref("redTheme");
const number=50;
const bool=ref("true");
const newList=ref([
  {id:1001, title:"今日头条",},
  {id:1002, title:"娱乐板块",},
  {id:1003, title:"军事新闻",},
  {id:1004, title:"体育赛事",},
  {id:1005, title:"美食频道",}
])
const user =ref({
  username:"",
  password:""
})

function changeTheme(){
  if(theme.value==="redTheme"){
    theme.value="greenTheme"
  }
  else{
    theme.value="redTheme"
  }
}
function login(){
  alert(user.value.username)
  alert(user.value.password)
}


function del(id){
  newList.value = newList.value.filter(item => item.id !== id)
}

</script>



<template>

  <h3>学习vue常用语法</h3><br>
  <p>{{message}}</p>
  <p>{{message1}}</p>
  <input type="text" placeholder="请输入" v-model.number="message">

  <div v-html="contentHtml"></div>
  <button @click="changeTheme">改变主题</button>
  <div :class="theme"></div>
  <p>{{number>10}}</p>

  <div v-show="bool">
    <div :class="theme"></div>
  </div>
  <div v-if="bool">
    zhen
  </div>
  <div v-else>
    jia
  </div>

  <ul >
    <li  v-for="(item, index) in newList" :key="item.id">
      <div >
        <span >{{ index + 1 }}.</span> <label>{{ item.title }}</label>
        <button @click="del(item.id)" >删除</button><br>
      </div>
    </li>
  </ul>
  <div>
    用户名：<input type="text" v-model.trim="user.username"><br>
    密码：<input type="password" v-model.trim="user.password">
  </div>

  <button @click="login">提交</button>


  <MySonComponents  :msg="message" :user="user"></MySonComponents>

</template>



<style scoped>
.redTheme{
  background-color: red;
  width:10vw;
  height:10vw;
}

.greenTheme {
  background-color: green;
  width: 10vw;
  height: 10vw;
}

</style>