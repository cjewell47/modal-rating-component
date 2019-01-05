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
                <button data-index="1"></button>
                <button data-index="2"></button>
                <button data-index="3"></button>
                <button data-index="4"></button>
                <button data-index="5"></button>
              </div>
            </div>
            <div class="modal-rating-wrapper">
              <h4>How would your rate your delivery driver?</h4>
              <div class="modal-rating-stars">
                <button data-index="1"></button>
                <button data-index="2"></button>
                <button data-index="3"></button>
                <button data-index="4"></button>
                <button data-index="5"></button>
              </div>
            </div>
            <div class="modal-rating-wrapper">
              <h4>How would your rate your overall experience?</h4>
              <div class="modal-rating-stars">
                <button data-index="1"></button>
                <button data-index="2"></button>
                <button data-index="3"></button>
                <button data-index="4"></button>
                <button data-index="5"></button>
              </div>
            </div>
          </div>

          <button class="modal-default-button" @click="$emit('close')">
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
      // greyStar: 'star.svg',
      // goldStar: 'star-gold.svg'
    };
  }
};
</script>

<style lang="scss">
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
  width: 300px;
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
      margin: 1px 7px;
      height: 20px;
      width: 20px;
      position: relative;
      &::before {
        content: "";
        display: inline-block;
        background-image: url("../assets/star.svg");
        background-size: cover;
        position: absolute;
        top: 0;
        left: 0;
        height: 20px;
        width: 20px;
      }
      &:hover {
        cursor: pointer;
        &::before {
          background-image: url("../assets/star-gold.svg");
        }
      }
    }
  }
}

.modal-default-button {
  float: right;
  background: transparent;
  border: 0;
  transition: all 0.4s ease;
  position: absolute;
  top: -8px;
  right: -12px;
  &:hover {
    cursor: pointer;
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
</style>
