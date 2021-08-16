<template>
  <div v-show="show" class="vListContainer">
    <ul class="listItem">
      <li v-for="(item, index) in arrMsg" :key="index" class="listItem">
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ListDialog",
  data() {
    return {
      show: false,
      arrMsg: [],
    };
  },
  mounted() {
    for (let index = 0; index < 100000; index++) {
      this.arrMsg.push(index);
    }
  },
};
</script>
<style scoped>
* {
  margin: 0;
  padding: 0;
}
.vListContainer {
  width: 500px;
  height: 1000px;
  background: #f5f6f8;
  overflow-y: auto;
}
.listItem {
  width: 100%;
  height: 100px;
  background: #fff;
  border: 1px solid bisque;
  text-align: center;
  line-height: 100px;
}
</style>