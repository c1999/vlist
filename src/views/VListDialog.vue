<template>
    <div class="list-wrap" ref="listWrap" @scroll="scrollListener" v-show="isShow">
      <div class="scroll-bar" ref="scrollBar"></div>
      <ul class="list" ref="list">
        <li v-for="(val, index) in showList" :key="index" class="listItem">{{ val }}</li>
      </ul>
    </div>
</template>

<script>
export default {
  name: "VListDialog",
  data() {
    return {
      list: [], //超长的显示数据
      itemHeight: 100, //每一列的高度
      showNum: 10, //显示几条数据
      start: 0, //滚动过程显示的开始索引
      end: 10, //滚动过程显示的结束索引
      isShow: false
    };
  },
  computed: {
    //显示的数组，用计算属性计算
    showList() {
      return this.list.slice(this.start, this.end);
    },
  },
  mounted() {
    //构造一个超长列表
    for (let i = 0; i < 1000000; i++) {
      this.list.push(i);
    }
    //计算滚动容器高度
    this.$refs.listWrap.style.height = this.itemHeight * this.showNum + "px";
    //计算总的数据需要的高度，构造滚动条高度
    this.$refs.scrollBar.style.height =
      this.itemHeight * this.list.length + "px";
  },
  methods: {
    scrollListener() {
      //获取滚动高度
      let scrollTop = this.$refs.listWrap.scrollTop;
      //开始的数组索引
      this.start = Math.floor(scrollTop / this.itemHeight);
      //结束索引
      this.end = this.start + this.showNum;
      //绝对定位对相对定位的偏移量
      this.$refs.list.style.top = this.start * this.itemHeight + "px";
    },
  },
};
</script>
<style scoped>
* {
  margin: 0;
  padding: 0;
}
.list-wrap {
  position: relative;
  overflow-y: auto;
  width: 500px;
  box-sizing: border-box;
}
.list {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
}
.listItem {
  border: 1px solid bisque;
  text-align: center;
  line-height: 100px;
  width: 100%;
}
.scroll-bar {
    background: goldenrod;
}
</style>