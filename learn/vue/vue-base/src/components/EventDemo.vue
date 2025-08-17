<template>
  <div>
    <button @click="addCount">button</button>
    <p
      @click="getName(item, $event)"
      v-for="(item, index) in items"
      :key="index"
    >
      {{ item }}
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      items: ["lili", "lucy", "mick"],
    };
  },
  methods: {
    addCount(e) {
      console.log(e);
      e.target.innerText = "clicked" + this.count;
      this.count++;
      console.log(this.count);
    },
    getName(name, e) {
      console.log(e);
      console.log(name);
    },
  },
};
</script>