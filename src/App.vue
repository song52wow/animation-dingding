<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { onMounted, ref } from "vue";

gsap.registerPlugin(ScrollTrigger);

const scrollRef = ref();
const companyRef = ref();
const mainRef = ref();

onMounted(() => {
  gsap
    .timeline({
      scrollTrigger: {
        trigger: scrollRef.value,
        markers: true,
        start: "top top",
        end: "+=120%",
        scrub: true,
      },
    })
    .from(companyRef.value, {
      scale: 0.01,
      opacity: 0.3,
    })
    .to(companyRef.value, {
      scale: 1,
      opacity: 1,
    })
    .to(companyRef.ref, {
      scale: 1.3,
      opacity: 0,
    });

  // ScrollTrigger.create({
  //   trigger: mainRef.value,
  //   pin: true,
  // });
});
</script>

<template>
  <div ref="scrollRef" class="scroll">
    <section class="banner"></section>
    <section ref="mainRef" class="main">
      <div ref="companyRef" class="company">
        <div class="logo">
          <img
            src="https://gw.alicdn.com/imgextra/i2/O1CN01kEuOaQ1OQe6INmAUY_!!6000000001700-55-tps-180-180.svg"
          />
        </div>
        <div class="name">
          <img
            src="https://gw.alicdn.com/imgextra/i2/O1CN01ymd4z41U5vtsYSFZF_!!6000000002467-55-tps-397-52.svg"
          />
        </div>
      </div>
      <div class="base-bg">
        <div v-for="i in 21" :key="i"></div>
      </div>
    </section>
  </div>
  <section class="footer"></section>
</template>

<style lang="scss" scoped>
@use 'sass:list';
@use 'sass:map';

