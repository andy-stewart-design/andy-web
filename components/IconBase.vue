<template>
  <div>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      :width="size"
      :height="size"
      :viewBox="viewBoxString"
      :aria-labelledby="iconName"
      role="presentation"
    >
      <title :id="iconName" lang="en">{{ iconName }} icon</title>
      <g :fill="iconColor">
        <slot />
      </g>
    </svg>
  </div>
</template>

<script>
export default {
  props: {
    iconName: {
      type: String,
      default: 'box',
    },
    viewbox: {
      type: [Number, String],
      default: 24,
    },
    size: {
      type: [Number, String],
      default: 24,
    },
    iconColor: {
      type: String,
      default: 'currentColor',
    },
  },
  computed: {
    viewBoxString() {
      return `0 0 ${this.viewbox} ${this.viewbox}`
    },
  },
}
</script>

<style></style>
