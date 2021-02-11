<template>
  <section ref="eye" class="hero" @mousemove="mouseMove">
    <svg class="eye" viewBox="0 0 36 24">
      <g>
        <defs>
          <path
            id="SVGID_1_"
            d="M36,12c0,0-6,12-18,12S0,12,0,12S6,0,18,0S36,12,36,12z"
          />
        </defs>
        <clipPath id="SVGID_2_">
          <use xlink:href="#SVGID_1_" style="overflow: visible" />
        </clipPath>
        <linearGradient
          id="SVGID_3_"
          gradientUnits="userSpaceOnUse"
          x1="5.2721"
          y1="-0.7279"
          x2="30.7279"
          y2="24.7279"
        >
          <stop offset="0" style="stop-color: #ff00ff" />
          <stop offset="1" style="stop-color: #0000ff" />
        </linearGradient>
        <circle class="st0 pupilX pupilY" cx="18" cy="12" r="1.5" />
        <circle class="st0 pupilX pupilY" cx="18" cy="12" r="3.5" />
        <circle class="st0 pupilX pupilY" cx="18" cy="12" r="5.5" />
        <circle class="st0 pupilX pupilY" cx="18" cy="12" r="7.5" />
        <circle class="st0 pupilX pupilY" cx="18" cy="12" r="9.5" />
        <circle class="st0 pupilX pupilY" cx="18" cy="12" r="11.5" />
        <circle class="st0 pupilX" cx="18" cy="12" r="13.5" />
        <circle class="st0 pupilX" cx="18" cy="12" r="15.5" />
        <circle class="st0 pupilX" cx="18" cy="12" r="17.5" />
      </g>
    </svg>
  </section>
</template>

<script>
export default {
  // eslint-disable-next-line
  props: ['positionX'],
  data() {
    return {
      hero: '',
      eye: '',
      posX: 0,
      posY: 0,
      midX: '',
      midY: '',
      maxX: 5,
      minX: '',
      maxY: 4,
      minY: '',
      clamp: '',
      mouseX: 0,
      mouseY: 0,
      clampX: 0,
      clampY: 0,
      ternX: 0,
      ternY: 0,
      log: '',
    }
  },
  mounted() {
    this.hero = this.heroSection
    this.eye = this.$refs.eye
    this.midX = window.innerWidth / 2
    this.midY = window.innerHeight / 2

    this.minX = this.maxX * -1
    this.minY = this.maxY * -1
    this.clamp = (num, min, max) => Math.min(Math.max(num, min), max)

    // this.hero.addEventListener('mousemove', this.mouseMove)
    // this.hero.addEventListener('mouseout', this.mouseOut)
  },
  methods: {
    moveBalls() {
      this.clampX = this.clamp(this.posX, this.minX, this.maxX)
      this.clampY = this.clamp(this.posY, this.minY, this.maxY)
      this.ternX = this.clampX >= 0 ? 0 : this.clampX
      this.ternY = this.clampY >= 0 ? 0 : this.clampY

      const tl = this.$gsap.timeline()

      tl.to(
        '.pupilX',
        {
          x: this.$gsap.utils.distribute({
            base: this.ternX,
            amount: this.clampX,
            from: 'end',
          }),
        },
        0
      ).to(
        '.pupilY',
        {
          y: this.$gsap.utils.distribute({
            base: this.ternY,
            amount: this.clampY,
            from: 'end',
          }),
        },
        0
      )
    },
    mouseMove(event) {
      // this.mouseX = event.clientX
      // this.mouseY = event.clientY
      // this.posX = (this.mouseX - this.midX) / 100
      // this.posY = (this.mouseY - this.midY) / 80

      // this.moveBalls()
      // eslint-disable-next-line
      console.log('eye: ' + this.positionX)
    },

    mouseOut() {
      this.posX = 0
      this.posY = 0

      this.moveBalls()
    },
  },
}
</script>

<style scoped lang="scss">
svg.eye {
  display: block;
  pointer-events: none;
  font-family: 'SohneSchmalTest-Fett';
  font-size: 10.5px;
  color: white;
  // border: 4px solid white;

  .st0 {
    clip-path: url(#SVGID_2_);
    fill: none;
    stroke: var(--blue);
    stroke-width: 0.875;
    stroke-miterlimit: 10;
  }
}
</style>
