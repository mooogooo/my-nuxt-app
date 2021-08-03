<template>
  <div class="">
    <button @click="changeColor01()">111</button>
    <button @click="changeColor02()">222</button>
  </div>
</template>

<script>
export default {
  data() {
    return { systemColor: "system-mode" };
  },
  methods: {
    changeColor01() {
      this.systemColor = "system-mode";
    },
    changeColor02() {
      this.systemColor = "eva-mode";
    },
  },
};
</script>

]