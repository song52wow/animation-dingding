<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { computed, onMounted, ref } from "vue";

gsap.registerPlugin(ScrollTrigger);

const scrollRef = ref();
const companyRef = ref();
const bannerRef = ref();
const mainRef = ref();
const companyAnimation = ref({
  logoScale: 0,
  titleScale: 0,
  scale: 0,
  yPercent: 0,
  opacity: 0,
  logoOpacity: 1,
  titleOpacity: 1,
});
const boxAnimation = ref({
  z: -200,
});
const listAnimation = ref({
  scale: 0,
  opacity: 0,
});

const listItemAnimation = ref([{
  scale: 0,
  opacity: 0,
},{
  scale: 0,
  opacity: 0,
},{
  scale: 0,
  opacity: 0,
},{
  scale: 0,
  opacity: 0,
}]);

const listImage = [
  "https://img.alicdn.com/imgextra/i3/O1CN01TVWH501KYCEaUxPgv_!!6000000001175-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i1/O1CN01vqBxIP1L5d98G9xJD_!!6000000001248-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i3/O1CN01AKJU3T1tSi2NAFHFP_!!6000000005901-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i1/O1CN01E0GR9h1ZXwFI8dRl1_!!6000000003205-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i1/O1CN01sphiAp1Fj7bOKEppz_!!6000000000522-2-tps-480-480.png",
  "https://img.alicdn.com/imgextra/i2/O1CN015T9BdZ28Ns5n1A82W_!!6000000007921-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i3/O1CN01bc6FKX1OCuHkDC2J7_!!6000000001670-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i1/O1CN01Y936lS1whluhvos2E_!!6000000006340-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i3/O1CN017Wk2Cp1lp8VaSd22U_!!6000000004867-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i4/O1CN016JIoXg1lMHYbmErdR_!!6000000004804-0-tps-240-240.jpg",
  "https://img.alicdn.com/imgextra/i3/O1CN011GyvMe1of0bAveV4u_!!6000000005251-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i2/O1CN01zFSNcP26wYrM09A4S_!!6000000007726-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i2/O1CN0142F9wc23s261dItxf_!!6000000007310-0-tps-480-480.jpg",
  "https://img.alicdn.com/imgextra/i4/O1CN012wi8vZ1xt3HbO0ttd_!!6000000006500-0-tps-480-480.jpg",
];

const listDoc = [
  "即时沟通",
  "组织",
  "智能人事",
  "组织大脑",
  "OA审批",
  "邮箱",
  "Teambition",
  "文档",
  "音视频会议",
  "开放平台",
  "宜搭",
  "钉闪会",
  "连接器",
  "酷应用",
];

const listStyle = computed(() => [
  {
    scale: listItemAnimation.value[3]["scale"],
    opacity: listItemAnimation.value[3]["opacity"],
    transformOrigin: 'right bottom'
  },
  {
    scale: listItemAnimation.value[2]["scale"],
    opacity: listItemAnimation.value[2]["opacity"],
    transformOrigin: 'right bottom'
  },
  {
    scale: listItemAnimation.value[1]["scale"],
    opacity: listItemAnimation.value[1]["opacity"],
    transformOrigin: 'right bottom'
  },
  {
    scale: listItemAnimation.value[0]["scale"],
    opacity: listItemAnimation.value[0]["opacity"],
    transformOrigin: 'bottom'
  },
  {
    scale: listItemAnimation.value[1]["scale"],
    opacity: listItemAnimation.value[1]["opacity"],
    transformOrigin: 'left bottom'
  },
  {
    scale: listItemAnimation.value[2]["scale"],
    opacity: listItemAnimation.value[2]["opacity"],
    transformOrigin: 'left bottom'
  },
  {
    scale: listItemAnimation.value[3]["scale"],
    opacity: listItemAnimation.value[3]["opacity"],
    transformOrigin: 'left bottom'
  },
  {
    scale: listItemAnimation.value[3]["scale"],
    opacity: listItemAnimation.value[3]["opacity"],
    transformOrigin: 'right top'
  },
  {
    scale: listItemAnimation.value[2]["scale"],
    opacity: listItemAnimation.value[2]["opacity"],
    transformOrigin: 'right top'
  },
  {
    scale: listItemAnimation.value[1]["scale"],
    opacity: listItemAnimation.value[1]["opacity"],
    transformOrigin: 'right top'
  },
  {
    scale: listItemAnimation.value[0]["scale"],
    opacity: listItemAnimation.value[0]["opacity"],
    transformOrigin: 'top'
  },
  {
    scale: listItemAnimation.value[1]["scale"],
    opacity: listItemAnimation.value[1]["opacity"],
    transformOrigin: 'left top'
  },
  {
    scale: listItemAnimation.value[2]["scale"],
    opacity: listItemAnimation.value[2]["opacity"],
    transformOrigin: 'left top'
  },
  {
    scale: listItemAnimation.value[3]["scale"],
    opacity: listItemAnimation.value[3]["opacity"],
    transformOrigin: 'left top'
  },
]);

const scrollTl = gsap
  .timeline()
  .addLabel("scroll")
  // .to(
  //   companyAnimation.value,
  //   {
  //     titleScale: 2,
  //     logoScale: 1.5,
  //     scale: 2
  //   },
  //   "scroll"
  // )
  .to(
    boxAnimation.value,
    {
      z: 800,
    },
    "scroll"
  );

const bannerStartTl = gsap.timeline().fromTo(
  companyAnimation.value,
  {
    opacity: 0,
    scale: 0,
  },
  {
    opacity: 1,
    scale: 1,
  }
);

