<template>
  <div class="p-c">
    <p>我是子组件</p>
    <p>通过父组件的v-model 传递的值 实现 显示隐藏</p>
    <p>{{ value }}</p>
    <p><button @click="handleChange()">改变</button></p>
  </div>
</template>

<script>
export default {
  name: "children",
  props: {
    value: {
      type: String,
      default: ""
    }
  },
  methods: {
    handleChange() {
      this.$emit("input", "改变");
    }
  }
};
</script>
<style scoped lang="less">
.p-c {
  .text-left();
  .menuList {
    display: flex;
    justify-content: flex-start;
    flex-wrap: wrap;
    span {
      padding: 5px 10px;
      margin: 5px;
      background: #999;
      color: #fff;
    }
    .active {
      background: #666;
    }
  }
  p {
    padding: 10px 0;
  }
  .border-bottom {
    border-bottom: 1px solid #ccc;
  }
  .title {
    text-align: center;
  }
}
</style>
