<template lang="html">
  <div class="clearAllContainer">
    <span class="clearAllBtn" @click="clearTodo">Clear All</span>
  </div>
</template>

<script>
export default {
  methods: {
    clearTodo() {
      this.$emit('removeAll')
    }
  }
}
</script>

<style lang="css" scoped>
  .clearAllContainer {position: absolute; bottom:0; left:0; width:100%;}
  .clearAllContainer .clearAllBtn {display: block; line-height: 50px; background-color: #000; color: #fff; text-align: center;}
</style>
