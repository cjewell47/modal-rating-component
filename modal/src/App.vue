<template>
  <div id="app">
    <button id="show-modal" @click="showModal = true">Rate our service!</button>
    <div>{{ ratings.food }}</div>
    <div>{{ ratings.delivery }}</div>
    <div>{{ ratings.overall }}</div>
    <modal v-if="showModal" @close="showModal = false" @submitRatings="updateRatings($event)"></modal>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "app",
  components: {
    modal: Modal
  },
  data() {
    return {
      showModal: false,
      ratings: {
        food: [4,4],
        delivery: [5,3],
        overall: [4,3]
      }
    };
  },
  methods: {
    updateRatings: function(newRatings) {
      console.log('new ratings', newRatings);
      this.ratings.food.push(parseInt(newRatings.food))
      this.ratings.delivery.push(parseInt(newRatings.delivery))
      this.ratings.overall.push(parseInt(newRatings.overall))
    }
  }
};
</script>

<style lang="scss">
</style>
