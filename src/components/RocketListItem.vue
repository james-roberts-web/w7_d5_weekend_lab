<template lang="html">
  <p>{{rocket.rocket_name}}</p>
</template>

<script>

import { eventBus } from '@/main.js';

export default {
  name: "rocket-list-item",
  props: ["rocket"]
}
</script>

<style lang="css" scoped>
</style>
