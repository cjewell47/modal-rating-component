<template>
  <div id="app">
    <button id="show-modal" @click="showModal = true">Rate our service!</button>
    <modal v-if="showModal" @close="showModal = false">
    </modal>
  </div>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: "app",
  components: {
    'modal': Modal
  },
  data() {
    return {
      showModal: false
    }
  }
};
</script>

<style lang="scss">

</style>
