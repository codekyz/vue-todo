<template>
  <div class="clearAllContainer">
    <span class="clearAllBtn" v-on:click="clearTodo">Clear All</span>
  </div>
</template>

<script>
export default {
  methods: {
    clearTodo() {
      this.$store.commit('clearAllItems');
    }
  }
}
</script>

<style scoped>

.clearAllContainer {
  width: 150px;
  height: 50px;
  line-height: 50px;
  background-color: #FFF;
  border-radius: 5px;
  margin: 0 auto;
}

.clearAllBtn {
  color: #e20303;
  display: block;
  cursor: pointer;
}

</style>