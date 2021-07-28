
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
          <img src="/close-line.svg" width="20px" alt="" />
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
      listCon: [
        "这里可以创建备忘录，",
        "是的，是临时的，刷新就没，不保留和窃取你的数据",
      ],
      message: "",
    };
  },
  methods: {
    btnAdd() {
      if (this.message != "") {
        this.listCon.push(this.message);
        this.message = "";
      } else {
        alert("还未填写任务内容");
      }
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