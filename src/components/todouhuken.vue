<!-- 都道府県入力フォーム -->
<template>
  <h1>都道府県を選択</h1>
  <!-- buttonsは複数あることが異常なのでidでいいと思っている -->
  <div id="buttons"></div>
</template>

<script lang="ts">
// APIキーなど共通ヘッダ
var headers = new Headers();
// APIキーが使われ放題？んなもんくれてやらぁ！
headers.set("X-API-KEY", "tHo6JXy8vlNO6dBUCtXp3hgcTqN19CQXpot93nCa");
headers.set("Accept", "application/json");
headers.set("Content-Type", "application/json;charset=utf-8");

var todouhukens: { [x: string]: any; } = [];
export default {
  name: "todouhuken",
  emits: ['upData', 'delData'],
  mounted(){
    this.get_todouhuken_itiran();
  },
  methods: {
    // 都道府県コードに対応した人口構成データを持ってきて送る
    get_todouhuken_data(code: number){
      fetch(`https://opendata.resas-portal.go.jp/api/v1/population/composition/perYear?prefCode=${code}`, {headers})
        .then(response => response.json())
        .then(data => {
          this.$emit('upData', [todouhukens[code-1], data["result"]["data"]]);
        })
        .catch(error => console.error('Error:', error));
    },
    // 都道府県と都道府県コードを持ってきてフォームを作る
    get_todouhuken_itiran(){
      fetch('https://opendata.resas-portal.go.jp/api/v1/prefectures', {headers})
      .then(response => response.json())
      .then(json_data => {
        var buttons = <HTMLCanvasElement> document.getElementById("buttons");
        json_data = json_data["result"];
        json_data.forEach((data: { [x: string]: string; }) => {
          todouhukens.push(data["prefName"]);

          let button_box = document.createElement("div");
          button_box.setAttribute("class","button_box");
          buttons.appendChild(button_box);
          
          let button_label = document.createElement("label");
          button_label.innerHTML = data["prefName"];
          let button = document.createElement("input");
          button.setAttribute("type","checkbox");
          button.setAttribute("value",String(data["prefCode"]));
          button_box.appendChild(button_label);
          button_label.appendChild(button);

          button.addEventListener("change",()=>{
            if(button.checked){
              this.get_todouhuken_data(Number(button.value))
            }
            else{
              // 除外をApp.vueに送る
              this.$emit('delData', todouhukens[Number(button.value)-1]);
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
  padding-left: 5px;
  border-left: solid 10px #747;
  border-top: solid 10px #7470;
  border-bottom: double 10px #747;
  border-right: solid 10px #7470;
}
#buttons{
  padding:5px;
  display: flex;
  flex-wrap: wrap;
  border:3px dotted #0007;
}
@media (max-width: 450px) {
  h1{
    font-size:1.5em;
  }
  label{
    font-size: 8px;
  }
}
</style>
