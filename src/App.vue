<!-- 全体管理 -->
<template>
  <header>
    <todouhuken @upData="getDatas" @delData="delDatas"/>
    <display_mode_form @upDispmode="getDispmode"/>
  </header>
  <main>
    <view_graph :datas="datas" :dismode="display_mode" :key="resetKey"/>
  </main>
</template>

<script lang="ts">
import todouhuken from './components/todouhuken.vue'
import view_graph from './components/view_graph.vue'
import display_mode_form from './components/display_mode_form.vue'

export default {
  name: "App",
  components: {
    todouhuken,
    view_graph,
    display_mode_form
  },
  data(){
    return{
      datas: [],  // データ集合[ [ "県名", [各データ] ] ]
      resetKey: 0,  // view_graph更新キー
      display_mode: 0  // 表示するデータ（総人口とか）
    }
  },
  methods: {
    getDatas(data: any) {
      // console.log(data);
      var push_frag=true;
      this.datas.forEach(raw=>{
        // 同じのがないならpushしてよし
        if(raw[0]==data[0])
          push_frag=false;
      });
      if(push_frag)
        this.datas.push(data);
      this.resetKey++;
    },
    delDatas(code: number) {
      // console.log(code);
      var data_index=-1;
      for(let i=0;i<this.datas.length;i++){
        if(this.datas[i][0]==code)
        data_index=i;
      }
      // 該当データを抜いてるだけ
      if(data_index>=0)
        this.datas = this.datas.slice(0,data_index).concat(this.datas.slice(data_index+1,this.datas.length));
      this.resetKey++;
    },
    getDispmode(mode: number){
      // console.log(mode);
      this.display_mode=mode;
      this.resetKey++;
    }
  }
}
</script>

<style scoped>
header{
  margin:30px;
}
</style>
