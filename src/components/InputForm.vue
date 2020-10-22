<template>
  <p class="Enter form data"></p>
  <ul>
  <div>
<label for="Width">Width</label>
<input type="input" id="Width"  v-model="checkedNames">
<label for="Height">Height</label>
<input type="input" id="Height"  v-model="checkedNames">
</div>
<div>
<div class="element">
<label for="Start">Start</label>
<input type="input" id="Start"  v-model="checkedNames">
</div>
<div class="element">
<label for="End">End</label>
  <input type="input" id="End" v-model="checkedNames">
  </div>
 <div class="element">
<label for="Brick density">Brick density</label>
<input type="input" id="Brick density"  v-model="checkedNames">
</div>
</div>
<button>Create maze</button>
  </ul>
</template>

<script>
export default {
  name: 'InputForm',
  props: {
    width: Number,
    height: Number,
    start: Number,
    end: Number,
    brickDensity: Number
  }
}
</script>
<style scoped lang="scss">
@import '@/style/_input-form.scss';
</style>
