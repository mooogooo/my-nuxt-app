<template>
  <div class="app">
    <div class="top"><h1>数据大屏</h1></div>
    <div class="flex-con">
      <div class="team">
        <ul>
          <li>1</li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
        </ul>
      </div>
      <div class="team">
        <ul>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style lang="less" scoped>
h1 {
  text-align: center;
  color: cyan;
}
.flex-con {
  display: flex;
  justify-content: space-between;
}

.team {
  ul {
    list-style: none;
    li {
      font-size: 1rem;
      margin-left: -2.5rem;
      width: 220px;
      height: 80px;
 background: rgba(32,189,202,0.33);
border: 1px solid #00FFC6;
      margin-bottom: 32px;
      border-radius: 1rem;
    }
  }
}
</style>