<template>
  <div class="maze">
      <div v-for="rows in schema" :key="rows.index">
          <div v-for="cell in rows" :key="cell.index">
              <MazeCell :type="cell"></MazeCell>
          </div>
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
    'path',
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
