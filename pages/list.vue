
<template>
  <div class="app">
    <input
      type="text"
      v-model="message"
      @keyup.enter="btnAdd()"
      placeholder="请输入"
    />
    <button @click="btnAdd">提交数据</button>
    <ul>
      <li class="rounded" v-for="(items, index) in listCon" :key="index">
        {{ index + 1 }}. {{ items }}
        <span @click="btnRem(index)">
          <Icon type="md-close" size="20" />
        </span>
      </li>
    </ul>
    <div class="" v-if="listCon.length == 0">
      <h1>还未添加任务</h1>
    </div>
    <div class="ground3">
      <span>任务数量：{{ listCon.length }} 个</span>
      <button @click="clear()" v-if="listCon.length != 0">全部删除</button>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      listCon: ["hahaha", "hehe"],
      message: "",
    };
  },
  methods: {
    btnAdd() {
      this.listCon.push(this.message);
      this.message = "";
    },
    clear() {
      this.listCon = [];
    },
    btnRem(index) {
      this.listCon.splice(index, 1);
    },
  },
};
</script>


<style lang="less" scoped>
.app {
  width: 800px;
  margin: 0 auto;
}

ul {
  list-style: none;
  li {
    background: #eee;
    padding: 0.3rem 1rem;
    margin: 1rem 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    span {
      padding: 1rem;

      &:hover {
        background-color: #aaa;
        cursor: pointer;
      }
    }
  }
}

.groud3 {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>