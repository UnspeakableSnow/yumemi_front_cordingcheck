<template>
  <canvas id="testCanvas" width="700" height="650"/>
</template>

<script lang="ts">
import "https://cdn.jsdelivr.net/npm/chart.js";

export default {
  name: "view_graph",
  props: ["datas"],
  mounted(){
    var canvas = document.getElementById( "testCanvas" );
    var context = canvas.getContext( "2d" );
    if(this.datas.length>0){
      var chart_data= {labels:[], datasets:[]}
      // 年度取得
      this.datas[0][1][0]["data"].forEach((row: { [x: string]: any; }) => {
        chart_data["labels"].push(row["year"]);
      });
      // データ取得
      this.datas.forEach((d: { [x: string]: any[]; }) => {
        let values= [];
        console.log(values);
        d[1][0]["data"].forEach((row: { [x: string]: number; }) => {
          values.push(row["value"]);
        });
        chart_data["datasets"].push({label:d[0],data:values});
      });
      new Chart(context, {
        type: 'line',
        data: chart_data,
      });
    }

  }
}
</script>