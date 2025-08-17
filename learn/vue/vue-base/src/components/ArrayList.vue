<template>
  <div>
    <ul>
      <button @click="addItem">添加数据</button>
      <li v-for="(item, index) of items" :key="index">{{ item }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: ["lili", "linda", "lucy"],
    };
  },
  methods: {
    addItem() {
      //   this.items.push("tom");
      this.items.concat(["tom"]);
      this.items2 = this.items.concat(["tom"]);
      console.log(this.items);
      console.log(this.items2);
    },
  },
};
</script>