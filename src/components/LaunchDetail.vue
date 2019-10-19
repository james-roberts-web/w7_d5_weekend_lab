<template lang="html">
  <div class="">
    <h3>{{launch.flight_number}}</h3>
    <h3>{{launch.mission_name}}</h3>
  </div>
</template>

<script>
import { eventBus } from '@/main.js';

export default {
  name: 'launch-detail',
  props: ['launch']
}

</script>

<style lang="css" scoped>
</style>
