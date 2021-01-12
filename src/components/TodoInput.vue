<template>
  <div class='inputBox shadow'>
    <input type="text" v-model='newTodoItem' v-on:keyup.enter='addTodo'>
    <span class='addContainer' @click='addTodo'>
      <svg class="bi bi-plus-square-fill addBtn" width="1em" height="1em" viewBox="0 0 16 16" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd" d="M2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2H2zm6.5 4a.5.5 0 0 0-1 0v3.5H4a.5.5 0 0 0 0 1h3.5V12a.5.5 0 0 0 1 0V8.5H12a.5.5 0 0 0 0-1H8.5V4z"/>
      </svg>
    </span>
    <ModalComponent v-if="showModal" @close="showModal = false">
      <div slot="header">Warning</div>
      <div slot='body'>입력된 값이 없습니다.</div>
    </ModalComponent>
  </div>
</template>
<script>
import ModalComponent from './util/ModalComponent.vue'
export default {
    data(){
      return {
        newTodoItem : '',
        showModal:false
      }
    },
    methods: {
      addTodo : function(){
        // console.log(this.newTodoItem)
        //Todo : 저장하는 로직
        if(this.newTodoItem !== ''){
          this.$emit('addTodoItem', this.newTodoItem)
          this.clearInput();
        }else{
          this.showModal = !this.showModal
        }
      },
      clearInput : function(){
        this.newTodoItem = '';
      }
    },
    components : {
      ModalComponent
    }
}
</script>
<style scoped>
  input:focus {
    outline: none;
  }
  .inputBox {
    width: 500px;
    height: 50px;
    border-radius: 5px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    background: #fff;
  }
  .inputBox input {
    border-style: none;
    font-size: 15px;
    width:90%;
    padding: 0 10px;
  }
  .addContainer {
    background: linear-gradient(to right, #6478FB, #8763FB);
    width: 50px;
    border-radius: 0 5px 5px 0;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .addBtn {
    color: #fff;
    vertical-align: middle;
  }
</style>