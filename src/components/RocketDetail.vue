<template lang="html">
  <div class="">

    <h3>{{ rocket.rocket_name}}</h3>
    <p>Description:</p>
    <p>{{ rocket.description}}</p>
    <p>First flight: {{ rocket.first_flight}}</p>
  </div>
</template>

<script>
import { eventBus } from '@/main.js';

export default {
  name: 'rocket-detail',
  props: ['rocket']
}

</script>

<style lang="css" scoped>
</style>
