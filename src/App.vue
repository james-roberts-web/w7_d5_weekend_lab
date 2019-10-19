<template lang="html">
  <h1>Rockets</h1>
</template>

<script>

import { eventBus } from '@/main.js';

export default {
  name: 'app',

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
