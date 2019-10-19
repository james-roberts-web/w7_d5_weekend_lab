<template lang="html">
  <div class="">
    <rocket-list-item v-for="(rocket, index) in rockets"
    :rocket="rocket" :key="index"></rocket-list-item>
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
