<template lang="html">
  <div class="app-container">

    <header>
      <h1>Rocket Info</h1>
    </header>

    <hr>

    <div class="rocket-info">
      <rocket-list class="rocket-list" :rockets="rockets"></rocket-list>

      <rocket-detail class="rocket-detail" v:if="selectedRocket"
      :rocket="selectedRocket"></rocket-detail>

    </div>

    <hr>

    <div class="launch-info">

      <launch-list class="launch-list" :launches="launches"></launch-list>

      <launch-detail class="launch-detail" v:if="selectedLaunch"
      :launch="selectedLaunch"></launch-detail>
    </div>

  </div>
</template>

<script>

import { eventBus } from '@/main.js';

import RocketList from '@/components/RocketList.vue';
import RocketListItem from '@/components/RocketListItem.vue';
import RocketDetail from '@/components/RocketDetail.vue';

import LaunchList from '@/components/LaunchList.vue';
import LaunchListItem from '@/components/LaunchListItem.vue';
import LaunchDetail from '@/components/LaunchDetail.vue';
import LaunchPatchImage from '@/components/LaunchPatchImage.vue';

export default {
  name: 'app',
  data() {
    return {
      rockets: [],
      launches:[],
      selectedRocket: "",
      selectedLaunch: ""
    };
  },

  components: {
    "rocket-list": RocketList,
    "rocket-detail": RocketDetail,
    "launch-list": LaunchList,
    "launch-detail": LaunchDetail,
    "launch-patch-image": LaunchPatchImage
  },

  mounted() {
    this.getRockets();
    this.getLaunches();
    eventBus.$on("rocket-selected", rocket => (this.selectedRocket = rocket));
    eventBus.$on("launch-selected", launch => (this.selectedLaunch = launch));
  },

  methods: {
    getRockets() {
      fetch('https://api.spacexdata.com/v3/rockets')
      .then(result => result.json())
      .then(data => this.rockets = data);
    },
    getLaunches() {
      fetch('https://api.spacexdata.com/v3/launches')
      .then(result => result.json())
      .then(launches => this.launches = launches)
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

.rocket-info, .launch-info {
  display: flex;
  justify-content: center;
}
.rocket-list, .launch-list {
  width:25%;
}

.rocket-detail, .launch-detail {
  width:75%;
}
</style>
