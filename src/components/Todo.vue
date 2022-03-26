<template>
  <div @mousemove="mouseMove" class="container">
    <p class="main_title">Vanilla Js DRAG & DROP TODO</p>
    <div class="todo_list_box">
      <div class="none box-detail">
        
        <div v-for="(item, index) in noneArr" v-bind:key="item">
          <div ref="itemBlock" v-on:drag="dragtest(index)" class="item" draggable="true">{{index}}, {{ noneArr[index] }}</div>
        </div>
        
        <div class="add-item">
          <input v-model="rawInput">
          <button @click="addTodo(rawInput)" class="commit">test</button>
        </div>
        
      </div>
      <div ref="itemBlock" v-on:drag="dragtest(index)" class="ready box-detail">

      </div>
      <div class="ongoing box-detail">
 
      </div>
      <div class="done box-detail">

      </div>
    </div>
  </div>
</template>

<script>

export default {
  setup(){
 
  },
  data() {
    return{
      noneArr: [],
      readyArr: [],
      ongoingArr: [],
      doneArr: [],
      rawInput: "",
    }
  },
  methods:{
    mouseMove(event) {
      console.log(event.clientX, event.clientY);
    },
    addTodo(rawInput){
      // rawInput !== "" ? console.log(rawInput) : alert("ㅁㄴㅇㄻㄴㅇ")
      if(rawInput !== "") {
        this.noneArr.push(rawInput)
        console.log(this.noneArr);
      }
    },
    dragtest(index){
      const el = this.$refs.itemBlock[index].getBoundingClientRect()
      console.log(index);
      console.log(el);
    }

  },
  watch:{
    
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .container{
    width: 100vw;
    height: 100vh;

    display: block;
  }

  .main_title{

    margin: 0 auto;

    font-size: 30px;
    font-weight: 700;

  }

  .todo_list_box{
    display: block;

    width: 1200px;
    height: 500px;

    display: flex;
    flex-direction: row;
    
    justify-content: space-around;
    align-items: center;

    background-color: rgb(163, 163, 163);
  }

  .box-detail{
    display: block;

    width: 250px;
    height: 400px;

    display: flex;
    flex-direction: column;

    align-items: center;

    background-color: rgb(197, 134, 134);
  }

  .item{
    display: block;

    width: 200px;
    height: 60px;

    margin-top: 30px;

    border-radius: 7px;
    background-color: rgb(158, 117, 117);

    cursor: move;
  }


  
</style>
