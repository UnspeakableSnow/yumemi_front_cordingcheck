<script setup lang="ts">
// defineProps<{
//   data: object
// }>()

</script>

<template>
  <canvas id="testCanvas" width="550" height="450"/>
</template>

<script lang="ts">
mounted:()=>{
  var canvas = document.getElementById( "testCanvas" );
var context = canvas.getContext( "2d" );  
   
// declare graph start and end  
var GRAPH_TOP = 25;  
var GRAPH_BOTTOM = 375;  
var GRAPH_LEFT = 25;  
var GRAPH_RIGHT = 475;   
   
var GRAPH_HEIGHT = 350;   
var GRAPH_WIDTH = 450;  
   
// clear canvas (if another graph was previously drawn)  
context.clearRect( 0, 0, 500, 400 );   
   
// draw X and Y axis  
context.beginPath();  
context.moveTo( GRAPH_LEFT, GRAPH_BOTTOM );  
context.lineTo( GRAPH_RIGHT, GRAPH_BOTTOM );  
context.lineTo( GRAPH_RIGHT, GRAPH_TOP );  
context.stroke();  
   
// draw reference line at the top of the graph  
context.beginPath();   
// set light grey color for reference lines  
context.strokeStyle = "#BBB";  
context.moveTo( GRAPH_LEFT, GRAPH_TOP );  
context.lineTo( GRAPH_RIGHT, GRAPH_TOP );  
context.stroke();  
   
// draw reference line 3/4 up from the bottom of the graph  
context.beginPath();  
context.moveTo( GRAPH_LEFT, ( GRAPH_HEIGHT ) / 4 * 3 + GRAPH_TOP );  
context.lineTo( GRAPH_RIGHT, ( GRAPH_HEIGHT ) / 4 * 3 + GRAPH_TOP );  
context.stroke();  
   
// draw reference line 1/2 way up the graph  
context.beginPath();  
context.moveTo( GRAPH_LEFT, ( GRAPH_HEIGHT ) / 2 + GRAPH_TOP );  
context.lineTo( GRAPH_RIGHT, ( GRAPH_HEIGHT ) / 2 + GRAPH_TOP );  
context.stroke();  
   
// draw reference line 1/4 up from the bottom of the graph  
context.beginPath();  
context.moveTo( GRAPH_LEFT, ( GRAPH_HEIGHT ) / 4 + GRAPH_TOP );  
context.lineTo( GRAPH_RIGHT, ( GRAPH_HEIGHT ) / 4 + GRAPH_TOP );  
context.stroke();
}
</script>