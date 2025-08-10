<template>
  <div>
    <h3>List Demo</h3>
    <!-- <p v-for="item in list">{{ item }}</p> -->
    <!-- index数组下标 -->
    <!-- in->换成of 也可以 of更接近js迭代器 -->
    <p v-for="(item, index) in list">{{ item }}-{{ index }}</p>
    <!--result 数组  循环渲染最好有唯一的key值-->
    <div v-for="item in result" :key="item.id">
      <p>
        {{ item.id }} - {{ item.name }} - {{ item.age }} - {{ item.address }}
      </p>
    </div>
    <!-- 对象 -->
    <div>
      <p v-for="(value, key, index) in user">
        {{ key }} - {{ value }}-{{ index }}
      </p>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      list: [1, 2, 3, 4, 5],
      result: [
        {
          id: 1,
          name: "张三",
          age: 20,
          address: "北京",
        },
        {
          id: 2,
          name: "李四",
          age: 25,
          address: "上海",
        },
      ],
      user: {
        name: "lili",
        age: 25,
      },
    };
  },
};
</script>