$baseStyle: (
  1: (
    width: 1.6em,
    height: 1.6em,
    radius: 0.3333em,
    left: calc(50% - 7.56em),
    top: calc(50% - 4.21em),
    bg: (
      linear-gradient(-33deg, #8f35ff, rgba(143, 53, 255, 0)),
      radial-gradient(
        circle at 62% -28%,
        rgba(0, 45, 156, 0.75) 0,
        #002d9c 68%,
        rgba(0, 45, 156, 0) 111%
      ),
      linear-gradient(
        116deg,
        rgba(0, 137, 255, 0.2) 1%,
        rgba(0, 186, 255, 0.04) 38%,
        rgba(68, 149, 255, 0.08) 68%,
        rgba(3, 79, 255, 0.16) 88%
      ),
    ),
  ),
  2: (
    width: 0.8em,
    height: 0.8em,
    radius: 0.1667em,
    left: calc(50% - 4.87em),
    top: calc(50% - 1.92em),
    bg: (
      linear-gradient(133deg, rgba(255, 186, 0, 0), rgba(255, 207, 0, 0.6) 68%),
      linear-gradient(170deg, #ffc400, #ff9200),
      linear-gradient(170deg, #ffc400, #ff9200),
    ),
  ),
  3: (
    width: 0.96em,
    height: 0.96em,
    radius: 0.2em,
    left: calc(50% - 6.24em),
    top: calc(50% - 1.41em),
    bg: #cc7201,
  ),
  4: (
    width: 0.4em,
    height: 0.4em,
    radius: 0.0833em,
    left: calc(50% - 3.16em),
    top: calc(50% - 0.67em),
    bg: linear-gradient(170deg, #3e9eff, #0062ff),
  ),
  5: (
    width: 0.46em,
    height: 0.46em,
    radius: 0.0958em,
    left: calc(50% - 2.59em),
    top: calc(50% - 0.28em),
    bg: none,
  ),
  6: (
    width: 0.72em,
    height: 0.72em,
    radius: 0.15em,
    left: calc(50% - 5.79em),
    bottom: calc(50% - 1.75em),
    bg: linear-gradient(46deg, #ff5f00, #ff8d16),
  ),
  7: (
    width: 1.6em,
    height: 1.6em,
    radius: 0.3333em,
    left: calc(50% - 7.01em),
    bottom: calc(50% - 4.12em),
    bg: (
      linear-gradient(220deg, #e58dff, #8f35ff 67%, rgba(143, 53, 255, 0)),
      radial-gradient(
        circle at 1.2222% -87%,
        rgba(0, 45, 156, 0.75) 0,
        #002d9c 171%,
        rgba(0, 45, 156, 0) 278%
      ),
      linear-gradient(137deg, rgba(0, 137, 255, 0.3), rgba(3, 79, 255, 0.24)),
    ),
  ),
  8: (
    width: 0.24em,
    height: 0.24em,
    radius: 0.05em,
    left: calc(50% - 2.43em),
    top: calc(50% - 0.03em),
    bg: (
      linear-gradient(220deg, #e58dff, #8f35ff 67%, rgba(143, 53, 255, 0)),
      radial-gradient(
        circle at 1.2222% -87%,
        rgba(0, 45, 156, 0.75) 0,
        #002d9c 171%,
        rgba(0, 45, 156, 0) 278%
      ),
      linear-gradient(137deg, rgba(0, 137, 255, 0.3), rgba(3, 79, 255, 0.24)),
    ),
  ),
  9: (
    width: 0.96em,
    height: 0.96em,
    radius: 0.2em,
    left: calc(50% - 1.54em),
    top: calc(50% - 4.73em),
    bg: (
      linear-gradient(-27deg, rgba(143, 53, 255, 0.8) 11%, rgba(143, 53, 255, 0)),
      radial-gradient(
        circle at 62% -28%,
        rgba(0, 45, 156, 0.75) 0,
        #002d9c 68%,
        rgba(0, 45, 156, 0) 111%
      ),
    ),
  ),
  10: (
    width: 0.46em,
    height: 0.46em,
    radius: 0.0958em,
    left: calc(50% - 3.62em),
    bottom: calc(50% - 0.98em),
    bg: (
      #ffa800,
    ),
  ),
  11: (
    width: 64px,
    height: 64px,
    radius: 13.33px,
    right: calc(50% - 1.02em),
    top: calc(50% - 3.95em),
    bg: (
      -webkit-radial-gradient(top, rgba(0, 45, 156, 0.75) 0, #002d9c 92%, rgba(
              0,
              45,
              156,
              0
            )
            166%),
    ),
  ),
  12: (
    width: 0.24em,
    height: 0.24em,
    radius: 0.05em,
    right: calc(50% - 0.38em),
    top: calc(50% - 2.06em),
    bg: (
      linear-gradient(147deg, #004fff, #002d9c 82%),
      linear-gradient(153deg, #007fff 5%, #0063ff 95%),
    ),
  ),
  13: (
    width: 1.3em,
    height: 1.3em,
    radius: 0.2708em,
    right: calc(50% - 7.04em),
    top: calc(50% - 3.63em),
    bg: (
      linear-gradient(39deg, rgba(0, 79, 255, 0), #004fff 72%),
      linear-gradient(153deg, #007fff 5%, #0063ff 95%),
    ),
  ),
  14: (
    width: 0.64em,
    height: 0.64em,
    radius: 0.1333em,
    right: calc(50% - 5.05em),
    top: calc(50% - 2.26em),
    bg: (
      linear-gradient(128deg, #00ebb6, #00ba46 69%),
    ),
  ),
  15: (
    width: 0.24em,
    height: 0.24em,
    radius: 0.05em,
    right: calc(50% - 2.18em),
    top: calc(50% - 0.52em),
    bg: (
      linear-gradient(170deg, #ffc400, rgba(255, 207, 0, 0.6)),
    ),
  ),
  16: (
    width: 0.24em,
    height: 0.24em,
    radius: 0.05em,
    right: calc(50% - 2.18em),
    top: calc(50% - 0.52em),
    bg: (
      linear-gradient(170deg, #ffc400, rgba(255, 207, 0, 0.6)),
    ),
  ),
  17: (
    width: 0.24em,
    height: 0.24em,
    radius: 0.05em,
    right: calc(50% - 3em),
    bottom: calc(50% - 0.49em),
    bg: (
      linear-gradient(170deg, #00b6ff, #007fff),
    ),
  ),
  18: (
    width: 0.64em,
    height: 0.64em,
    radius: 0.1333em,
    right: calc(50% - 4.53em),
    bottom: calc(50% - 1.7em),
    bg: (
      linear-gradient(148deg, #76d2ff, #09baff 99%),
    ),
  ),
  19: (
    width: 0.96em,
    height: 0.96em,
    radius: 0.2em,
    right: calc(50% - 6.57em),
    bottom: calc(50% - 1.33em),
    bg: (
      linear-gradient(136deg, #3e9eff 19%, #0062ff),
    ),
  ),
  20: (
    width: 1.6em,
    height: 1.6em,
    radius: 0.3333em,
    right: calc(50% - 8em),
    bottom: calc(50% - 3.45em),
    bg: (
      linear-gradient(147deg, rgba(0, 79, 255, 0.6), rgba(0, 45, 156, 0.6) 82%),
      linear-gradient(153deg, #007fff 5%, #0063ff 95%),
    ),
  ),
  21: (
    width: 0.96em,
    height: 0.96em,
    radius: 0.2em,
    right: calc(50% - 2.13em),
    bottom: calc(50% - 5.32em),
    bg: (
      linear-gradient(-2deg, rgba(0, 45, 156, 0.75), #002d9c),
    ),
  ),
);

@mixin baseCss($key) {
  $style: map.get($baseStyle, $key);

  background: map.get($style, "bg");
  border-radius: map.get($style, "radius");
  width: map.get($style, "width");
  height: map.get($style, "height");
  @if map.get($style, "top") {
    top: map.get($style, "top");
  }
  @if map.get($style, "left") {
    left: map.get($style, "left");
  }
  @if map.get($style, "bottom") {
    bottom: map.get($style, "bottom");
  }
  @if map.get($style, "right") {
    right: map.get($style, "right");
  }
}

.scroll {
  overflow: hidden;
}

.banner {
  height: 900px;
}

.main {
  height: 200vh;
  background-color: #040506;
  position: relative;
  font-size: 100px;

  .company {
    text-align: center;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    .name {
      margin-top: 100px;
    }
  }

  .base-bg {
    width: 100%;
    height: 100vh;
    position: absolute;

    > div {
      position: absolute;

      @each $key, $value in $baseStyle {
        &:nth-child(#{$key}) {
          @include baseCss($key);
        }
      }
    }
  }
}
</style>

<style>
* {
  margin: 0;
  padding: 0;
}
</style>
