<template lang="html">
  <div class="">
    <h1>Rockets</h1>
    <rocket-list></rocket-list>
  </div>
</template>

<script>

import { eventBus } from '@/main.js';
import RocketList from '@/components/RocketList.vue';

export default {
  name: 'app',
  components: {
    "rocket-list": RocketList
  },

  data() {
    return {
      rockets: []
    };
  },

  mounted() {
    this.getRockets();
  },

  methods: {
    getRockets() {
      fetch('https://api.spacexdata.com/v3/rockets')
      .then(result => result.json())
      .then(data => this.rockets = data);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
