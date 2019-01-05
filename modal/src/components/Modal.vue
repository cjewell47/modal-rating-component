<template>
  <transition name="modal-fade">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <h2>How did we do?</h2>
          </div>

          <div class="modal-body">
            <p>Please let us know how our food delvery was. It will really help us to keep improving our service.</p>
            <div class="modal-rating-wrapper">
              <h4>How would your rate your food?</h4>
              <div class="modal-rating-stars">
                <button
                  class="modal-rating-stars"
                  data-type="food"
                  data-index="1"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="food"
                  data-index="2"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="food"
                  data-index="3"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="food"
                  data-index="4"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="food"
                  data-index="5"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
              </div>
            </div>
            <div class="modal-rating-wrapper">
              <h4>How would your rate your delivery driver?</h4>
              <div class="modal-rating-stars">
                <button
                  class="modal-rating-stars"
                  data-type="delivery"
                  data-index="1"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="delivery"
                  data-index="2"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="delivery"
                  data-index="3"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="delivery"
                  data-index="4"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="delivery"
                  data-index="5"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
              </div>
            </div>
            <div class="modal-rating-wrapper">
              <h4>How would your rate your overall experience?</h4>
              <div class="modal-rating-stars">
                <button
                  class="modal-rating-stars"
                  data-type="overall"
                  data-index="1"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="overall"
                  data-index="2"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="overall"
                  data-index="3"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="overall"
                  data-index="4"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
                <button
                  class="modal-rating-stars"
                  data-type="overall"
                  data-index="5"
                  @click="starClick"
                  @mouseover="starEnter"
                  @mouseleave="starLeave"
                ></button>
              </div>
            </div>
            <p
              class="modal-rating-submit-message"
              v-if="submitted"
            >Thank you for submitting these ratings</p>
            <p
              class="modal-rating-zero-message"
              v-if="zeroRating"
            >You have left some ratings as 0. Click submit again to confirm these ratings</p>
          </div>
          <button v-if="!submitted" class="modal-submit-button" @click="submitClick">Submit Feedback</button>
          
          <button class="modal-close-button" @click="$emit('close')">
            <img src="../assets/close.svg" alt="close-icon">
          </button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "modal",
  data() {
    return {
      ratings: {
        food: 0,
        delivery: 0,
        overall: 0
      },
      zeroRating: false,
      submitted: false,
      zeroErrorOnce: false
    };
  },
  methods: {
    starClick: function(e) {
      const category = e.target.getAttribute("data-type");
      const rating = e.target.getAttribute("data-index");
      console.log(category, rating);
      this.ratings[category] = rating;
      const selected = Array.from(
        document.querySelectorAll(
          '.modal-rating-stars[data-type="' + category + '"]'
        )
      );
      selected.forEach((star, index) => {
        if (index < rating) {
          star.classList.add("selected");
        } else {
          star.classList.remove("selected");
        }
      });
    },
    starEnter: function(e) {
      const category = e.target.getAttribute("data-type");
      const rating = e.target.getAttribute("data-index");
      const selected = Array.from(
        document.querySelectorAll(
          '.modal-rating-stars[data-type="' + category + '"]'
        )
      );
      selected.forEach((star, index) => {
        if (index < rating) {
          star.classList.add("star-hover");
        }
      });
    },
    starLeave: function(e) {
      const category = e.target.getAttribute("data-type");
      const rating = e.target.getAttribute("data-index");
      const selected = Array.from(
        document.querySelectorAll(
          '.modal-rating-stars[data-type="' + category + '"]'
        )
      );
      selected.forEach(star => {
        star.classList.remove("star-hover");
      });
    },
    submitClick: function() {
      if (
        (this.ratings.food === 0 ||
          this.ratings.delivery === 0 ||
          this.ratings.overall === 0) &&
        !this.zeroErrorOnce
      ) {
        this.zeroRating = true;
        this.zeroErrorOnce = true;
      } else {
        this.zeroRating = false;
        this.submitted = true;
        this.$emit("submitRatings", this.ratings);
      }
    }
  }
};
</script>

<style lang="scss">
button {
  &:hover {
    cursor: pointer;
  }
}
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  max-width: 300px;
  position: relative;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  font-family: Helvetica, Arial, sans-serif;
  text-align: center;
}

.modal-header h3 {
  margin-top: 0;
  color: #000;
}

.modal-body {
  margin: 20px 0;
  .modal-rating-stars {
    display: flex;
    justify-content: center;
    button {
      background: transparent;
      border: 0;
      padding: 0;
      margin: 1px 3px;
      height: 20px;
      width: 20px;
      position: relative;
      background-image: url("../assets/star.svg");
      background-size: cover;
      transition: all 0.4s ease;
      &:hover {
        transform: scale(1.2);
      }
      &.selected {
        background-image: url("../assets/star-gold.svg");
      }
      &.star-hover {
        background-image: url("../assets/star-gold.svg");
      }
      &:focus {
        outline: 0;
      }
    }
  }
  .modal-rating-zero-message {
    color: red;
  }
}

.modal-submit-button {
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

.modal-close-button {
  float: right;
  background: transparent;
  border: 0;
  transition: all 0.4s ease;
  position: absolute;
  top: -8px;
  right: -12px;
  &:hover {
    transform: scale(1.2);
  }
  &:focus {
    outline: none;
  }
  img {
    height: 25px;
  }
}

.modal-fade-enter,
.modal-fade-leave-active {
  opacity: 0;
}

.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.5s ease;
}

@media screen and (max-width: 425px) {
  .modal-container {
    width: 240px;
  }
}
</style>
