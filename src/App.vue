<template>
  <div id="app">
    <full-page :options="options">
      <div class="section">
        First section ...
        <div id="circle" style="display:block;width:20px;height:20px;border-radius:500em;background-color:#fff"></div>
      </div>
      <div class="section">
        Second section ...
        <div id="right-squre" style="position:absolute;top:0;right:-100%;width:20%;height:100%;z-index:1;bottom:0;background-color:green"></div>
        <div id="circle2" style="display:block;width:20px;height:20px;border-radius:500em;background-color:#123"></div>
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
        sectionsColor: ["#41b883", "#ff5f45", "#0798ec"],
        afterLoad: this.afterLoad
      }
    };
  },
  methods: {
    afterLoad(origin, destination, direction) {
      console.log(origin, destination.index, direction);
      switch (destination.anchor) {
        case anchors[0]:
          gsap.to("#circle", { x: 500, duration: 3 });
          break;
        case anchors[1]:
          gsap.to("#right-squre", 1, { right: 0 });
          gsap.to("#circle2", { x: 500, duration: 3 });
          break;
      }
    }
  }
};
</script>
<style lang="scss">
@import "@/styles/global.scss";

.section {
  position: relative;
}
</style>
