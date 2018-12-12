<template>
  <div class="calculator">
    <div class="display"> Display </div>
    <div> C </div>
    <div> +/- </div>
    <div> % </div>
    <div> ÷ </div>
    <div> Hello </div>
    <div> Hello </div>
    <div> Hello </div>
    <div> Hello </div>
    <div> Hello </div>
    <div> Hello </div>
    <div> Hello </div>
    <div> Hello </div>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.calculator {
  font-size: 20pt;
  display: grid;
  grid-template-columns: repeat(4, 1fr); 
  grid-auto-rows: minmax(50px, auto); 
}
.display {
  grid-column: 1 / 5;
  background-color: red;
  text-align: center;
}
</style>
