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
    return {};
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
