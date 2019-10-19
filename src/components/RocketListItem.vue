<template lang="html">

  <li v-on:click="handleClick">{{rocket.rocket_name}}</li>
</template>

<script>

import { eventBus } from '@/main.js';

export default {
  name: "rocket-list-item",
  props: ["rocket"],
  methods: {
    handleClick(){
      eventBus.$emit("rocket-selected", this.rocket)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
