<!-- グラフを描く -->
<template>
  <canvas id="testCanvas" width="1000" height="500"/>
</template>

<script lang="ts">
import "https://cdn.jsdelivr.net/npm/chart.js";

export default {
  name: "view_graph",
  props: ["datas","dismode"],
  mounted(){
    var canvas = document.getElementById( "testCanvas" );
    var context = canvas.getContext( "2d" );
    // データがないなら描かない
    if(this.datas.length>0){
      var chart_data= {labels:[], datasets:[]}
      // 年度取得
      this.datas[0][1][this.dismode]["data"].forEach((row: { [x: string]: any; }) => {
        chart_data["labels"].push(row["year"]);
      });
      // データ取得
      this.datas.forEach((d: { [x: string]: any[]; }) => {
        let values= [];
        d[1][this.dismode]["data"].forEach((row: { [x: string]: number; }) => {
          values.push(row["value"]);
        });
        chart_data["datasets"].push({label:d[0],data:values});
      });
      // かきかき
      new Chart(context, {
        type: 'line',
        data: chart_data,
      });
    }
  }
}
</script>
