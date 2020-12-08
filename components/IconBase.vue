<template>
  <div>
    <svg
      v-if="viewbox == 24"
      xmlns="http://www.w3.org/2000/svg"
      :width="size"
      :height="size"
      viewBox="0 0 24 24"
      :aria-labelledby="iconName"
      role="presentation"
    >
      <title :id="iconName" lang="en">{{ iconName }} icon</title>
      <g :fill="iconColor">
        <slot />
      </g>
    </svg>
    <svg
      v-else-if="viewbox == 32"
      xmlns="http://www.w3.org/2000/svg"
      :width="size"
      :height="size"
      viewBox="0 0 32 32"
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
}
</script>

<style></style>
