<template>
  <div id="app">
    <!-- 滚动容器 -->
    <div class="virtual-box" @scroll="onScroll" ref="container">
      <!-- 滚动虚拟条 -->
      <div class="virtual-scroll" :style="{ height: totalHeight + 'px' }">
        <!-- 滚动虚拟列表 -->
        <div
          class="virtual-list"
          :style="{ transform: `translateY(${startOffset}px)` }"
        >
          <!-- 只渲染visibleItems的数据 而不是全部items -->
          <div class="virtual-item" v-for="item in visibleItems" :key="item">
            {{ item }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [], // 虚拟列表数据
      itemHeight: 50, // 虚拟列表项高度
      // totalHeight: 0, // 虚拟列表总高度
      startOffset: 0, // 虚拟列表开始偏移量
      viewCount: 0, // 视图可见项数
      startIndex: 0, // 视图开始索引
    };
  },
  computed: {
    //原jsrenderData渲染数据部分
    visibleItems() {
      return this.items.slice(
        this.startIndex,
        this.startIndex + this.viewCount
      );
    },
    totalHeight() {
      return this.items.length * this.itemHeight;
    },
  },
  mounted() {
    //生成数据 计算viewCount
    for (let i = 0; i < 1000; i++) {
      this.items.push("item-" + i);
    }
    //$refs获取元素高度，相对于原来的container.offsetHeight
    const containerHeight = this.$refs.container.offsetHeight;
    this.viewCount = Math.ceil(containerHeight / this.itemHeight);
  },
  methods: {
    //滚动事件
    onScroll(e) {
      const scrollTop = e.target.scrollTop;
      this.startIndex = Math.floor(scrollTop / this.itemHeight);
      this.startOffset = scrollTop - (scrollTop % this.itemHeight);
    },
  },
};
</script>

 <style>
* {
  margin: 0;
  padding: 0;
  /* 更适合响应式布局 */
  box-sizing: border-box;
}

/* 滚动容器 */
.virtual-box {
  width: 100vw;
  height: 100vh;
  /* 水平居中 上下留白 */
  /* margin: 20px auto; */
  border: 2px solid red;
  /* 内容超出时可以滚动 */
  overflow: auto;
  position: relative;
}

/* 滚动虚拟条 */
.virtual-scroll {
  width: 100%;
}

/* 滚动列表容器高度 */
.virtual-list {
  position: absolute;
  width: 100%;
  height: 100%;
  /* top:0;
      left: 0; */
}

/* height 和 line-height 一致 垂直方向居中对齐 */
.virtual-item {
  height: 50px;
  line-height: 50px;
  /* padding: 5px 10px; */
  background-color: #f0f0f0;
  border: 1px solid green;
}
</style>