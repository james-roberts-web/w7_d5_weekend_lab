<template lang="html">
  <li v-on:click="handleLaunchClick">{{launch.flight_number}}</li>
</template>

<script>

import { eventBus } from '@/main.js';

export default {
  name:"launch-list-item",
  props: ["launch"],
  methods: {
    handleLaunchClick(){
      eventBus.$emit("launch-selected", this.launch)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
