<template>
  <div style="overflow-y: scroll">
    <div v-for="(el, index) of array" :key="index" :style="'background-color:' + el.color">
      {{ el.id }} - {{ el.text }}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'SimpleModal',
  components: {
  }, setup() {
    const array = [];

    function randomColor() {
      const o = Math.round, r = Math.random, s = 255;
      return 'rgba(' + o(r() * s) + ',' + o(r() * s) + ',' + o(r() * s) + ',' + r().toFixed(1) + ')';
    }

    for (let i = 0; i < 350; i++) {
      array.push({
        id: i + 1,
        text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
        color: randomColor()
      });
    }
    return {
      array
    };
  }
});
</script>

<style scoped>
</style>