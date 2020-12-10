<template>
  <g class="close-container">
    <polygon
      class="bl-tr"
      points="4.9,19.9 4.1,19.1 11.7,11.6 19.1,4.1 19.9,4.9 		"
    />
    <polygon
      class="tl-br"
      points="19.1,19.9 4.1,4.9 4.9,4.1 10.4,9.7 19.9,19.1 		"
    />
  </g>
</template>

<style scoped lang="scss">
div.trigger {
  .close-container {
    --transition: transform 0.5s cubic-bezier(0.33, 1, 0.68, 1);

    transition: var(--transition);
    transform-origin: 12px 12px;

    .bl-tr,
    .tl-br {
      fill: currentColor;
      transform-origin: 12px 12px;
      transition: var(--transition);
    }
  }

  &:hover {
    .close-container {
      transform: rotate(90deg);

      .bl-tr {
        transform: rotate(135deg);
      }
      .tl-br {
        transform: rotate(45deg);
      }
    }
  }
}
</style>
