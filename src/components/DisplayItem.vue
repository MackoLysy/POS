<template>
  <div class="hello">
    <div v-if="item.type == 'html'">
      <iframe
        width="1920"
        height="1080"
        v-bind:src="item.path"
        frameborder="0"
      />
    </div>
    <div v-if="item.type == 'video'">
      <video width="1920" height="1080" controls  v-bind:src="item.path"></video>
    </div>
    <div v-if="item.type == 'img'"><img v-bind:src="item.path" /></div>
  </div>
</template>

<script>
export default {
  name: "displayItem",
  props: {
    renderMsg: { require: true },
    item: { require: true },
  },
  data() {
    return {
      msg: "Welcome to Your asdsa MDB Vue.js App",
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
