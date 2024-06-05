<!-- 表示状態（総人口、年少人口など）切り替えフォーム -->
<template>
  <form id="display_mode_form">
    <label><input type="radio" name="display_mode" value="0" checked>総人口</label>
    <label><input type="radio" name="display_mode" value="1">年少人口</label>
    <label><input type="radio" name="display_mode" value="2">生産年齢人口</label>
    <label><input type="radio" name="display_mode" value="3">老年人口</label>
  </form>
</template>

<script lang="ts">

export default {
  name: "display_mode_form",
  emits: ['upDispmode'],
  mounted(){
    var display_mode_form = <HTMLInputElement> document.getElementById("display_mode_form");
    var display_mode_buttons = <NodeListOf<HTMLInputElement>> document.getElementsByName("display_mode");
    // ラジオボタンの値を送信
    display_mode_form.addEventListener("change",()=>{
      for (let i=0; i<display_mode_buttons.length; i++){
        if (display_mode_buttons[i].checked){
          this.$emit('upDispmode', display_mode_buttons[i].value);
        }
      }
    })
  }
}
</script>

<style>
#display_mode_form{
  padding:5px;
  display: flex;
  flex-wrap: wrap;
}
</style>
