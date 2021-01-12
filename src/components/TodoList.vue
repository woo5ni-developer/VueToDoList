<template>
    <div>
        <transition-group name="list" tag="ul">
            <li v-for='(todoItem, index) in propsdata' v-bind:key='todoItem' class="shadow">
                {{ todoItem }} 
                <span class='removeBtn' v-on:click="removeTodo(todoItem, index)">
                    <svg class="bi bi-trash" width="1em" height="1em" viewBox="0 0 16 16" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
                        <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/>
                        <path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4L4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/>
                    </svg>
                </span>
            </li>
        </transition-group>
    </div>
</template>
<script>
export default {
    props : ['propsdata'],
    methods: {
      removeTodo: function(todoItem, index) {
        this.$emit('removeItem', todoItem, index);
      },
    }
}
</script>
<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  align-items: center;
  min-height: 50px;
  width: 500px;
  margin: 20px auto 0;
  padding: 15px 55px 15px 15px;
  background: #fff;
  border-radius: 5px;
  position: relative;
  box-sizing: border-box;
}
.removeBtn {
  position: absolute;
  right: 20px;
  color: #de4343;
}

.list-enter-active, .list-leave-active {
  transition: all .5s;
}
.list-enter, .list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>