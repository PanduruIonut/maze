<template>
  <p class="Enter form data"></p>
  <ul>
  <div>
<input type="input" id="Width" placeholder="Width"  v-model="Width" ref="Width">
<input type="input" id="Height" placeholder="Height" v-model="Height" ref="Height">
</div>
<div>
<div class="element">
<input type="input" id="Start" placeholder="Start" v-model="Start" ref="Start">
</div>
<div class="element">
  <input type="input" id="End" placeholder="End" v-model="End" ref="End">
  </div>
 <div class="element">
<input type="input" id="Brick density"  placeholder="Brick density" v-model="BrickDensity" ref="BrickDensity">
</div>
</div>
<button class="create-button" @click="submitForm">Create maze</button>
  </ul>
</template>

<script>
export default {
  name: 'InputForm',
  data() {  
    return{
      Width:'',
      Height:'',
      Start:'',
      End:'',
      BrickDensity:'',
    }
  },
  methods: {
    submitForm() {
      this.$emit('submit', { 
        width: this.Width,
        height: this.Height,
        start: this.Start,
        end: this.End,
        BrickDensity: this.BrickDensity,
      })
  },
}
}
</script>
<style scoped lang="scss">
@import '@/style/_input-form.scss';
</style>
