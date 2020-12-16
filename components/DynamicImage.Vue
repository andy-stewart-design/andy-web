<template>
  <div>
    <p>My dynamic image below</p>
    <img :src="dynamicImage" />
  </div>
</template>

<script>
export default {
  name: 'DynamicImage',

  props: {
    filename: {
      type: String,
      required: true,
    },
  },

  computed: {
    dynamicImage() {
      return require(`~/assets/${this.filename}`)
    },
  },
}
</script>
