<template>
  <div
    ref="hero"
    class="hero-container"
    @mousemove="mouseMove"
    @mouseleave="mouseOut"
  >
    <div class="eye-container">
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
    </div>
    <div class="grid-container">
      <h1 class="hero-head">
        Andy Stewart is a graphic designer working at the intersection of brand
        and technology. He is currently the digital creative director at
        Turnstyle.
      </h1>
      <h1 class="hero-head">&copy;&nbsp;{{ date }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: 'The Graphic Design Portfolio of Andy Stewart',
      descr:
        'Andy Stewart is the Digital Creative Director at Turnstyle in Seattle',
      date: '',
      hero: '',
      eye: '',
      posX: 0,
      posY: 0,
      midX: 0,
      midY: 0,
      maxX: 5,
      minX: 0,
      maxY: 4,
      minY: 0,
      clamp: 0,
      mouseX: 0,
      mouseY: 0,
      clampX: 0,
      clampY: 0,
      ternX: 0,
      ternY: 0,
    }
  },
  mounted() {
    this.eye = this.$refs.hero
    this.midX = window.innerWidth / 2
    this.midY = window.innerHeight / 2

    this.minX = this.maxX * -1
    this.minY = this.maxY * -1
    this.clamp = (num, min, max) => Math.min(Math.max(num, min), max)

    const today = new Date()
    const hours = today.getHours()
    const normHours = hours >= 13 ? hours - 12 : hours
    const mins = today.getMinutes()
    const normMins = mins <= 9 ? '0' + mins : mins
    const date =
      today.getMonth() + 1 + '.' + today.getDate() + '.' + today.getFullYear()
    const time = normHours + ':' + normMins
    this.date = date + ' ' + time
    this.intro = this.$refs.intro
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
      this.mouseX = event.clientX
      this.mouseY = event.clientY
      this.posX = (this.mouseX - this.midX) / 100
      this.posY = (this.mouseY - this.midY) / 80

      this.moveBalls()
    },
    mouseOut() {
      this.posX = 0
      this.posY = 0

      this.moveBalls()
    },
  },
  head() {
    return {
      title: this.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.descr,
        },
      ],
    }
  },
}
</script>

<style scoped lang="scss">
@use '@/assets/_base/mixins';

.hero-container {
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  position: relative;
  width: 100vw;
  height: 100vh;
  min-height: 440px;

  .eye-container {
    @include mixins.flex-center;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;

    svg.eye {
      display: block;
      pointer-events: none;
      width: 95%;
      height: 90%;

      @include mixins.respond(md) {
        width: 80%;
      }

      .st0 {
        clip-path: url(#SVGID_2_);
        fill: none;
        stroke: var(--blue);
        stroke-width: 0.875;
        stroke-miterlimit: 10;
      }
    }
  }

  div.grid-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 100%;
    min-height: 100%;
    padding: calc(var(--type-baseline) * 7) 0.5rem var(--type-baseline);

    @include mixins.respond(md) {
      padding: var(--type-baseline) 4.25rem;
    }

    .hero-head {
      position: relative;
      width: 100%;
      max-width: 840px;
      padding: 0 0.5rem;
      font-family: var(--sans-book);
      font-size: var(--text-2xl);
      line-height: calc(var(--type-baseline) * 4.5);
      font-variant-numeric: tabular-nums;

      @include mixins.respond(md) {
        padding: 0 0.75rem;
      }
    }
  }
}
</style>
