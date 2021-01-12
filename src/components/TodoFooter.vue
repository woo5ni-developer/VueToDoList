<template>
    <div class="clearAllContainer">
        <span class="clearAllBtn" v-on:click="clearTodo">Clear All</span>
    </div>
</template>
<script>
export default {
  methods: {
    clearTodo: function() {
      this.$emit('removeAllItem');
    }
  }
}
</script>
<style scoped>
  .clearAllContainer {
    width: 135px;
    height: 50px;
    display: flex;
    align-items: center;
    background-color: #fff;
    border-radius: 5px;
    margin: 0 auto;
    justify-content: center;
  }
  .clearAllBtn {
    color: #e20303;
    display: block;
  }
</style>