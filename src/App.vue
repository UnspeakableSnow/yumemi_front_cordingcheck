<template>
  <header>
    <todouhuken @upData="getDatas"/>
  </header>
  <main>
    <view_graph :datas="datas" :key="resetKey"/>
  </main>
</template>

<script lang="ts">
import todouhuken from './components/todouhuken.vue'
import view_graph from './components/view_graph.vue'

export default {
  name: "App",
  components: {
    todouhuken,
    view_graph
  },
  data(){
    return{
      datas: [],
      resetKey: 0
    }
  },
  methods: {
    getDatas(data: any) {
      this.datas.push(data);
      this.resetKey++;
    }
  }
}
</script>

<style scoped>
header{
  margin:auto;
}
</style>
