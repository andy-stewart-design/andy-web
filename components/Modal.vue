<template>
  <div class="modal-container">
    <div class="overlay" @click="toggleModal"></div>
    <div class="modal">
      <p>Hello!</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  data() {
    return {
      showModal: true,
    }
  },
  methods: {
    toggleModal() {
      this.$emit('toggle-modal')
    },
  },
}
</script>

<style scoped lang="scss">
.modal-container {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100vw;
  height: 100vh;
  z-index: 1000000;

  .overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.85);
  }

  .modal {
    position: relative;
    background: white;
    padding: 2rem;
    color: black;
  }
}
</style>
