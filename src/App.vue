<template>
  <div id="app">
    <full-page :options="options">
      <div class="section">
        First section ...
        <div class="circle" style="display:block;width:20px;height:20px;border-radius:500em;background-color:#fff"></div>
      </div>
      <div class="section">
        Second section ...
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

export default {
  data() {
    return {
      options: {
        // licenseKey: "YOUR_KEY_HEERE",
        menu: "#menu",
        anchors: ["page1", "page2", "page3"],
        sectionsColor: ["#41b883", "#ff5f45", "#0798ec"],
        afterLoad: this.afterLoad
      }
    };
  },
  methods: {
    afterLoad(origin, destination, direction) {
      console.log(origin, destination, direction);
      gsap.to(".circle", { x: 500, duration: 3 });
    }
  }
};
</script>
<style lang="scss">
@import "@/styles/global.scss";
</style>
