<template>
  <div id="app">
    <button @click="isShowList">优化前</button>
    <button>优化后</button>
    <list-dialog ref="listDialog"/>
  </div>
</template>

<script>
import ListDialog from './views/ListDialog.vue'
export default {
  name: 'App',
  components: {
    ListDialog,
  },
  methods: {
    isShowList(){
      this.$refs.listDialog.show = !this.$refs.listDialog.show 
    }
  }
}
</script>

