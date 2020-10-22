<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <InputForm/>
  <Maze :schema="maze"></Maze>
</template>

<script>
import InputForm from '@/components/InputForm'
import Maze from '@/components/Maze'


export default {
  name: 'App',
  components: {
    InputForm,
    Maze
  },
  setup() {
    const schema = matrix(8,8,'0');
    const maze = generateBlocks(4, 8,8,0,0,0,4,schema);
    console.log('maze',maze);
    solveMaze(maze,0,0);

    function matrix( rows, cols, defaultValue){
      var arr = [];
      for(var i=0; i < rows; i++){
          arr.push([]);
          arr[i].push( new Array(cols));
          for(var j=0; j < cols; j++){
            arr[i][j] = defaultValue;
          }
      }

    return arr;
    }

    function generateBlocks(blockDensity, width,height, startx,starty, endx,endy, schema){
      schema[startx][starty]='s';
      schema[endx][endy]='f';
      var density = parseInt((blockDensity/width*height));
      console.log(density);
      while(density!= 0){
        let posx = parseInt(Math.random()*width);
        let posy = parseInt(Math.random()*height);
        if(posx != startx &&posy!=startx  && posx!= endx && posy!=endy && schema[posx][posy] !='B')
        schema[posx][posy] = 'B'
        density--;
      }
      return schema;
    }

      function solveMaze(maze, startx,starty) {

          function walk(column, row) {
              if(maze[column][row] == 'f') {
                  console.log("We solved the maze at (" + column + ", " + row + ")");
              } else if(maze[column][row] == '0') {
                  console.log("At valid position (" + column + ", " + row + ")");
                  maze[column][row] = 9;
              if(column < maze.length - 1) {
                  walk(column + 1, row);
              }
              if(row < maze[column].length - 1) {
                  walk(column, row + 1);
              }
              if(column > 0) {
                  walk(column - 1, row);
              }
              if(row > 0) {
                  walk(column, row - 1);
              }
          }
      }
    for(let i=startx;i<maze.length;i++){
      for(let j=starty;j<=maze.length;j++)
      walk(i,j)
    }
  }
      return{
      maze,
    }
}
}



</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
