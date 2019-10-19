<template lang="html">
  <div class="app-container">

    <header>
      <h1>Rockets</h1>
    </header>
    <hr>
    <div class="info">
      <rocket-list class="rocket-list" :rockets="rockets"></rocket-list>
      <rocket-detail class="rocket-detail" v:if="selectedRocket"
      :rocket="selectedRocket"></rocket-detail>
    </div>
  </div>
</template>

<script>

import { eventBus } from '@/main.js';
import RocketList from '@/components/RocketList.vue';
import RocketListItem from '@/components/RocketListItem.vue';
import RocketDetail from '@/components/RocketDetail.vue';

export default {
  name: 'app',
  data() {
    return {
      rockets: [],
      selectedRocket: ""
    };
  },

  components: {
    "rocket-list": RocketList,
    "rocket-detail": RocketDetail
  },

  mounted() {
    this.getRockets();
    eventBus.$on("rocket-selected", rocket => (this.selectedRocket = rocket));
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

.app-container {


  margin: 5%;
  font-family: Helvetica, Arial, sans-serif;
  width: 75%;
}

header {
  display: flex;
  justify-content: center;
}

.info {
  display:flex;
  justify-content: space-between;
}

.rocket-list {
  width:25%;
}

.rocket-detail {
  width:75%;
}
</style>
