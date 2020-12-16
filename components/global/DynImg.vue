<template>
  <div>
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
      return require(`~/assets/img/blog/${this.filename}`)
    },
  },
}
</script>
