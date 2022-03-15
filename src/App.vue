<template>
  <h1>My Vue App</h1>
  <p>
    Welcome...
  </p>
  <button @click="toggleModal">Show normal modal</button>
  <button @click="toggleModal2">Show sale modal</button>
  <teleport to=".modals" v-if="showModal">
    <Modal @close="toggleModal">
      <h2>{{ modalHeader }}</h2>
      <p>{{ modalText }}</p>
      <template v-slot:links>
        <a href="#">more info</a>
        <a href="#">sing in</a>
      </template>
    </Modal>
  </teleport>
  <teleport to=".modals" v-if="showModal2">
    <Modal theme="sale" @close="toggleModal2">
      <h2>{{ modalHeader }}</h2>
      <p>{{ modalText }}</p>
      <template v-slot:links>
        <a href="#">more info</a>
        <a href="#">sing in</a>
      </template>
    </Modal>
  </teleport>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Modal
  },
  data(){
    return {
      modalHeader: "This is a header",
      modalText: "This is my Modal Text",
      modalClass: "gray rounded",
      showModal: false,
      showModal2: false
    }
  },
  methods:{
    toggleModal(){
      this.showModal = !this.showModal
    },
    toggleModal2(){
      this.showModal2 = !this.showModal2
    }
  }
}
</script>

<style>
#app {
  color: #2c3e50;
  margin-top: 60px;
}
</style>
