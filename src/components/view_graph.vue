<!-- グラフを描く -->
<template>
  <canvas id="testCanvas" width="1000" height="500"/>
</template>

<script lang="ts">
import Chart from 'chart.js/auto';

export default {
  name: "view_graph",
  props: ["datas","dismode"],
  mounted(){
    var canvas = <HTMLCanvasElement> document.getElementById( "testCanvas" );
    if(canvas!=null){
      var context = <CanvasRenderingContext2D> canvas.getContext( "2d" );
      // データがないなら描かない
      if(this.datas.length>0){
        var chart_data: {labels: any[], datasets: any[]} = {labels:[], datasets:[]}
        console.log(chart_data)
        // 年度取得
        this.datas[0][1][this.dismode]["data"].forEach((row: { [x: string]: any[]; }) => {
          chart_data["labels"].push(row["year"]);
        });
        // データ取得
        this.datas.forEach((d: { [x: string]: any[]; }) => {
          let values: number[] = [];
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
}
</script>
