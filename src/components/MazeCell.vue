<template>
<div class="cell">
</div>
</template>

<script>
export default {
  name: 'MazeCell',
  props: {
    isBlock:Boolean
  }
}
</script>
<style scoped lang="scss">
@import '@/style/_maze-cell.scss';
</style>
