<template>
  <div id="app">
    <todo-header/>
    <todo-input v-on:addTodoItem='addOneItem'/>
    <todo-list v-bind:propsdata='todoItems' v-on:removeItem='removeOneItem'/>
    <todo-footer v-on:removeAllItem='clearAllItem'/>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  name: 'App',
  components: {
    TodoHeader, TodoInput, TodoList, TodoFooter
  },
  data(){
    return {
        todoItems : []
    }
  },
  methods:{
    addOneItem : function(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeOneItem : function(todoItem, index){
      // console.log(todoItem, index);
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    clearAllItem : function(){
      localStorage.clear(); 
      this.todoItems = [];
    }
  },
  created() {
    if(localStorage.length > 0){
      for(let i = 0 ; i < localStorage.length ; i++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
            this.todoItems.push(localStorage.key(i))
        }
        // console.log(localStorage.key(i))
      }
    }
  },
}
</script>

<style>
  body {
    text-align:center;
    background-color: #F6F6F6;
  }
  input{
    border-style: groove;
    width: 200px;
  }
  button {
    border-style: groove;
  }

  .shadow{
    box-shadow: 5px 10px 20px rgba(0,0,0,0.03);
  }
</style>
