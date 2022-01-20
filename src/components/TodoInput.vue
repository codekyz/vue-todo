<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
        <i class="fas fa-plus addBtn"></i>
    </span>


    <Modal v-if="showModal" @close="showModal = false">
      <template v-slot:header>
        <h3>
          경고!
        </h3>
      </template>

      <template v-slot:body>
        아무것도 입력하지 않으셨습니다.
        <i class="closeModalBtn fas fa-times" v-on:click="showModal = false"></i>
      </template>
      
    </Modal>
  </div>
</template>

<script>

import Modal from './common/Modal.vue'

export default {
  data: function() {
      return {
        newTodoItem: '',
        showModal: false
      }
  },
  methods: {
      addTodo: function() {
        if(this.newTodoItem !== '') {
          this.$emit('addTodoItem', this.newTodoItem);
          this.clearInput();
        } else {
          this.showModal = !this.showModal;
        }
      },
      clearInput: function() {
        this.newTodoItem = '';
      }
  },

  components: {
    Modal,
  }
}
</script>

<style scoped>

input:focus {
    outline: none;
}
.inputBox {
    background-color: #FFF;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
}

.inputBox input {
    border-style: none;
    font-size: 16px;
}

.addContainer {
    float: right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display: block;
    width: 55px;
    border-radius: 0 5px 5px 0;
}

.addBtn {
    color: #FFF;
    vertical-align: middle;
}

.closeModalBtn {
  color: #34b983;

}

</style>