<template>
  <div>
    <h3>模板语法</h3>
    <!-- <p v-bind:class="msg2">{{ msg }}</p> -->
    <p :class="msg2">{{ msg }}</p>
    <p>{{ num + 10 }}</p>
    <p>{{ ok ? "YES" : "NO" }}</p>
    <p>{{ message.split("").reverse().join("") }}</p>
    <p>{{ raw }}</p>
    <p v-html="raw"></p>
    <div v-bind="objectAttr">测试</div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      msg: "Hello Vue!",
      num: 100,
      ok: true,
      message: "大家好",
      raw: '<a href="#">Learn Vue.js</a>',
      msg2: "active", //动态绑定属性
      objectAttr: {
        name: "张三",
        age: 20,
      },
    };
  },
};
</script>

<style>
.active {
  color: red;
}
</style>