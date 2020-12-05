<template>
  <div>
    <nav-bar @toggle-modal="toggleModal" />
    <modal v-show="modalActive" @toggle-modal="toggleModal" />
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

<style lang="scss"></style>
