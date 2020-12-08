<template>
  <g>
    <polygon
      class="line-bot"
      points="26,24 5,24 4.5,23.5 5,23 26,23 26.5,23.5 	"
    />
    <polygon
      class="line-mid"
      points="26,16.5 5,16.5 4.5,16 5,15.5 26,15.5 26.5,16 	"
    />
    <polygon class="line-top" points="26,9 5,9 4.5,8.5 5,8 26,8 26.5,8.5 	" />
  </g>
</template>

<style scoped lang="scss">
div.trigger {
  .line-top,
  .line-mid,
  .line-bot {
    transition: transform 0.375s cubic-bezier(0.33, 1, 0.68, 1);
  }

  .line-top {
    transform-origin: 16px 8.5px;
  }

  .line-mid {
    transform-origin: 16px 16px;
  }

  .line-bot {
    transform-origin: 16px 23.5px;
  }

  &:hover {
    .line-top {
      transform: rotate(-45deg) translate3d(-6px, -6px, 0);
    }

    .line-mid {
      transform: scaleX(1.5);
    }

    .line-bot {
      transform: rotate(45deg) translate3d(-6px, 6px, 0);
    }
  }
}
</style>
