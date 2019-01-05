<template>
  <div id="app">
    <div class="home-container">
      <img class="home-chef" src="./assets/luigi.png" alt="Luigi">
      <button id="show-modal" @click="showModal = true">Rate our service!</button>
      <div>{{ averageRatings }}</div>
    </div>
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
        food: [4, 4],
        delivery: [5, 3],
        overall: [4, 3]
      }
    };
  },
  methods: {
    updateRatings: function(newRatings) {
      console.log("new ratings", newRatings);
      this.ratings.food.push(parseInt(newRatings.food));
      this.ratings.delivery.push(parseInt(newRatings.delivery));
      this.ratings.overall.push(parseInt(newRatings.overall));
    }
  },
  computed: {
    averageRatings: function() {
      const avgs = [];
      Object.values(this.ratings).forEach(value => {
        const sum = value.reduce(function(a, b) {
          return a + b;
        });
        const avg = sum / value.length;
        avgs.push(avg.toFixed(2));
      });
      return {
        food: avgs[0],
        delivery: avgs[1],
        overall: avgs[2]
      };
    }
  }
};
</script>

<style lang="scss">
.home-container {
  margin: auto;
  padding: 40px;
  text-align: center;
  .home-chef {
    display: block;
    margin: auto;
    padding: 30px;
  }
  #show-modal {
    background: #ce3079;
    color: #fff;
    font-size: 16px;
    border: 0;
    border-radius: 4px;
    padding: 10px 20px;
    transition: all 0.5s ease;
    &:hover {
      transform: scale(1.1);
      background: darken($color: #ce3079, $amount: 10);
    }
    &:focus {
      outline: 0;
    }
  }
}
</style>
