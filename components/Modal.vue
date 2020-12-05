<template>
  <transition name="fade">
    <div class="modal-container">
      <div class="overlay" @click="toggleModal"></div>
      <div class="modal">
        <div class="close-container">
          <div class="icon-close" @click="toggleModal"></div>
        </div>
        <p>Hello!</p>
      </div>
    </div>
  </transition>
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
    background-color: var(--black);
    opacity: 0.85;
  }

  .modal {
    position: absolute;
    top: 0;
    right: 0;
    height: 100vh;
    width: 100%;
    max-width: 360px;
    padding: 1.75rem;
    background: var(--white);
    color: var(--black);

    .close-container {
      width: 100%;

      .icon-close {
        width: 1.5rem;
        height: 1.5rem;
        background: var(--black);
        margin-left: auto;
        cursor: pointer;
      }
    }
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s cubic-bezier(0.22, 1, 0.36, 1);
  transition-delay: 0;

  .modal {
    transform: translate3d(0%, 0, 0);
  }
}

.fade-enter-to,
.fade-leave {
  .modal {
    transition: transform 0.5s cubic-bezier(0.33, 1, 0.68, 1);
    transition-delay: 0.5s;
  }
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
  transition: opacity 0.5s;
  transition-delay: 0.5s;

  .modal {
    transform: translate3d(100%, 0, 0);
    transition: transform 0.5s cubic-bezier(0.32, 0, 0.67, 0);
    transition-delay: 0s;
  }
}
</style>
