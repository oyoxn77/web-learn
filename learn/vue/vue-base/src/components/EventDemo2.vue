<template>
  <div>
    <h3>事件修饰符</h3>
    <!-- <a href="https://www.baidu.com" @click="clickHandle($event)">百度</a> -->
    <a href="https://www.baidu.com" @click.prevent="clickHandle()">百度</a>
    <div @click="clickDiv">
      <!-- <p @click="clickP($event)">测试冒泡</p> -->
      <p @click.stop="clickP()">测试冒泡</p>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    clickHandle(e) {
      // e.preventDefault(); // 阻止默认事件
      console.log("点击了百度");
    },
    clickDiv() {
      console.log("点击了div");
    },
    clickP() {
      // e.stopPropagation(); // 阻止冒泡
      console.log("点击了p");
    },
  },
};
</script>