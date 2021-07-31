<template>
  <div id="app">
    <input v-model="message" placeholder="edit me"/>
    <p>Message is: {{ message }}</p>
    <p>
      <button @click="message= 'input'">set message to input</button>
    </p>

    <textarea v-model="message" placeholder="edit me"/>
    <p>Message is: {{ message }}</p>
    <p>
      <button @click="message= 'textarea'">set message to textarea</button>
    </p>

    爱好(复选框)：{{ x }}
    <label>
      <input type="checkbox" v-model="x" :value="1"/>
      <span>写代码</span>
    </label>
    <label>
      <input type="checkbox" v-model="x" :value="2"/>
      <span>学算法</span>
    </label>
    <label>
      <input type="checkbox" v-model="x" :value="3"/>
      <span>做项目</span>
    </label>

    <br/>

    希望做(单选框)：{{ y }}
    <label>
      <input type="radio" name="want" v-model="y" :value="1"/>
      <span>写代码</span>
    </label>
    <label>
      <input type="radio" name="want" v-model="y" :value="2"/>
      <span>学算法</span>
    </label>
    <label>
      <input type="radio" name="want" v-model="y" :value="3"/>
      <span>做项目</span>
    </label>
  </div>

  <br/>

  选择题(下拉列表--单选): {{ z }}
  <br/>
  <!--  复制当前行 ctrl+d -->
  <select v-model="z">
    <option value="">请选择</option>
    <option v-for="item in array1" :value="item.value" :key="item.value">
      {{ item.text }}
    </option>
  </select>

  <br/>

  选择题(下拉列表--多选): {{ a }}

  <br/>
  <br/>

  <select multiple v-model="a">
    <option value="">请选择</option>
    <option v-for="item in array2" :value="item.value" :key="item.value">
      {{ item.text }}
    </option>
  </select>

  <br/>
  <br/>

  {{ user }}
  <hr/>
  登录界面
  <form @submit.prevent="onSubmit">
    <label>
      <span>用户名</span>
      <MyInput v-model.lazy="user.username" />

      <!--   .lazy 在移出选框的时候变化   -->
      <!--   .number 在只想要数字的时候使用，返回数字,并且也要初始化为数字   -->
      <!--   .trim 去掉首尾空格   -->

      <!--   v-model 的等价写法如下：   -->
      <!--            <input type="text" :value="user.username" @input="user.username = $event.target.value" />-->
      <!--      <input type="text" v-model.trim="user.username">-->
    </label>
    <label>
      <span>密码</span>
      <input type="password" v-model="user.password">
    </label>
    <button>登录</button>
  </form>

</template>

<script>
import MyInput from "./MyInput.vue";

export default {
  components: {MyInput},
  name: 'App',
  data() {
    return {
      message: 'Hi',
      array1: [
        {text: "写代码", value: 1},
        {text: "学算法", value: 2},
        {text: "做项目", value: 3},
        {text: "全栈", value: 4}
      ],
      array2: [
        {text: "写代码", value: 1},
        {text: "学算法", value: 2},
        {text: "做项目", value: 3},
        {text: "全栈", value: 4}
      ],
      x: [],
      y: '',
      z: "",
      a: [],
      user: {
        username: '',
        password: ''
      },

    }
  },

  methods: {
    onSubmit() {
      console.log(this.user);
    }
  },
}
</script>
