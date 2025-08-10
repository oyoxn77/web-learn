<template>
  <div>
    <h3>条件渲染</h3>
    <div v-if="show">see</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: true,
    };
  },
};
</script>