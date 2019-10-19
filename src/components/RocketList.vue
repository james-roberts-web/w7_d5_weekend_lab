<template lang="html">
  <div class="">
    <ul>
      <h3>Rockets:</h3>
      <rocket-list-item
      v-for="(rocket, index) in rockets"
      :rocket="rocket" :key="index"></rocket-list-item>
    </ul>
  </div>
</template>

<script>

import RocketListItem from '@/components/RocketListItem.vue';


export default {
  name: "rocket-list",
  props: ["rockets"],
  components: {
    "rocket-list-item": RocketListItem
  }
};
</script>

<style lang="css" scoped>
</style>
