
<template>
  <div :class="systemColor">
    <div class="app-bg">
      <link
        href="https://cdn.jsdelivr.net/npm/remixicon@2.5.0/fonts/remixicon.css"
        rel="stylesheet"
      />
      <div class="app">
        <div class="tit">临时笔记 - Temporary Notes</div>
        <div class="input-ground">
          <input
            type="text"
            v-model="message"
            @keyup.enter="btnAdd()"
            placeholder="请输入"
          />
          <div @click="btnAdd" class="btn-add">加一条</div>
        </div>
        <ul class="list">
          <li class="" v-for="(items, index) in listCon" :key="index">
            <div class="num-index">{{ index + 1 }}.</div>
            <div class="list-con">{{ items }}</div>
            <span @click="btnRem(index)">
              <i class="ri-close-line"></i>
            </span>
          </li>
        </ul>
        <div class="empty" v-if="listCon.length == 0">
          <div class="con">没有写</div>
        </div>
        <div class="ground3" v-if="listCon.length != 0">
          <span>笔记数量：{{ listCon.length }} 条</span>
          <div class="btn-clear" @click="clear()">全部删除</div>
        </div>
        <div class="changeColor">
          <div @click="changeColor01()">system</div>
          <div @click="changeColor02()">eva</div>
          <div @click="changeColor03()">builder</div>
        </div>
      </div>

      <div class="by">by mogo</div>
    </div>
  </div>
</template>


<script>
export default {
  head: {
    title: "临时笔记 - Temporary notes",
  },
  data() {
    return {
      systemColor: "system-mode",
      listCon: [
        "上面输入，可以创建一条条的笔记。",
        "是的，临时的，不会“保留”任何。",
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
    shuru() {
      alert("okokok");
    },
    changeColor01() {
      this.systemColor = "system-mode";
    },
    changeColor02() {
      this.systemColor = "eva-mode";
    },
    changeColor03() {
      this.systemColor = "builder-mode";
    },
  },
};
</script>


<style lang="less" scoped>
@import "~/assets/eva.less";
@import "~/assets/builder.less";

@max: (max-width: 768px);

body {
  background-color: #f1e7d0;
  color: #433422;
}

.system-mode {
  .app-bg {
    background-image: linear-gradient(180deg, #0b0c0d 47.49%, #20487c 147.49%);
    .app {
      .tit {
        color: #fff;
        &::after {
          content: " 🗄️";
        }
      }
    }
  }
}

.app-bg {
  // background-image: linear-gradient(180deg, #0b0c0d 47.49%, #20487c 147.49%);
  // background-image: @bbbggg1;
  height: 100vh;
  width: 100%;
  @media @max {
    height: 100%;
    min-height: 100vh;
  }
}

.app {
  width: 800px;
  margin: 0 auto;
  padding: 80px 0;
  @media @max {
    width: 90%;
    padding: 50px 0;
  }

  .tit {
    font-size: 3rem;
    text-align: center;
    font-weight: bolder;
    @media @max {
      font-size: 2rem;
    }
  }
}

.input-ground {
  display: flex;
  justify-content: space-between;
  margin: 40px auto;
  @media @max {
    flex-wrap: wrap;
  }
  input {
    width: 80%;
    background: #161e28;
    border: 1px solid #20487c00;
    border-radius: 20px;
    padding: 20px;
    font-size: 1rem;

    font-weight: 400;
    color: #fff;
    transition: all 300ms;
    @media @max {
      width: 100%;
    }
    &:focus {
      transition: all 300ms;
      outline: none;
      border: 1px solid #388eff;
    }
  }
  input::input-placeholder {
    color: #888;
  }
  input::-webkit-input-placeholder {
    //兼容WebKit browsers（Chrome的内核）
    color: #888;
  }
  input::-moz-placeholder {
    //Mozilla Firefox 4 to 18
    color: #888;
  }
  input::-moz-placeholder {
    //Mozilla Firefox 19+
    color: #888;
  }
  input::-ms-input-placeholder {
    //Internet Explorer 10+
    color: #888;
  }

  .btn-add {
    width: 18%;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all 300ms;
    background-color: #16202e;
    color: rgb(140, 167, 207);
    font-size: 1rem;
    border-radius: 20px;
    @media @max {
      width: 70%;
      padding: 1rem;
      margin: 1rem auto 0;
    }
    &:hover {
      background-color: #1d2c41;
      cursor: pointer;
      transition: all 300ms;
      color: #fff;
    }
  }
}

.list {
  padding: 0;
  width: 100%;
  li {
    background: rgba(22, 45, 71, 0.88);
    border: 1px solid #326197cc;
    border-radius: 20px;
    padding: 0.5rem;
    margin: 1rem 0;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: flex-start;
    color: #fff;
    &:nth-child(2n) {
      background: rgba(22, 53, 71, 0.88);
      border: 1px solid #296868cc;
    }

    .num-index {
      padding: 0.5rem 0;
      margin-left: 10px;
    }
    .list-con {
      padding: 0.5rem;
      width: 88%;
      text-align: justify;
      @media @max {
        width: 93%;
      }
    }

    span {
      padding: 8px 16px;
      color: #839dc755;
      font-size: 1.5rem;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 16px;
      @media @max {
        margin: 0 auto;
      }
      &:hover {
        background-color: #ffffff05;
        cursor: pointer;
        color: #fff;
      }
    }
  }
}

.empty {
  .con {
    color: #839dc755;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 2rem;
    font-weight: bold;
    border-radius: 20px;
    background-color: #161c2388;
    border: 2px dashed #20487c55;
    padding: 3rem 0;
    margin: 40px auto;
  }
}

.ground3 {
  display: flex;
  justify-content: space-between;
  align-items: center;
  span {
    color: #fff;
  }
  .btn-clear {
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all 300ms;
    padding: 0.5rem 1rem;
    background-color: #16202e;
    color: rgb(140, 167, 207);
    font-size: 1rem;
    border-radius: 20px;
    &:hover {
      background-color: red;
      cursor: pointer;
      transition: all 300ms;
      color: #fff;
    }
  }
}

.by {
  color: #fff;
  width: 100%;
  text-align: center;
  position: fixed;
  bottom: 12px;
  opacity: 0.1;
  @media @max {
    position: relative;
  }
}

.changeColor {
  display: flex;
  margin: 5rem auto 0;
  justify-content: center;

  div {
    padding: 1rem;
    margin: 0 1rem;

    border-radius: 8px;
    color: #ffffff11;
    transition: all 300ms;

    &:hover {
      color: #ffffff33;
      cursor: pointer;
      transition: all 300ms;
      background-color: #00000011;
    }
  }
}
</style>