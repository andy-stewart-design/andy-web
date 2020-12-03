<template>
  <div>
    <nav-bar @toggle-modal="toggleModal" />
    <transition name="fade">
      <modal v-show="modalActive" @toggle-modal="toggleModal" />
    </transition>
    <Nuxt />
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import Modal from '@/components/Modal'

export default {
  components: {
    NavBar,
    Modal,
  },
  data() {
    return {
      modalActive: false,
    }
  },
  methods: {
    toggleModal() {
      this.modalActive = !this.modalActive
    },
  },
}
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
