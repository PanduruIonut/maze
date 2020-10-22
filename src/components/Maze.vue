<template>
  <div class="maze">
      <div v-for="cell in schema" :key="cell.index">
              <MazeCell></MazeCell>
          </div>
  </div>
</template>

<script>

import MazeCell from '@/components/MazeCell'

export default {
  name: 'Maze',
    components: {
      MazeCell,
  },
  props: [
    'schema',
  ],
setup(props) {
  const size = props.width * props.height;
 return {
      MazeCell,
      size,
    }
}
}

</script>
<style scoped lang="scss">
@import '@/style/maze.scss';
</style>
