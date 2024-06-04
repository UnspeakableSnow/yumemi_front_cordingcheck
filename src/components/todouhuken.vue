<script setup lang="ts">
</script>

<template>
  <h1>都道府県を選択</h1>
  <div id="bottoms"></div>
</template>

<script lang="ts">
var headers = new Headers();
headers.set("X-API-KEY", "tHo6JXy8vlNO6dBUCtXp3hgcTqN19CQXpot93nCa")
headers.set("Accept", "application/json")
headers.set("Content-Type", "application/json;charset=utf-8")

function get_todouhuken_data(id: number){
  fetch('https://opendata.resas-portal.go.jp/api/v1/population/composition/perYear?prefCode=11', {headers})
    .then(response => response.json())
    .then(data => console.log(data["result"]))
    .catch(error => console.error('Error:', error));
  return id;
}

// window.addEventListener('DOMContentLoaded', function() {
mounted:()=>{
  fetch('https://opendata.resas-portal.go.jp/api/v1/prefectures', {headers})
  .then(response => response.json())
  .then(json_data => {
    json_data = json_data["result"];
    json_data.forEach(data => {
      console.log(data);
      let bottom_box = document.createElement("div");
      bottom_box.setAttribute("class","bottom_box")
      document.getElementById("bottoms").appendChild(bottom_box);
      
      let bottom = document.createElement("input");
      bottom.setAttribute("type","checkbox");
      bottom.setAttribute("value",String(data["prefCode"]));
      let bottom_label = document.createElement("label");
      bottom_label.innerHTML = data["prefName"];
      bottom_box.appendChild(bottom);
      bottom_box.appendChild(bottom_label);

      bottom.addEventListener("change",()=>{
        if(bottom.checked){}
        console.log(bottom.value)
      })
    });
  })
  .catch(error => console.error('Error:', error));
}
</script>

<style scoped>
h1 {
  font-size: 2.6rem;
}
#bottoms{
  /* display: flex; */
  border:3px solid #000;
}
.bottom_box{
  display: flex;
  border:1px solid #00f;
}
</style>
