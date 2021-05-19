<template>
  <div id="app">
    <display-item :item="currentItem"></display-item>
  </div>
</template>

<script>
import DisplayItem from "./components/DisplayItem";
import config from "./libs/config";

export default {
  name: "App",
  components: {
    DisplayItem,
  },
  data: function () {
    return {
      interval: null,
      config: {},
      currentItem: {},
      index: 0,
    };
  },
  mounted() {
    this.config = config.timeline;
    this.index = -1;
    if (this.config.items.length > 1) {
      console.log("Startuje!");
      this.start();
    }
  },
  methods: {
    start() {
      this.next();
    },
    next() {
      this.index = this.index + 1;
      if (this.index == this.config.items.length) {
        this.index = 0;
      }
      this.currentItem = this.config.items[this.index];
      console.log(this.index);
      console.log(this.currentItem);
      var context = this;
      setTimeout(function () {
        context.next();
      }, this.currentItem.time);
    },
  },
  beforeDestroy() {
    clearInterval(this.interval);
  },
};
</script>

<style>
#app {
  margin: 0;
}
</style>