const mainStartTl = gsap
  .timeline()
  .addLabel("main")
  .fromTo(
    companyAnimation.value,
    {
      scale: 1,
    },
    {
      scale: 2,
    },
    "main"
  )
  .to(
    companyAnimation.value,
    {
      yPercent: -100,
    },
    "main"
  )
  .to(
    companyAnimation.value,
    {
      logoOpacity: 0,
      duration: 0.1,
    },
    "main+=30%"
  )
  .to(
    companyAnimation.value,
    {
      titleOpacity: 0,
      duration: 0.1,
    },
    "main+=100%"
  )
  .to(
    listAnimation.value,
    {
      opacity: 1,
      scale: 1,
    },
    "main+=50%"
  )
  .to(
    listItemAnimation.value[0],
    {
      "scale": 1,
      "opacity": 1,
    },
    "main+=80%"
  )
  .to(
    listItemAnimation.value[1],
    {
      "scale": 1,
      "opacity": 1,
    },
    "main+=70%"
  )
  .to(
    listItemAnimation.value[2],
    {
      "scale": 1,
      "opacity": 1,
    },
    "main+=60%"
  )
  .to(
    listItemAnimation.value[3],
    {
      "scale": 1,
      "opacity": 1,
    },
    "main+=50%"
  )

onMounted(() => {
  ScrollTrigger.create({
    trigger: bannerRef.value,
    scrub: true,
    start: "top top",
    animation: bannerStartTl,
  });

  ScrollTrigger.create({
    trigger: scrollRef.value,
    scrub: true,
    start: "top top",
    end: "bottom top",
    animation: scrollTl,
  });

  ScrollTrigger.create({
    trigger: mainRef.value,
    pin: true,
    scrub: true,
    markers: true,
    start: "top top",
    animation: mainStartTl,
  });
});
</script>

<template>
  <div ref="scrollRef" class="scroll">
    <section ref="bannerRef" class="banner"></section>
    <section ref="mainRef" class="main">
      <div class="main-animation">
        <div
          ref="companyRef"
          class="company"
          :style="{
            transform: `translateY(${companyAnimation.yPercent}%) scale(${companyAnimation.scale})`,
            opacity: companyAnimation.opacity,
          }"
        >
          <div
            class="logo"
            :style="{
              opacity: `${companyAnimation.logoOpacity}`,
            }"
          >
            <img
              src="https://gw.alicdn.com/imgextra/i2/O1CN01kEuOaQ1OQe6INmAUY_!!6000000001700-55-tps-180-180.svg"
            />
          </div>
          <div
            class="name"
            :style="{
              opacity: `${companyAnimation.titleOpacity}`,
            }"
          >
            <img
              src="https://gw.alicdn.com/imgextra/i2/O1CN01ymd4z41U5vtsYSFZF_!!6000000002467-55-tps-397-52.svg"
            />
          </div>
        </div>
        <div class="main-other">
          <h2
            :style="{
              transform: `scale(${listAnimation.scale})`,
              opacity: listAnimation.opacity,
            }"
          >
            企业数字化一个钉钉就解决
          </h2>

          <ul
            class="list"
            :style="{
              transform: `scale(${listAnimation.scale})`,
              opacity: listAnimation.opacity,
            }"
          >
            <li v-for="(l, i) in listImage" :key="i" :style="listStyle[i]">
              <img :src="l" alt="" />

              <p>{{ listDoc[i] }}</p>
            </li>
          </ul>
        </div>
        <div class="base-bg">
          <div
            v-for="i in 21"
            :key="i"
            :style="{
              transform: `translateZ(${boxAnimation.z}px)`,
            }"
          ></div>
        </div>
      </div>
      <!-- <div class="main-other">
        <h2>企业数字化一个钉钉就解决</h2>

        <ul class="list" :style="{
          transform: `scale(${listAnimation.scale})`
        }">
          <li v-for="(l, i) in listImage" :key="i">
            <img :src="l" alt="">

            <p>{{ listDoc[i] }}</p>
          </li>
        </ul>
      </div> -->
    </section>
  </div>
  <section class="footer"></section>
</template>

<style lang="scss" scoped>
@use "sass:list";
@use "sass:map";

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
      linear-gradient(
        -27deg,
        rgba(143, 53, 255, 0.8) 11%,
        rgba(143, 53, 255, 0)
      ),
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
  background-color: #040506;
  overflow: hidden;
  font-size: 100px;
  color: #ffffff;

  .main-animation {
    font-size: 100px;
    height: 100vh;
    position: relative;
    display: flex;
    align-items: center;

    .company {
      text-align: center;
      width: 100%;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      position: absolute;
      top: 0;

      .logo {
        width: 180px;
        height: 180px;
      }

      .name {
        width: 397px;
        height: 52px;
      }
    }

    .base-bg {
      width: 100%;
      height: 100vh;
      position: absolute;
      top: 0;
      left: 0;
      transform-style: preserve-3d;
      perspective: 800px;

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

  .main-other {
    width: 12em;
    margin: 0 auto;
    text-align: center;
    border-radius: .16em;

    h2 {
      font-size: 0.48em;
    }

    .list {
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      list-style: none;
      row-gap: 1.3em;
      background-color: rgba(23,26,29,.9);
      padding: .83em .43em;
      box-sizing: border-box;

      img {
        border-radius: 0.1667em;
        height: 0.8em;
        width: 0.8em;
      }

      p {
        font-size: 0.2em;
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
