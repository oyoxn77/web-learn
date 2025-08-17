<template>
  <div>
    <h3>{{ itContent.name }}</h3>
    <p>{{ itContent }}</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      itContent: {
        name: "lili",
        content: ["py", "c", "js"],
      },
    };
  },
  computed: {
    itContent() {
      return this.itContent.content.length > 0 ? "有内容" : "无内容";
    },
  },
};
</script>