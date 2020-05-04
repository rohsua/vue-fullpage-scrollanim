<template>
  <div id="app">
    <full-page :options="options">
      <div class="section">
        First section ...
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
    }
  }
};
</script>
<style lang="scss">
@import "@/styles/global.scss";
</style>
