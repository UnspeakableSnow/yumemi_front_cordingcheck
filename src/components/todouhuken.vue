<template>
  <h1>都道府県を選択</h1>
  <div id="buttons"></div>
</template>

<script lang="ts">
var headers = new Headers();
headers.set("X-API-KEY", "tHo6JXy8vlNO6dBUCtXp3hgcTqN19CQXpot93nCa");
headers.set("Accept", "application/json");
headers.set("Content-Type", "application/json;charset=utf-8");

// window.addEventListener('DOMContentLoaded', function() {
export default {
  name: "todouhuken",
  data(){
    return{
      todouhukens: []
    }
  },
  mounted(){
    this.get_todouhuken_itiran();
  },
  methods: {
    get_todouhuken_data(id: number){
      fetch(`https://opendata.resas-portal.go.jp/api/v1/population/composition/perYear?prefCode=${id}`, {headers})
        .then(response => response.json())
        .then(data => {
          // console.log(data["result"]["data"]);
          this.$emit('upData', [this.todouhukens[id-1], data["result"]["data"]]);
        })
        .catch(error => console.error('Error:', error));
    },
    get_todouhuken_itiran(){
      fetch('https://opendata.resas-portal.go.jp/api/v1/prefectures', {headers})
      .then(response => response.json())
      .then(json_data => {
        json_data = json_data["result"];
        json_data.forEach((data: { [x: string]: string; }) => {
          this.todouhukens.push(data["prefName"]);

          let button_box = document.createElement("div");
          button_box.setAttribute("class","button_box")
          document.getElementById("buttons").appendChild(button_box);
          
          let button = document.createElement("input");
          button.setAttribute("type","checkbox");
          button.setAttribute("value",String(data["prefCode"]));
          let button_label = document.createElement("label");
          button_label.innerHTML = data["prefName"];
          button_box.appendChild(button);
          button_box.appendChild(button_label);

          button.addEventListener("change",()=>{
            if(button.checked){
              this.get_todouhuken_data(Number(button.value))
            }
            else{
            }
          })
        });
      })
      .catch(error => console.error('Error:', error));}
  },
}
</script>

<style scoped>
h1 {
  font-size: 2.6rem;
}
#buttons{
  /* display: flex; */
  border:3px solid #000;
}
.button_box{
  display: inline;
  border:1px solid #00f;
}
</style>
