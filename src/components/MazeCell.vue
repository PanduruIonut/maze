<template>
<div class="cell" :class="getStyle(type)">
</div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'MazeCell',
  props: {
    type:String
  },
  methods:{
    getStyle(type){
      if(type=='s'){
        return `cell--start`;
      }
      else if(type=='f'){
        return `cell--finish`;
      }
      else if(type=='B'){
        return 'cell--block'
      }
      else if(type=='p'){
        return 'cell--path'
      }
      return '0';
    },
  },
});
</script>
<style scoped lang="scss">
@import '@/style/_maze-cell.scss';
</style>
