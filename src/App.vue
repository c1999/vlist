<template>
  <div id="app">
    <button @click="isShowList">优化前</button>
    <button @click="visShowList">优化后</button>
    <list-dialog ref="listDialog"/>
    <v-list-dialog ref="vListDialog"/>
  </div>
</template>

<script>
import ListDialog from './views/ListDialog.vue'
import VListDialog from './views/VListDialog.vue'

export default {
  name: 'App',
  components: {
    ListDialog,
    VListDialog,
  },
  methods: {
    isShowList(){
      this.$refs.listDialog.show = !this.$refs.listDialog.show 
    },
    visShowList(){
      console.log('========');
      this.$refs.vListDialog.isShow = !this.$refs.vListDialog.isShow 
    }
  }
}
</script>

