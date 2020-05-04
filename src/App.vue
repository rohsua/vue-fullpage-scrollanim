<template>
  <div id="app">
    <full-page :options="options">
      <div class="section">
        First section ...
        <div id="circle" class="circle"></div>
      </div>
      <div class="section">
        Second section ...
        <div id="right-squre" class="squre"></div>
        <div id="circle2" class="circle"></div>
      </div>
      <div class="section">
        Third section ...
      </div>
      <div class="section fp-auto-height">
        Footer section ...
      </div>
    </full-page>
  </div>
</template>

<script>
import { gsap } from "gsap";

const anchors = ["page1", "page2", "page3"];

export default {
  data() {
    return {
      options: {
        // licenseKey: "YOUR_KEY_HEERE",
        menu: "#menu",
        anchors: anchors,
        navigation: true,
        navigationPosition: "left",
        sectionsColor: ["#41b883", "#ff5f45", "#0798ec"],
        afterLoad: this.afterLoad,
        responsiveWidth: 769
      }
    };
  },
  methods: {
    afterLoad(origin, destination, direction) {
      console.log(origin, destination.index, direction);
      switch (destination.anchor) {
        case anchors[0]:
          gsap.to("#circle", { x: 200, duration: 3 });
          break;
        case anchors[1]:
          gsap.to("#right-squre", 1, { right: 0 });
          gsap.to("#circle2", { x: 500, duration: 3 });
          break;
      }
    }
  },
  beforeMount() {}
};
</script>
<style lang="scss">
@import "@/styles/global.scss";

.fullpage-wrapper {
  overflow-x: hidden;
}

.section {
  position: relative;

  .squre {
    position: absolute;
    top: 0;
    right: -100%;
    width: 20%;
    height: 100vh;
    z-index: 1;
    background-color: green;
  }

  .circle {
    display: block;
    width: 20px;
    height: 20px;
    border-radius: 500em;
    background-color: #fff;
  }

  @media screen and (max-width: 768px) {
    .squre {
      display: none;
    }
  }
}
</style>
