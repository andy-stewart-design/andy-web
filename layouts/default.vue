<template>
  <div>
    <nav-bar @toggle-modal="toggleModal" />
    <modal v-show="modalActive" @toggle-modal="toggleModal" />
    <Nuxt />
    <!-- <grid /> -->
  </div>
</template>

<script>
export default {
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
