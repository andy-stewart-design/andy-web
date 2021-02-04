<template>
  <svg class="eye" viewBox="0 0 36 30">
    <text transform="matrix(1 0 0 1 3.7566 7.9906)" class="eye-text">
      GRAPHIC
    </text>
    <text transform="matrix(1 0 0 1 6.4607 29.5329)" class="eye-text">
      DESIGN
    </text>
    <g>
      <defs>
        <path
          id="SVGID_1_"
          d="M36,15c0,0-6,12-18,12S0,15,0,15S6,3,18,3S36,15,36,15z"
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
      <circle class="st0 pupilX pupilY" cx="18" cy="15" r="1.5" />
      <circle class="st0 pupilX pupilY" cx="18" cy="15" r="3.5" />
      <circle class="st0 pupilX pupilY" cx="18" cy="15" r="5.5" />
      <circle class="st0 pupilX pupilY" cx="18" cy="15" r="7.5" />
      <circle class="st0 pupilX pupilY" cx="18" cy="15" r="9.5" />
      <circle class="st0 pupilX pupilY" cx="18" cy="15" r="11.5" />
      <circle class="st0 pupilX" cx="18" cy="15" r="13.5" />
      <circle class="st0 pupilX" cx="18" cy="15" r="15.5" />
      <circle class="st0 pupilX" cx="18" cy="15" r="17.5" />
    </g>
  </svg>
</template>

<style scoped lang="scss">
.eye {
  display: block;
  pointer-events: none;
  font-family: 'SohneSchmalTest-Fett';
  font-size: 10.5px;
  color: white;

  .st0 {
    clip-path: url(#SVGID_2_);
    fill: none;
    stroke: url(#SVGID_3_);
    stroke-width: 0.875;
    stroke-miterlimit: 10;
    opacity: 0.875;
  }

  .eye-text {
    font-family: 'SohneSchmalTest-Fett';
    font-size: 10.5px;
    text-transform: uppercase;
    fill: var(--white);
    opacity: 0.8;
  }
}
</style>
