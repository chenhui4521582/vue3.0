<template>
  <div class="p-c">
    <p>我是子组件1</p>
    <p>接收子组件children2传递的值:</p>
    <p style="color: red">{{ receiveData }}</p>
    <button @click="sendParent">传递数据到子组件2</button>
  </div>
</template>

<script>
export default {
  name: "children",
  data: () => ({
    receiveData: ""
  }),
  created() {
    // 通过$bus 接收children2 传递过来的数据
    window.$bus.$on("dataformchildren", data => {
      this.receiveData = data;
    });
  },
  methods: {
    // 通过$bus 发送数据到 children2 传递过来的数据
    sendParent() {
      window.$bus.$emit(
        "dataToChildren",
        " 这是children1 传递过来的数据， 111111111"
      );
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
