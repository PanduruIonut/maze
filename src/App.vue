<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <InputForm @submit="test">{{}}</InputForm>
  <Maze :schema="maze" :path="path"></Maze>
</template>

<script>
import InputForm from '@/components/InputForm'
import Maze from '@/components/Maze'
import 'core-js/es/array';


export default {
  name: 'App',
  components: {
    InputForm,
    Maze
  },
  data(){
    return{
    }
  },
  setup() {
    
    let width="8";
    let height="8";
    let start="0,0";
    let finish="7,7";
    let brickDensity="40";

    let schema = matrix(width,height,'0');
    let maze = generateBlocks(brickDensity, width,height,start.split(",")[0],start.split(",")[1],finish.split(",")[0],finish.split(",")[1],schema);
    console.log('maze',maze);
    let path = solveMaze(maze,0,0);
    console.log(path);
    // let maze;
    // let schema;
    // let path;

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

    function test(params){
      width = params.width,
      height = params.height,
      start = params.start,
      finish = params.end,
      brickDensity = params.BrickDensity
      
      schema = matrix(width,height,'0');

      console.log(schema);
      maze = generateBlocks(brickDensity, width,height,start.split(",")[0],start.split(",")[1],finish.split(",")[0],finish.split(",")[1],schema);
      console.log('maze',maze);
      const path = solveMaze(maze,0,0);
      console.log(path);
      return maze;
    }

    function generateBlocks(brickDensity, width,height, startx,starty, endx,endy, schema){
      console.log('blockDensity',brickDensity)
      console.log('width',width)
      console.log('height',height)
      console.log('startx',startx)
      console.log('starty',starty)
      console.log('endx',endx)
      console.log('endy',endy)
      console.log('schema',schema)
      schema[startx][starty]='s';
      schema[endx][endy]='f';
      var density = parseInt((brickDensity/width*height));
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
        let path = [];
        let found =0;
          function walk(column, row) {
              if(maze[column][row] == 'f') {
                  console.log("We solved the maze at (" + column + ", " + row + ")");
                  found = 1;
              } else if(maze[column][row] == '0') {
                if(found==1){
                  return;
                }
                  console.log("At valid position (" + column + ", " + row + ")");
                  path.push({column,row});
                  maze[column][row]='p';

                  // maze[column][row] = 9;
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
      if(found==1){
        console.log('break inner');
        break;
      }
      for(let j=starty;j<=i;j++)
      if(found==1){
        console.log('break inner');
        break;
      }else{
        walk(i,j)
      }
    }
    return maze;
  }

  return{
    maze,
    path,
    test,
    schema,
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
